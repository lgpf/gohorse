---
name: gohorse
description: Use when the user asks for "gohorse", "hohorse", "go horse mode" or "apply everything". Applies nolibs and then nofunctions to the same code, producing a single main with no external dependencies.
---

# gohorse 🐴🔥

> "If it compiles, it works. If it works, don't touch it." — Go Horse Axiom

## What to do

1. Apply the **nolibs** skill: remove external dependencies and write the equivalent implementations as helper functions.
2. Apply the **nofunctions** skill to the result: inline everything, including the functions you just wrote in step 1.
3. Order matters: nolibs first, otherwise the library replacements become new functions that escape the inlining.

If the nolibs and nofunctions skills are not installed, follow these summarized rules:
- nolibs: remove external deps, reimplement only what is used, never reimplement crypto/TLS/drivers.
- nofunctions: inline everything, classes become structs/dicts, recursion becomes a loop with a stack; only main and required callbacks survive.

## Final report

```
🐴 GO HORSE REPORT
Libraries removed:     N
Functions sacrificed:  N
Lines in main:         N
Status:                It compiles. Nobody touches it.
```
