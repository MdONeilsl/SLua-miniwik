# SLua Test Framework — User Documentation

---

## 1. Files

| File | Purpose |
|---|---|
| `modules/test/base.lua` | Test runner |
| `modules/test/assert.lua` | Fatal checks |
| `modules/test/expect.lua` | Non-fatal checks |
| `modules/test/not.lua` | Inverted non-fatal checks |
| `modules/test/mock.lua` | Mocks and spies |

---

## 2. Imports

```lua
local TEST   = require("./modules/test/base")
local ASSERT = require("./modules/test/assert")(TEST)
local EXPECT = require("./modules/test/expect")(TEST)
local NOT    = require("./modules/test/not")(TEST)
local MOCK   = require("./modules/test/mock")
```

`assert`, `expect`, `not` are factories — pass the `TEST` object. `base` and `mock` are plain modules. Import only what you use.

---

## 3. Writing a suite

A suite is a table. Reserved keys are hooks. Every other function-valued key is a test.

```lua
local tests = {
    before_all  = function() end,
    before_each = function(name) end,
    after_each  = function(name) end,
    after_all   = function() end,

    my_test_1 = function() end,
    my_test_2 = function() end,
}

TEST:RUN_ALL(tests)
```

Tests run in alphabetical order by key name. `RUN_ALL` returns `true` if every test passed.

### 3.1 Hook signatures

| Hook | Runs | Receives | Notes |
|---|---|---|---|
| `before_all` | Once before every test | — | Failure aborts the suite |
| `before_each` | Before every test | Test name | Failure skips the test body and `after_each` |
| `after_each` | After every test | Test name | Failure fails the test even if the body passed |
| `after_all` | Once after every test | — | Runs even if `before_all` failed |

---

## 4. Checks

### 4.1 Signature

Every check is `(value, expected, message)`.

`TRUE` / `FALSE` accept `(v, "message")` or `(v, nil, "message")` — the second slot acts as the message when it is a string.

Floating-point checks accept an optional 4th argument: `FEQ(v, e, m, eps)`, `DEQ(v, e, m, eps)`, `NEAR(v, e, m, tol)`.

### 4.2 `ASSERT` — fatal

Throws on failure. The test aborts at the call site. Subsequent statements do not run.

```lua
ASSERT.EQ(divide(10, 2), 5, "10 / 2 = 5")
ASSERT.TRUE(is_valid, "precondition")
```

### 4.3 `EXPECT` — non-fatal

Reports on failure. The test continues. All failures are buffered and printed under the test's result line.

```lua
EXPECT.EQ(divide(2, 2), 5)        -- fails, continues
EXPECT.TRUE(lamp.lit)             -- runs anyway
```

### 4.4 `NOT` — inverted, non-fatal

Passes when the non-`not` counterpart would fail. Same failure behaviour as `EXPECT`.

```lua
NOT.EQ(a, b)                      -- passes when a ~= b
NOT.TRUE(spy.called, "not called")
NOT.THAT(c, is_alive, "should be dead")
```

### 4.5 Available checks

| Check | Assertion |
|---|---|
| `TRUE(v)` | `v` is truthy |
| `FALSE(v)` | `v` is falsy |
| `EQ(v, e)` | `v == e` |
| `NE(v, e)` | `v ~= e` |
| `LT(v, e)` | `v < e` |
| `LE(v, e)` | `v <= e` |
| `GT(v, e)` | `v > e` |
| `GE(v, e)` | `v >= e` |
| `STREQ(v, e)` | `tostring(v) == tostring(e)` |
| `STRNE(v, e)` | `tostring(v) ~= tostring(e)` |
| `CSTREQ(v, e)` | case-insensitive equality |
| `CSTRNE(v, e)` | case-insensitive inequality |
| `FEQ(v, e, m?, eps?)` | `abs(v - e) <= eps` (default `1e-4`) |
| `DEQ(v, e, m?, eps?)` | `abs(v - e) <= eps` (default `1e-8`) |
| `NEAR(v, e, m?, tol?)` | `abs(v - e) <= tol` (default `1e-4`) |
| `THAT(v, f)` | `f(v)` is truthy |

### 4.6 Failure behaviour

| Family | On failure | Test continues |
|---|---|---|
| `ASSERT.*` | Throws `error(m)` | no |
| `EXPECT.*` | Buffers message | yes |
| `NOT.*` | Buffers message | yes |

### 4.7 Default messages

When no message is given, defaults are:

| Check | Default |
|---|---|
| `TRUE` | `TRUE failed` |
| `FALSE` | `FALSE failed` |
| `EQ` | `EQ failed: <v> != <e>` |
| `NE` | `NE failed: <v> == <e>` |
| `LT` | `LT failed: <v> >= <e>` |
| `LE` | `LE failed: <v> > <e>` |
| `GT` | `GT failed: <v> <= <e>` |
| `GE` | `GE failed: <v> < <e>` |
| `STREQ` | `STREQ failed: '<v>' != '<e>'` |
| `STRNE` | `STRNE failed: '<v>' == '<e>'` |
| `CSTREQ` | `CSTREQ failed: '<v>' != '<e>'` |
| `CSTRNE` | `CSTRNE failed: '<v>' == '<e>'` |
| `FEQ` | `FEQ failed: <v> != <e>` |
| `DEQ` | `DEQ failed: <v> != <e>` |
| `NEAR` | `NEAR failed: <v>, <e> > <tol>` |
| `THAT` | `THAT failed: <v>` |

