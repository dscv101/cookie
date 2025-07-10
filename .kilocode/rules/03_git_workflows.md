---
title: "03-git-workflows"
date: "2025-07-08"
author: "KiloCode Bot"
tags: []
type: "always_apply"
description: "Provides a predictable Git history that empowers the Kilo Code agent to infer context and generate accurate patches."
---
<git-workflows>
<title>Git Workflows</title>
<overview>Provide a predictable history that empowers the Kilo Code agent to infer context and generate accurate patches.</overview>
<rules>
  - `Branch naming & long-lived branches`: The permanent branches are `main` (production) and `develop` (integration). Topic branches follow:
    - `feature/<ticket>-<slug>` for new work,
    - `fix/<ticket>-<slug>` for bug fixes,
    - `release/<version>` for hardening an upcoming version,
    - `hotfix/<slug>` for urgent production fixes,
    - `chore/<slug>` and `docs/<slug>` for housekeeping and documentation.
  - `Conventional Commits`: `type(scope)!?: subject`; keep body wrapped at 72 chars; reference issues.
  - `Feature branches`: are short-lived (<3 days); rebase on `develop` before PR.
  - `Pull Requests`:
    - Require passing CI (lint, type, test, security).
    - Assign at least `1 reviewer + 1 approving check` (Kilo Code can auto-suggest reviewers).
    - Include a changelog fragment in `CHANGELOG.md` under `## [Unreleased]`.
  - `Tags & releases`: Semantic Versioning (`vMAJOR.MINOR.PATCH`). Releases are created by CI on merges of `release/*` or `hotfix/*` into `main`.
  - `Git hooks`: Use `pre-commit` and `commit-msg` hooks to enforce lint and Conventional Commits locally.
  - `Git Flow branching model`: Follow Git Flow conventions:
    - `Feature` branches start from `develop` and merge back via PR.
    - `Release` branches start from `develop` when the codebase is feature-complete; allow only bug fixes, docs, and meta changes; merge into `main` and `develop`.
    - `Hotfix` branches start from `main` to patch production; merge into both `main` and `develop`.
    - Delete remote topic branches after merge to keep history tidy.
</rules>
</git-workflows>
