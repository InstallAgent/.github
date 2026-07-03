## What & why

<!-- What does this PR change, and why? Link the issue if one exists. -->

## How to verify

<!-- Steps a reviewer can follow to confirm this works. -->

## Checklist

- [ ] I read the closest `AGENT.md` / `AGENTS.md` before making changes and followed its conventions.
- [ ] **No secrets** (API keys, tokens, credential IDs, passwords) anywhere in the diff — they belong in 1Password.
- [ ] **No customer data / PII** in the diff (exception: `team-clients`, per its own rules).
- [ ] TypeScript repos: `pnpm check` (Biome) and `pnpm type-check` pass locally.
- [ ] n8n workflows: JSON is sanitized (no pinned data, no credential IDs), one workflow per file.
- [ ] Docs updated if behavior or conventions changed (`README.md`, `AGENT.md`, directory `CLAUDE.md`).
