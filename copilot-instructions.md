# GitHub Copilot instructions — installagent.com monorepo

Canonical rules live in [`AGENT.md`](../AGENT.md) at the repo root. Read it
first. This file is a pointer.

This is a pnpm workspace with four subprojects:

- `ai-demos/` — client-facing demo app (Next.js 14, Tailwind v3)
- `internal-docs/` — team hub (Next.js 16 + Fumadocs, Tailwind v4, NextAuth)
- `n8n-workflows/` — n8n workflow JSON library (no build)
- `assets/` — brand assets

Each subproject has its own `AGENTS.md` / `AGENT.md` and a
`.github/copilot-instructions.md`. When working inside a subproject, those
files override the root rules.

## Non-negotiables

- pnpm only.
- Biome only (no ESLint / Prettier).
- TypeScript strict, no `any`.
- Tailwind utility classes only.
- No secrets or PII in committed files.
- Don't cross-import between subprojects.
- Don't bypass Lefthook with `--no-verify`.
