```lua
--!strict
--[[
    SLua test runner + utility provider.

    Usage:
        local TEST   = require("...base")
        local ASSERT = require("...assert")(TEST)
        local EXPECT = require("...expect")(TEST)

        local tests = {
            before_all  = function() end,
            before_each = function(name) end,
            after_each  = function(name) end,
            after_all   = function() end,
            some_test   = function() end,
        }

        TEST:RUN_ALL(tests, MOCK)   -- MOCK is optional
]]

-- ═══ Types ═══════════════════════════════════════════════════════════

export type Test = () -> ()
export type Hook = (name: string) -> ()

export type Suite = {
    before_all:  (() -> ())?,
    before_each: Hook?,
    after_each:  Hook?,
    after_all:   (() -> ())?,
    [string]: any,
}

export type MockLike = {
    before:  (() -> ())?,
    between: (() -> ())?,
    after:   (() -> ())?,
}

export type TestRunner = {
    str_cmp: <T, U>(a: T, b: U) -> boolean,
    fail: (m: string) -> (),
    RUN: (
        self: TestRunner,
        name: string,
        func: Test,
        hooks: Suite?,
        idx: number?,
        total: number?
    ) -> boolean,
    RUN_ALL: (self: TestRunner, suite: Suite, mock: MockLike?) -> boolean,
}

-- ═══ Constants ═══════════════════════════════════════════════════════

local HOOKS: {[string]: boolean} = {
    before_all  = true,
    before_each = true,
    after_each  = true,
    after_all   = true,
}

-- ═══ State ═══════════════════════════════════════════════════════════

local TEST: TestRunner = ({} :: any) :: TestRunner
local pending: {string} = {}

-- ═══ Utilities ═══════════════════════════════════════════════════════

function TEST.str_cmp<T, U>(a: T, b: U): boolean
    return string.lower(tostring(a)) == string.lower(tostring(b))
end

function TEST.fail(m: string)
    pending[#pending + 1] = m
end

-- ═══ Runner ══════════════════════════════════════════════════════════

function TEST:RUN(
    name: string,
    func: Test,
    hooks: Suite?,
    idx: number?,
    total: number?
): boolean
    pending = {}
    local passed = true

    -- before_each
    if hooks then
        local be = hooks.before_each
        if be then
            local ok, err = xpcall(be :: (string) -> any, debug.traceback, name)
            if not ok then
                pending[#pending + 1] = "before_each: " .. tostring(err)
                passed = false
            end
        end
    end

    -- body + after_each
    if passed then
        local ok, err = xpcall(func :: () -> any, debug.traceback)
        if not ok then
            pending[#pending + 1] = tostring(err)
        end

        if hooks then
            local ae = hooks.after_each
            if ae then
                local ok2, err2 = xpcall(ae :: (string) -> any, debug.traceback, name)
                if not ok2 then
                    pending[#pending + 1] = "after_each: " .. tostring(err2)
                end
            end
        end
    end

    if #pending > 0 then passed = false end

    local prefix: string
    if idx and total then
        prefix = string.format("> [%d/%d] ", idx, total)
    else
        prefix = "> "
    end

    print(prefix .. name .. " ...... " .. (passed and "PASSED" or "FAILED"))
    for _, m in ipairs(pending) do
        print("    " .. (m:gsub("\n", "\n    ")))
    end
    return passed
end

function TEST:RUN_ALL(suite: Suite, mock: MockLike?): boolean
    if mock then
        local b = mock.before
        if b then b() end
    end

    print("========== Test start ==========")

    local ba = suite.before_all
    if ba then
        local ok, err = xpcall(ba :: () -> any, debug.traceback)
        if not ok then
            print("before_all: " .. (tostring(err):gsub("\n", "\n  ")))
            local aa = suite.after_all
            if aa then pcall(aa) end
            if mock then
                local a = mock.after
                if a then a() end
            end
            print("========== Test end ==========")
            return false
        end
    end

    local names: {string} = {}
    for n, v in pairs(suite) do
        if not HOOKS[n] and type(v) == "function" then
            names[#names + 1] = n
        end
    end
    table.sort(names)

    local pass = 0
    for i, n in ipairs(names) do
        if mock then
            local b = mock.between
            if b then b() end
        end
        local test = suite[n] :: Test
        if self:RUN(n, test, suite, i, #names) then
            pass = pass + 1
        end
    end

    local aa = suite.after_all
    if aa then
        local ok, err = xpcall(aa :: () -> any, debug.traceback)
        if not ok then
            print("after_all: " .. (tostring(err):gsub("\n", "\n  ")))
        end
    end

    if mock then
        local a = mock.after
        if a then a() end
    end

    print(string.format("> Summary: %d/%d passed", pass, #names))
    print("========== Test end ==========")
    return pass == #names
end

return TEST


```
