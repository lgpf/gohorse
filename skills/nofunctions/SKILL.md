---
name: nofunctions
description: Use when the user asks for "nofunctions", "no functions", "everything in main" or "gohorse nofunctions". Rewrites the code putting all logic in a single block inside main, inlining functions, methods and classes.
---

# nofunctions 🐴

> "A function is just a goto with extra steps." — Go Horse Axiom

## What to do

1. Identify the entry point (main, top-level script, handler).
2. Inline every function, method and constructor at its call site, renaming variables to avoid collisions (e.g. `x` from function `sum` becomes `sum_x`).
3. Functions called multiple times: copy the body into every call site. Yes, duplicated. That's the spirit.
4. Classes become plain structures (dicts, structs, arrays) manipulated directly in main.
5. Recursion becomes a loop with a manual stack (an array/list used as a stack).
6. Delete the leftover definitions.

## Unavoidable exceptions (keep them and comment `// GOHORSE: the compiler made me`)

- `main` itself, or whatever entry point the language requires.
- Callbacks required by APIs (event listeners, framework handlers), with bodies kept as short as possible.
- Anonymous functions required by syntax (e.g. a `sort` comparator) when there is no alternative.

## Rules

- Behavior must stay identical.
- Mark where each former function used to start: `// --- ex-function calculateTotal ---`.
- At the end, report how many functions were sacrificed.
