# then

The conditional clause separator. Marks the boundary between the condition of an `if` or `elseif` and the block that runs when the condition is truthy. `then` appears exactly once per `if` and once per `elseif`, immediately after the condition and before the first statement of the block. It is not used in `while`, `for`, `repeat`, or any other construct. This page lists every position where `then` is valid, the forms it can take, and the restrictions the parser enforces.

## Contents

- [Purpose](#purpose)
- [After if](#after-if)
- [After elseif](#after-elseif)
- [With compound conditions](#with-compound-conditions)
- [With multiline conditions](#with-multiline-conditions)
- [With empty blocks](#with-empty-blocks)
- [Not used in other constructs](#not-used-in-other-constructs)
- [Restriction: exactly one then per branch](#restriction-exactly-one-then-per-branch)
- [Restriction: required after every condition](#restriction-required-after-every-condition)

## Purpose

`then` separates a condition from its body. In `if cond then body end`, the parser evaluates `cond`, and if the result is truthy, runs `body`. Without `then`, the parser cannot tell where the condition ends and the body begins.

```lua
if ready then
    print("go")
end
```

**Breakdown**

- `if ready then` evaluates `ready`.
- `then` marks the end of the condition and the start of the body.
- `print("go")` runs only when `ready` is truthy.
- `end` closes the whole `if` statement.

## After if

Every `if` statement has exactly one `then`, immediately after its condition. It is required; omitting it is a syntax error.

```lua
if x > 0 then
    print("positive")
end
```

**Breakdown**

- `if x > 0 then` tests the comparison.
- `then` introduces the body that runs when the comparison is true.
- `end` closes the statement.
- `if x > 0 print("positive") end` without `then` is rejected by the parser.

## After elseif

Every `elseif` branch also has its own `then`, immediately after its condition. The `elseif ... then` pair behaves like a fresh `if ... then`, except that it only runs when every preceding condition was falsy.

```lua
if score >= 90 then
    print("A")
elseif score >= 80 then
    print("B")
end
```

**Breakdown**

- `if score >= 90 then` opens the chain.
- `elseif score >= 80 then` adds a second branch, with its own `then`.
- Each branch has exactly one `then`.
- A single `end` closes the entire chain.

## With compound conditions

The condition before `then` may be any expression, including one built with `and`, `or`, and `not`. `then` comes after the entire expression, not between the sub-expressions.

```lua
if hasKey and hasPermission then
    print("granted")
end

if not done or retryCount < 3 then
    print("keep trying")
end
```

**Breakdown**

- `hasKey and hasPermission` is the full condition; `then` follows the whole expression.
- `not done or retryCount < 3` is the full condition.
- Writing `if hasKey then and hasPermission then` is a syntax error; there is one `then` per branch.

## With multiline conditions

A condition may span multiple lines. The `then` appears after the condition ends, on the same line as the last part of the condition or on a following line.

```lua
if ready
    and hasPermission
    and not isBusy
then
    print("proceed")
end
```

**Breakdown**

- The condition spans three lines; each sub-expression is joined by `and`.
- `then` appears on its own line after the condition, before the body.
- Placing `then` earlier, in the middle of the condition, is a syntax error.
- Both styles compile to the same thing; the placement is a matter of formatting.

## With empty blocks

An `if ... then` with no statement before `end` is valid. The body is empty and does nothing when the condition is truthy.

```lua
if debugMode then
end

if debugMode then end
```

**Breakdown**

- Both forms are valid; the first uses two lines, the second uses one.
- The empty body does nothing; the condition is still evaluated.
- Empty `if` blocks are occasionally used as documentation or as placeholders.
- For a conditional that produces no code, an empty `if ... then end` is clearer than a comment alone.

## Not used in other constructs

`then` is only valid in `if` and `elseif`. It does not appear in `while`, `for`, `repeat`, `do`, or `function`. Using `then` in any of those is a syntax error.

```lua
-- while x > 0 then ... end      -- compile error: while uses do
-- for i = 1, 3 then ... end     -- compile error: for uses do
-- repeat ... then cond          -- compile error: repeat uses until
```

**Breakdown**

- `while` uses `do`, not `then`.
- `for` uses `do`, not `then`.
- `repeat` uses `until`, not `then`.
- `if` and `elseif` are the only constructs that use `then`.

## Restriction: exactly one then per branch

Every `if` branch and every `elseif` branch has exactly one `then`. Writing two `then` keywords in the same branch is a syntax error.

```lua
-- if x then then print("x") end       -- compile error: duplicate then
-- elseif x then then print("x") end   -- compile error: duplicate then
```

**Breakdown**

- The first `then` closes the condition.
- A second `then` immediately after is rejected; the parser expects a statement or `end` next.
- The same rule applies to `elseif`.

## Restriction: required after every condition

Every `if` and `elseif` condition must be followed by `then`. Omitting it is a syntax error, and the parser will report the expected token at the position where the body was supposed to begin.

```lua
-- if x > 0 print("positive") end      -- compile error: missing then
-- if x > 0                            -- compile error: missing then
--     print("positive")
-- end
```

**Breakdown**

- `if x > 0 print(...)` is rejected because `then` is missing between the condition and the body.
- Splitting the body across lines does not change the rule; `then` is still required.
- The parser reports the missing `then` at the position where the body begins.

