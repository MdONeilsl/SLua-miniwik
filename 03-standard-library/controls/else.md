# else

The final alternative in a conditional chain. Runs when the controlling `if` and every preceding `elseif` are falsy. `else` is optional; a chain may end at any `elseif` or at the single `if`. This page lists every chain shape in which `else` can appear, what runs in each, and the two restrictions the parser enforces.

## Contents

- [Purpose](#purpose)
- [After a single if](#after-a-single-if)
- [After one or more elseif](#after-one-or-more-elseif)
- [No else at all](#no-else-at-all)
- [Inside a function with early return](#inside-a-function-with-early-return)
- [Inside nested if chains](#inside-nested-if-chains)
- [Interaction with truthiness](#interaction-with-truthiness)
- [Restriction: only once per chain](#restriction-only-once-per-chain)
- [Restriction: must be last](#restriction-must-be-last)

## Purpose

`else` provides a default branch when no earlier condition holds. Without `else`, a chain may run no branch at all; with `else`, exactly one branch always runs.

```lua
local score = 55

if score >= 90 then
    print("A")
else
    print("not A")
end
```

**Breakdown**

- If `score >= 90`, the `if` branch runs.
- Otherwise, the `else` branch runs.
- One of the two branches always runs; there is no path where neither runs.

## After a single if

The simplest form: one `if` and one `else`. Exactly one of the two branches runs.

```lua
local flag = true

if flag then
    print("yes")
else
    print("no")
end
```

**Breakdown**

- If `flag` is truthy, `"yes"` is printed.
- If `flag` is falsy, `"no"` is printed.
- `else` catches every value that is not truthy, including `nil` and `false`.

## After one or more elseif

`else` after `elseif` catches every case not covered by the earlier conditions. The chain is tested top to bottom; the first truthy condition wins; `else` runs only if none of the earlier conditions was truthy.

```lua
local score = 75

if score >= 90 then
    print("A")
elseif score >= 80 then
    print("B")
elseif score >= 70 then
    print("C")
else
    print("F")
end
```

**Breakdown**

- With `score == 75`, the first two conditions are false, the third is true, and `"C"` is printed.
- `else` does not run because an earlier `elseif` matched.
- Only one branch runs regardless of how many conditions are tested.

## No else at all

`else` is optional. Without it, the chain may run zero branches when no condition matches.

```lua
local score = 55

if score >= 90 then
    print("A")
elseif score >= 80 then
    print("B")
end
```

**Breakdown**

- With `score == 55`, no condition matches.
- No branch runs; the chain falls through silently.
- Adding an `else` would guarantee a branch runs; omitting it leaves the no-match case as a no-op.

## Inside a function with early return

A common idiom replaces `else` with an early `return`. The two forms are equivalent; the early-return form is flatter and easier to read.

```lua
local function classify(score: number): string
    if score >= 90 then return "A" end
    if score >= 80 then return "B" end
    return "F"
end
```

**Breakdown**

- Each `if` returns immediately on match, so no `else` is needed.
- The final `return "F"` plays the role of `else`; it runs only if the earlier conditions did not return.
- Rewriting this with explicit `else` branches produces the same behavior.

## Inside nested if chains

`else` binds to the nearest `if` in the same block. In a nested chain, an `else` without a matching `elseif` belongs to the innermost `if` that has not yet been closed.

```lua
local a = true
local b = false

if a then
    if b then
        print("both")
    else
        print("a only")
    end
else
    print("not a")
end
```

**Breakdown**

- The first `else` belongs to `if b`; it runs when `a` is true and `b` is false.
- The second `else` belongs to `if a`; it runs when `a` is false.
- With `a == true` and `b == false`, `"a only"` is printed.
- Indentation does not affect binding; only the `if`/`end` pairing does.

## Interaction with truthiness

`else` runs for every falsy value, not only `false`. Both `nil` and `false` trigger it, and no other value does.

```lua
local v = 0

if v then
    print("truthy")
else
    print("falsy")
end
```

**Breakdown**

- `0` is truthy in SLua, so `"truthy"` is printed.
- The `else` branch runs only for `nil` or `false`.
- To treat `0` as "absent", test explicitly: `if v ~= 0 then ... else ... end`.

## Restriction: only once per chain

A single `if ... elseif ... else ... end` chain may contain exactly one `else`. Adding a second `else` is a syntax error.

```lua
if a then
    print("a")
else
    print("not a")
-- else      -- compile error: duplicate else
end
```

**Breakdown**

- The first `else` is the chain's default branch.
- A second `else` in the same chain is rejected.
- Chains with multiple default branches must be restructured with `elseif`.

## Restriction: must be last

`else` is always the final branch of the chain. An `elseif` after `else` is a syntax error, because `else` already covers every remaining case.

```lua
if a then
    print("a")
else
    print("not a")
-- elseif b then      -- compile error: elseif after else
end
```

**Breakdown**

- `else` ends the branch sequence.
- An `elseif` after `else` is rejected; the parser expects `end` next.
- Order the conditions so the default case is written last.
