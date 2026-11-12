```lua
--!strict
--[[
    SLua Mock Module — seam mocks, direct mocks, and spies.

    Seam (for ll.* on modules with `__ll`):
        MOCK.mock(owner, name, fn)          -- replace, no log
        MOCK.spy(owner, name, fn?)          -- replace, log; default no-op

    Direct (any writable field on any table):
        MOCK.mock_on(owner, name, fn)       -- replace, no log
        MOCK.spy_on(owner, name, fn?)       -- replace, log; default call-through

    Spy handle:
        s.called, s.call_count, s.calls, s._orig
        s:called_with(...)      exact arg match (== per arg)
        s:called_with_arg(i, v) i-th arg match
        s:reset()               clear log

    Lifecycle (driven by TEST:RUN_ALL when MOCK is passed):
        MOCK.before()    apply registered mocks
        MOCK.between()   reset all spies (per test)
        MOCK.after()     restore everything (idempotent)

    Module seam (2 lines at top of module):
        local ll = setmetatable({}, { __index = _G.ll })
        <Module>.__ll = ll

    Seam introspection:
        rawget(owner.__ll, name)   -- mock installed?
        owner.__ll[name]           -- active function (mock or fallthrough)
]]

export type Owner = {[string]: any}
export type Call  = { n: number, [number]: any }

export type Spy = {
    calls:           {Call},
    call_count:      number,
    called:          boolean,
    _orig:           ((...any) -> ...any)?,
    called_with:     (self: Spy, ...any) -> boolean,
    called_with_arg: (self: Spy, idx: number, want: any) -> boolean,
    reset:           (self: Spy) -> (),
}

type Reg  = { owner: Owner, name: string, fn: any, orig: any?, mode: string }
type Live = { owner: Owner, name: string, orig: any?, mode: string }

local MOCK = {}
local reg:  {Reg}  = {}
local live: {Live} = {}

local function new_spy(fn: (...any) -> ...any, orig: ((...any) -> ...any)?): Spy
    local s: any = {
        calls      = {},
        call_count = 0,
        called     = false,
        _orig      = orig,
    }

    function s.called_with(self: Spy, ...: any): boolean
        local args = { n = select("#", ...), ... }
        for _, c in ipairs(self.calls) do
            if c.n == args.n then
                local ok = true
                for i = 1, args.n do
                    if c[i] ~= args[i] then
                        ok = false
                        break
                    end
                end
                if ok then return true end
            end
        end
        return false
    end

    function s.called_with_arg(self: Spy, idx: number, want: any): boolean
        for _, c in ipairs(self.calls) do
            if c[idx] == want then return true end
        end
        return false
    end

    function s.reset(self: Spy)
        for i = #self.calls, 1, -1 do
            self.calls[i] = nil
        end
        self.call_count = 0
        self.called     = false
    end

    return (setmetatable(s, {
        __call = function(_, ...: any): ...any
            local n = select("#", ...)
            local rec = { n = n } :: Call
            for i = 1, n do
                rec[i] = select(i, ...)
            end
            s.calls[#s.calls + 1] = rec
            s.call_count = s.call_count + 1
            s.called     = true
            return fn(...)
        end,
    }) :: any) :: Spy
end

local function seam_orig(owner: Owner, name: string): ((...any) -> ...any)?
    local mt = getmetatable(owner.__ll)
    return (mt and type(mt.__index) == "table" and mt.__index[name]) or nil
end

local function check_seam(owner: Owner, fname: string)
    if not owner.__ll then
        error(fname .. ": target has no __ll seam (use *_on for direct)", 3)
    end
end

local function check_writable(owner: Owner, name: string, fname: string)
    local probe = owner[name]
    local ok, err = pcall(function() owner[name] = probe end)
    if not ok then
        error(fname .. ": cannot write '" .. tostring(name) .. "' — " .. tostring(err), 3)
    end
end

function MOCK.mock(owner: Owner, name: string, fn: (...any) -> ...any)
    check_seam(owner, "MOCK.mock")
    reg[#reg + 1] = { owner = owner, name = name, fn = fn, mode = "seam" }
end

function MOCK.spy(owner: Owner, name: string, fn: ((...any) -> ...any)?): Spy
    check_seam(owner, "MOCK.spy")
    local s = new_spy(fn or function() end, seam_orig(owner, name))
    reg[#reg + 1] = { owner = owner, name = name, fn = s, mode = "seam" }
    return s
end

function MOCK.mock_on(owner: Owner, name: string, fn: (...any) -> ...any)
    check_writable(owner, name, "MOCK.mock_on")
    reg[#reg + 1] = { owner = owner, name = name, fn = fn, orig = owner[name], mode = "direct" }
end

function MOCK.spy_on(owner: Owner, name: string, fn: ((...any) -> ...any)?): Spy
    check_writable(owner, name, "MOCK.spy_on")
    local orig = owner[name]
    local s = new_spy(fn or orig or function() end, orig)
    reg[#reg + 1] = { owner = owner, name = name, fn = s, orig = orig, mode = "direct" }
    return s
end

function MOCK.before()
    for _, e in ipairs(reg) do
        if e.mode == "seam" then
            e.owner.__ll[e.name] = e.fn
            live[#live + 1] = { owner = e.owner, name = e.name, mode = "seam" }
        else
            e.owner[e.name] = e.fn
            live[#live + 1] = { owner = e.owner, name = e.name, orig = e.orig, mode = "direct" }
        end
    end
end

function MOCK.between()
    for _, e in ipairs(reg) do
        local s = e.fn :: any
        if type(s) == "table" and s.reset then s:reset() end
    end
end

function MOCK.after()
    for i = #live, 1, -1 do
        local e = live[i]
        if e.mode == "seam" then
            e.owner.__ll[e.name] = nil
        else
            e.owner[e.name] = e.orig
        end
    end
    live = {}
end

function MOCK.real(owner: Owner, name: string): ((...any) -> ...any)?
    if owner.__ll then return seam_orig(owner, name) end
    for _, e in ipairs(reg) do
        if e.owner == owner and e.name == name and e.mode == "direct" then
            return e.orig
        end
    end
    return nil
end

return MOCK

```