`NOT.*` prefixes each default with `NOT_`.

---

## 5. Output format

```
========== Test start ==========
> [1/3] alpha ...... PASSED
> [2/3] beta ...... FAILED
    <buffered failure message>
    <buffered traceback>
> [3/3] gamma ...... PASSED
> Summary: 2/3 passed
========== Test end ==========
```

Tracebacks and messages are indented 4 spaces.

---

## 6. Making a module mockable

Two lines at the top of the module, after the module table is declared:

```lua
local Lamp = {}
local ll = setmetatable({}, { __index = _G.ll })
Lamp.__ll = ll
```

The module body then uses `ll.X(...)` exactly as it would use the global `ll`:

```lua
function Lamp.turn_on(self)
    self.lit = true
    ll.SetClickAction(CLICK_ACTION_TOUCH)
end
```

The seam is required. `_G` and `ll` are both frozen; a module without the seam cannot be mocked.

---

## 7. Mocks

### 7.1 Two families

| Family | Targets | Use on |
|---|---|---|
| `mock` / `spy` | `owner.__ll[name]` | Frozen engine calls (`ll.*`) |
| `mock_on` / `spy_on` | `owner[name]` | User-defined fields |

### 7.2 Mocks

A mock replaces behaviour. No call log.

```lua
MOCK.mock(Lamp, "SetClickAction", function(action) end)
MOCK.mock_on(helpers, "greet", function(name) return "MOCKED" end)
```

### 7.3 Spies

A spy records calls and returns the handle.

```lua
local spy = MOCK.spy(Lamp, "SetClickAction")           -- default no-op
local spy = MOCK.spy_on(helpers, "greet")              -- default call-through
local spy = MOCK.spy_on(helpers, "greet", function(n)  -- explicit impl
    return "hi " .. n
end)
```

### 7.4 Default behaviour when `fn` omitted

| Family | Default |
|---|---|
| Seam (`spy`) | no-op — original is not called |
| Direct (`spy_on`) | call-through — original is called |

### 7.5 Spy handle

| Field / method | Type | Meaning |
|---|---|---|
| `spy.called` | `boolean` | `true` if called at least once since reset |
| `spy.call_count` | `number` | Number of calls since reset |
| `spy.calls` | `{Call}` | Every recorded call; `calls[k].n` is arg count, `calls[k][i]` is i-th arg |
| `spy._orig` | `fn?` | Original function, or `nil` if none captured |
| `spy:called_with(...)` | `-> boolean` | `true` if any call matched all args (`==` per arg) |
| `spy:called_with_arg(i, v)` | `-> boolean` | `true` if any call's i-th arg equals `v` |
| `spy:reset()` | `-> ()` | Clear the log |

Argument matching is `==` per argument. Table arguments compare by reference — `called_with({})` will not match a call that passed a different `{}`.

### 7.6 Looking up the original

```lua
local orig = MOCK.real(helpers, "greet")   -- original fn, or nil
local orig = MOCK.real(Lamp, "SetClickAction")
```

Also available as `spy._orig`.

### 7.7 Lifecycle

Mocks are applied and restored automatically when `MOCK` is passed to `RUN_ALL`:

```lua
MOCK.mock(Lamp, "SetClickAction", fn)     -- register only
local spy = MOCK.spy(Lamp, "CreateCharacter")

TEST:RUN_ALL(tests, MOCK)                 -- applies, runs, restores
```

Inside `RUN_ALL`, `MOCK.before()` runs once at start, `MOCK.between()` runs before each test (resetting spies), and `MOCK.after()` runs once at end.

Without the argument, `RUN_ALL(tests)` runs no mock lifecycle. Call the methods manually if you need them:

```lua
MOCK.before()
TEST:RUN_ALL(tests)
MOCK.after()
```

### 7.8 Introspection

| Expression | Result |
|---|---|
| `rawget(owner.__ll, name)` | The installed mock, or `nil` if not mocked |
| `owner.__ll[name]` | The active function (mock if installed, original otherwise) |

### 7.9 Validation errors

| Situation | Message |
|---|---|
| `mock` / `spy` on target without `__ll` | `"<fname>: target has no __ll seam (use *_on for direct)"` |
| `mock_on` / `spy_on` on unwritable field | `"<fname>: cannot write '<name>' — <reason>"` |

---

## 8. `TEST` object

| Symbol | Signature |
|---|---|
| `TEST:RUN` | `(name: string, func: () -> (), hooks: Suite?, idx: number?, total: number?) -> boolean` |
| `TEST:RUN_ALL` | `(suite: Suite, mock: MockLike?) -> boolean` |
| `TEST.str_cmp` | `<T, U>(a: T, b: U) -> boolean` |
| `TEST.fail` | `(m: string) -> ()` |

