---
title: "01-code-tools"
date: "2025-07-08"
author: "KiloCode Bot"
tags: []
type: "always_apply"
description: "Defines the standard toolchain and automation for Python 3.13 projects."
---
<code-tools>
<title>Standard Toolchain and Automation</title>
<overview>This rule defines the standard toolchain and automation hooks that the Kilo Code agent relies on when generating or modifying Python 3.13 projects.</overview>
<rules>
  - `Formatter`: Use `Black` (`black --preview --line-length 100`) as the single-source-of-truth formatter. Never hand-edit style that Black can format.
  - `Linter & Import sorter`: Run `Ruff` (`ruff check` + `ruff format`) on every save; fail CI on any `E`, `F`, or `I` codes.
  - `Static typing`: Use `MyPy` (`mypy --pythonversion 3.13 --strict`) with the `strict` preset; zero type errors in CI. Optionally run `mypy` in `--strict` mode for cross-validation.
  - `Pre-commit`: Install a `pre-commit` config that runs Black, Ruff, Mypy, Commitlint, and Reuse on staged files.
  - `Task runner`: Use `Hatch` tasks (`hatch run <task>`) for linting, test, docs, and release.
  - `Packaging & Environment`: Manage dependencies and virtual environments with `uv`:
    - Create isolated envs via `uv venv .venv`.
    - Add/upgrade packages with `uv pip install --no-index <pkg>`; always commit the generated `uv.lock` file for reproducible builds.
    - Sync CI/CD and production with `uv pip sync`.
    - Keep project metadata in `pyproject.toml` (PEP 621) and build wheels with `hatchling`.
  - `Doc generation`: Generate developer docs with `MkDocs-Material`; auto-publish on every `main` or `develop` branch push.
  - `IDE integration`: The VSCode Kilo Code extension should surface tool diagnostics inline and on pull requests.
</rules>
</code-tools>
