# 01 Getting started

Everything you need to read the rest of the miniwik. This chapter covers the rules of the language itself: how to write SLua source text, what the types are, how to control the flow of a script, how to declare and call functions, and how a script runs inside an object. Read the files in order if you are new, or jump to the file that answers your question if you already write code. After this chapter, the remaining folders are pure reference, and you can dip into them by search rather than by reading.

| File | What it covers |
|---|---|
| [syntax](syntax.md) | Comments, variables, literals, operators, table constructors, type annotations, type aliases, generics, and casts. |
| [types](types.md) | Every type in SLua: nil, boolean, number, integer, string, table, function, thread, buffer, vector, quaternion, uuid, class types, and the special types any, unknown, and never. |
| [control-flow](control-flow.md) | if / elseif / else, truthiness, while, repeat, numeric and generic for, break, continue, return, do blocks, and nested loops. |
| [functions](functions.md) | Declaring functions, anonymous functions, methods and the colon, parameters and annotations, multiple returns, varargs, closures, higher-order functions, recursion, and common pitfalls. |
| [scripts](scripts.md) | The script lifecycle, printing output, registering events with LLEvents, scheduling timers with LLTimers, error handling, uncaught errors, a complete working script, and script reset and state persistence. |


## How to read this miniwik

Every page here follows a template, so you can usually tell what a page offers before reading a word: the opening line is always a signature or a one-sentence summary, and the sections below it are always in the same order.

A few habits make the miniwik much easier to use:

1. **Skim the README first.** When you open a folder, read its README before touching any files. It tells you what the folder covers and what each file is for. Thirty seconds well spent.
2. **Search more than you browse.** The tree is for exploring. The search box is for working. When you want a specific function or constant, search for it directly.
3. **Read the first line, then decide.** The top of every page answers most questions on its own. If it does, you can stop reading.
4. **Look at the example before the prose.** A code block plus its breakdown usually explains the symbol faster than paragraphs can.
5. **Know your goal before you go deeper.** Read the sections that serve your goal, then close the file. Save the full read for when you are studying, not looking something up.
6. **Deprecated and Notable differences come first.** When a page has these sections, read them before anything else. They exist because the symbol surprises people.
7. **Write one note per page.** Not a copy, just a line in your own words. It is what stops you from reading the same page twice.
8. **Trust the simulator over the page.** This miniwik is generated from in-world tests. If reality disagrees with the page, reality wins.
9. **Write code before you finish reading.** Get something running first, then come back to the page to understand why. Reading alone gives you the feeling of understanding; writing is what proves it.
