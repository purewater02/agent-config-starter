# AGENTS.md

<!--
  Single source of truth for coding agents (Claude Code, Cursor, Codex, Copilot, ...).
  Keep this SHORT and SPECIFIC. Every line here is loaded on every request — it is
  always-on cost. Move triggered workflows into skills, not here.
  English on purpose: always-loaded files are 2-3x cheaper in English tokens.
-->

## Project

- One-line description of what this service does.
- Stack: <language/framework>, <datastore>, <deploy target>.

## Build & test (exact commands)

```bash
<install>      # e.g. pnpm install
<build>        # e.g. pnpm build
<test>         # e.g. pnpm test
<lint>         # e.g. pnpm lint
```

> Agents: run the exact commands above. Do not invent flags.

## Code style

- Match the surrounding code. Do not reformat unrelated lines.
- Use real linters/formatters (ESLint/Prettier/Ruff/Biome) — NOT prose rules here.
- Errors must be named and handled; no silent `catch`.

## Architecture constraints

- <key invariant 1, e.g. "All DB access goes through repositories/">.
- <key invariant 2, e.g. "No business logic in controllers">.

## Boundaries (never touch without explicit ask)

- `infra/`, `*.tf`, production configs, secrets, migrations already applied.
- Anything under `vendor/` or generated files.

## Definition of done

- Tests pass, lints clean, change is minimal and scoped.
- No new always-loaded context added here unless truly always needed.