`TEST.str_cmp` and `TEST.fail` are used internally by the check factories. `TEST:RUN` is used by `RUN_ALL`; call it directly only for custom orchestration.

---

## 9. Examples

### 9.1 Minimal — `EXPECT` only

```lua
local TEST   = require("./modules/test/base")
local EXPECT = require("./modules/test/expect")(TEST)

local function add(a, b) return a + b end

local tests = {
    add_positive = function()
        EXPECT.EQ(add(2, 3), 5, "2 + 3 = 5")
        EXPECT.GT(add(1, 1), 1, "1 + 1 > 1")
    end,
    add_identity = function()
        EXPECT.EQ(add(7, 0), 7, "n + 0 = n")
    end,
}

TEST:RUN_ALL(tests)
```

### 9.2 `EXPECT` + `ASSERT`

```lua
local TEST   = require("./modules/test/base")
local ASSERT = require("./modules/test/assert")(TEST)
local EXPECT = require("./modules/test/expect")(TEST)

local function divide(a, b)
    if b == 0 then error("division by zero", 0) end
    return a / b
end

local tests = {
    divide_basic = function()
        ASSERT.EQ(divide(10, 2), 5, "10 / 2 = 5")
        EXPECT.FEQ(divide(1, 3), 1/3, "1 / 3 ≈ 0.333")
    end,

    divide_expect_continues = function()
        EXPECT.EQ(divide(2, 2), 5, "intentional fail")
        EXPECT.FALSE(divide(9, 3) == 3, "intentional fail")
    end,

    divide_assert_aborts = function()
        ASSERT.EQ(divide(1, 1), 99, "intentional fail")
        -- execution stops here
    end,
}

TEST:RUN_ALL(tests)
```

### 9.3 Mock — no spy

```lua
local TEST   = require("./modules/test/base")
local EXPECT = require("./modules/test/expect")(TEST)
local MOCK   = require("./modules/test/mock")

local Lamp = {}
Lamp.__index = Lamp
local ll = setmetatable({}, { __index = _G.ll })
Lamp.__ll = ll

function Lamp.new() return setmetatable({ lit = false }, Lamp) end
function Lamp.turn_on(self)
    self.lit = true
    ll.SetClickAction(CLICK_ACTION_TOUCH)
end
function Lamp.turn_off(self)
    self.lit = false
    ll.SetClickAction(CLICK_ACTION_NONE)
end

MOCK.mock(Lamp, "SetClickAction", function(_action) end)

local tests = {
    turn_on_sets_flag = function()
        local lamp = Lamp.new()
        lamp:turn_on()
        EXPECT.TRUE(lamp.lit, "turn_on sets lit")
    end,
}

TEST:RUN_ALL(tests, MOCK)
```

### 9.4 Spy — record calls

```lua
local TEST   = require("./modules/test/base")
local EXPECT = require("./modules/test/expect")(TEST)
local MOCK   = require("./modules/test/mock")

local Lamp = {}
Lamp.__index = Lamp
local ll = setmetatable({}, { __index = _G.ll })
Lamp.__ll = ll

function Lamp.new() return setmetatable({ lit = false }, Lamp) end
function Lamp.turn_on(self)
    self.lit = true
    ll.SetClickAction(CLICK_ACTION_TOUCH)
end
function Lamp.turn_off(self)
    self.lit = false
    ll.SetClickAction(CLICK_ACTION_NONE)
end

local spy = MOCK.spy(Lamp, "SetClickAction")

local tests = {
    turn_on_fires_touch = function()
        local lamp = Lamp.new()
        lamp:turn_on()
        EXPECT.TRUE(spy.called, "SetClickAction fired")
        EXPECT.EQ(spy.call_count, 1, "called once")
        EXPECT.TRUE(spy:called_with_arg(1, CLICK_ACTION_TOUCH), "TOUCH action")
    end,

    turn_off_fires_none = function()
        local lamp = Lamp.new()
        lamp:turn_off()
        EXPECT.TRUE(spy:called_with_arg(1, CLICK_ACTION_NONE), "NONE action")
    end,
}

TEST:RUN_ALL(tests, MOCK)
```

---

## 10. Compile-time checks

In strict mode, `EQ`, `NE`, and `THAT` unify their types:

- `EQ(1, "1")` — compile error (`T` mismatch)
- `LT("a", "b")` — compile error (expects `number`)
- `THAT(n, function(s: string) … end)` where `n: number` — compile error (predicate signature)
- `CSTREQ(123, "123")` — compiles (both coerce to `tostring`)

---

## 11. Limitations

- Only **fields of writable tables** can be mocked or spied. Locals and upvalues are unreachable.
- Modules must have the **2-line seam** to be mockable via `mock` / `spy`.
- Spy argument matching is `==` per argument — no deep equality.
- Tests run in **alphabetical order**; no explicit ordering API.
- No `skip` / `only`.
- No async support. Simulating async events requires mocking the scheduler function and driving events manually.


