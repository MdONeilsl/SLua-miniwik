```lua
--!strict
--[[
    Non-fatal check factory. Every check reports via ctx.fail and continues.

    Signature: (value, expected, message[, eps|tol]).

    TRUE / FALSE accept (v, e_or_m, m?): the second argument acts as the
    message when it is a string, matching the shape used by assert.lua.

    Factory: (ctx) -> Checks. `ctx.str_cmp` is the shared comparator
    used by the case-insensitive checks; `ctx.fail` records a failure
    without raising.
]]

export type Ctx = {
    str_cmp: <T, U>(a: T, b: U) -> boolean,
    fail: (m: string) -> (),
}

export type Checks = {
    TRUE:   (v: any, e: any, m: string?) -> (),
    FALSE:  (v: any, e: any, m: string?) -> (),
    EQ:     <T>(v: T, e: T, m: string?) -> (),
    NE:     <T>(v: T, e: T, m: string?) -> (),
    LT:     (v: number, e: number, m: string?) -> (),
    LE:     (v: number, e: number, m: string?) -> (),
    GT:     (v: number, e: number, m: string?) -> (),
    GE:     (v: number, e: number, m: string?) -> (),
    STREQ:  <T, U>(v: T, e: U, m: string?) -> (),
    STRNE:  <T, U>(v: T, e: U, m: string?) -> (),
    CSTREQ: <T, U>(v: T, e: U, m: string?) -> (),
    CSTRNE: <T, U>(v: T, e: U, m: string?) -> (),
    FEQ:    (v: number, e: number, m: string?, eps: number?) -> (),
    DEQ:    (v: number, e: number, m: string?, eps: number?) -> (),
    NEAR:   (v: number, e: number, m: string?, t: number?) -> (),
    THAT:   <T>(v: T, f: (T) -> boolean, m: string?) -> (),
}

return function(ctx: Ctx): Checks
    local function rp(m: string) ctx.fail(m) end
    return {
        TRUE   = function(v: any, e: any, m: string?) if not v then rp(m or (type(e) == "string" and e or "TRUE failed")) end end,
        FALSE  = function(v: any, e: any, m: string?) if v then rp(m or (type(e) == "string" and e or "FALSE failed")) end end,
        EQ     = function<T>(v: T, e: T, m: string?) if v ~= e then rp(m or string.format("EQ failed: %s != %s", tostring(v), tostring(e))) end end,
        NE     = function<T>(v: T, e: T, m: string?) if v == e then rp(m or string.format("NE failed: %s == %s", tostring(v), tostring(e))) end end,
        LT     = function(v: number, e: number, m: string?) if not (v < e) then rp(m or string.format("LT failed: %s >= %s", tostring(v), tostring(e))) end end,
        LE     = function(v: number, e: number, m: string?) if not (v <= e) then rp(m or string.format("LE failed: %s > %s", tostring(v), tostring(e))) end end,
        GT     = function(v: number, e: number, m: string?) if not (v > e) then rp(m or string.format("GT failed: %s <= %s", tostring(v), tostring(e))) end end,
        GE     = function(v: number, e: number, m: string?) if not (v >= e) then rp(m or string.format("GE failed: %s < %s", tostring(v), tostring(e))) end end,
        STREQ  = function<T, U>(v: T, e: U, m: string?) if tostring(v) ~= tostring(e) then rp(m or string.format("STREQ failed: '%s' != '%s'", tostring(v), tostring(e))) end end,
        STRNE  = function<T, U>(v: T, e: U, m: string?) if tostring(v) == tostring(e) then rp(m or string.format("STRNE failed: '%s' == '%s'", tostring(v), tostring(e))) end end,
        CSTREQ = function<T, U>(v: T, e: U, m: string?) if not ctx.str_cmp(v, e) then rp(m or string.format("CSTREQ failed: '%s' != '%s'", tostring(v), tostring(e))) end end,
        CSTRNE = function<T, U>(v: T, e: U, m: string?) if ctx.str_cmp(v, e) then rp(m or string.format("CSTRNE failed: '%s' == '%s'", tostring(v), tostring(e))) end end,
        FEQ    = function(v: number, e: number, m: string?, eps: number?) local d = eps or 1e-4; if math.abs(v - e) > d then rp(m or string.format("FEQ failed: %f != %f", v, e)) end end,
        DEQ    = function(v: number, e: number, m: string?, eps: number?) local d = eps or 1e-8; if math.abs(v - e) > d then rp(m or string.format("DEQ failed: %f != %f", v, e)) end end,
        NEAR   = function(v: number, e: number, m: string?, t: number?) local d = t or 1e-4; if math.abs(v - e) > d then rp(m or string.format("NEAR failed: %f, %f > %f", v, e, d)) end end,
        THAT   = function<T>(v: T, f: (T) -> boolean, m: string?) if not f(v) then rp(m or string.format("THAT failed: %s", tostring(v))) end end,
    }
end

```