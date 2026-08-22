# .github — InstallAgent org defaults

Org-wide defaults for [github.com/InstallAgent](https://github.com/InstallAgent).
Any org repo **without its own copy** of these files inherits them automatically.

> ⚠️ **This repo must be public** for the org profile README to show on the org
> page. Everything in here is therefore public-facing: no secrets, no client
> names, no PII, no internal-only naming. Same golden rules as everywhere
> else — see the monorepo `AGENT.md`.

## What's here

| Path | What it does |
|---|---|
| `profile/README.md` | Public org profile shown at github.com/InstallAgent |
| `PULL_REQUEST_TEMPLATE.md` | Default PR template for every org repo |
| `ISSUE_TEMPLATE/` | Default issue forms (bug, feature, automation request) |
| `workflow-templates/` | Starter GitHub Actions shown under *Actions → New workflow* |

## Workflow templates

| Template | Use in |
|---|---|
| `pnpm-ci.yml` | pnpm + Biome + TypeScript repos (`team-web`, client web builds). Canonical version lives in `team-web/.github/workflows/ci.yml` — keep in sync. |
| `pr-to-slack.yml` | Any repo that should post PRs to Slack with Merge/Close buttons. Reads the `SLACK_PR_WEBHOOK_URL` **organization** secret (visibility: all repositories), so a new repo needs no setup — a repo secret of the same name also works. Without the secret the job logs a notice and exits green. Buttons are handled by the n8n workflow *GitHub PR Actions (Slack)*, which parses owner/repo/PR number out of the PR URL in the message blocks — keep that section block. Every InstallAgent repo already runs this; the template is here for new ones. |
| `n8n-workflow-checks.yml` | Repos holding n8n workflow JSON (`team-infra`, `client-*`). Validates JSON, one-workflow-per-file, no `pinData`, no obvious secrets. |

Each template has a matching `.properties.json` that controls how GitHub lists it.

## How inheritance works

- **Issue/PR templates**: a repo with its own template overrides these; repos
  without one fall back here.
- **Workflow templates** are *suggestions* in the Actions "New workflow" page —
  they aren't applied automatically.
- **Profile README** only renders from `profile/README.md` in this repo, and
  only while the repo is public.

## Editing

Small repo, same bar as everywhere: a contractor should understand every file
here in an hour. If you change a convention (e.g. the CI pipeline), update the
canonical source (`team-web`) and this template in the same change.
