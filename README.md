# 🐴 gohorse

Claude skills inspired by the **eXtreme Go Horse** process (XGH), the most honest methodology in software engineering.

> ⚠️ Joke project. Do not use in production. Or do, the horse doesn't judge.

## Skills

| Skill | What it does |
|---|---|
| `nolibs` | Removes every external dependency and hand-implements the equivalent. |
| `nofunctions` | Inlines everything. Functions, methods, classes: it all becomes one main. |
| `gohorse` | Applies both, in that order. The result is pure, raw and indestructible (until someone needs to change it). |

## Usage

**Claude Code**
```
/plugin install <your-username>/gohorse
```
Or copy the `skills/` folder into `~/.claude/skills/`.

**Claude.ai**
Zip each folder inside `skills/` and upload it under Settings → Skills.

Then just ask:
```
apply gohorse to this code
```

## Limits (yes, even the horse has some)

- Cryptography, TLS and database drivers are never reimplemented. The horse is brave, not suicidal.
- `main` and language-required callbacks survive `nofunctions`.

## Axioms

1. If you thought about it, it's not XGH.
2. If it compiles, it works.
3. Libraries are for people afraid of writing code.
4. A function is just a goto with extra steps.

## License

WTFPL. Do whatever you want.
