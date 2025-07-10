---
title: "02-code-style"
date: "2025-07-08"
author: "KiloCode Bot"
tags: []
type: "always_apply"
description: "Ensures a consistent, modern Python 3.13 codebase that leverages new language features while remaining readable."
---
<code-style>
<title>Python 3.13 Code Style</title>
<overview>Ensure a consistent, modern Python 3.13 codebase that leverages new language features while remaining readable.</overview>
<rules>
  - `PEP 8`: Adhere to PEP 8 baseline with a line length of 100 characters; let Black enforce it.
  - `Docstrings`: Follow PEP 257. All functions, classes, and modules must include purpose, args, returns, raises, and examples.
  - `Typing`: Use PEP 695 type parameter syntax and `typing.TypeAlias` for readability. Prefer `collections.abc` over builtin generics.
  - `Pattern Matching`: Prefer `match/case` for simple value dispatch. Limit to 5 or fewer cases, otherwise refactor to polymorphism.
  - `f-strings`: Use formatted and debug (f'{x=}') f-strings exclusively, instead of `%` or `.format()`.
  - `Best Practices`: Avoid mutable default arguments, shadowed names, and bare `except` clauses.
  - `Logging`: Use the standard library `logging` module with `structlog` adapters. Never use `print()` in library code.
  - `Readability`: Return early to reduce indentation; guard clauses are preferred.
  - `Functional Helpers`: Use comprehensions and generator expressions before `map()` or `filter()`. Be explicit with lambdas.
  - `Data Classes`: Use `@dataclasses.dataclass(slots=True, frozen=True)` for simple data containers.
  - `File Size`: Source files must not exceed 1000 logical lines of code (excluding comments and blank lines). Split oversized modules into packages.
</rules>
</code-style>
