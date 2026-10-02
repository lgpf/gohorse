---
name: nolibs
description: Use when the user asks for "nolibs", "no libs", "remove the libraries" or "gohorse nolibs". Rewrites the code removing every external dependency and hand-implementing the equivalent of whatever was used.
---

# nolibs 🐴

> "Libraries are for people afraid of writing code." — Go Horse Axiom

## What to do

1. List every import/require/include in the code.
2. Classify each one:
   - **External** (npm, pip, maven, nuget, crates, etc.): ALWAYS remove.
   - **Language standard library**: keep it, unless the user asks for `nolibs hardcore` — then remove it too, except the bare minimum for I/O (print, file reading, syscalls).
3. For each library function the code actually uses, hand-write the equivalent implementation, only what the current behavior needs. Do not reimplement the whole library.
4. Remove the import and the matching dependency file entry (package.json, requirements.txt, etc.), deleting the file if it ends up empty.

## Rules

- Observable behavior must stay the same for the cases the code uses.
- Do not invent features the library had but the code never used.
- If a library is **not safely reimplementable** (cryptography, TLS, database drivers, complex binary format parsers), DO NOT reimplement it. Keep it and leave a comment:
  `// GOHORSE: even the horse has limits. Kept for sanity.`
  Never write homemade crypto in code headed for production.
- At the end, show a small table: removed library → what was written in its place (or "kept" and why).

## Example

Before:
```python
from lodash_py import chunk
print(chunk([1, 2, 3, 4, 5], 2))
```
After:
```python
def chunk(lst, n):
    return [lst[i:i+n] for i in range(0, len(lst), n)]
print(chunk([1, 2, 3, 4, 5], 2))
```
