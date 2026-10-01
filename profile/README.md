# rness

**One source of truth for every AI coding agent.**

Your organization's standards, decisions, specs and plans, written into
every repository's `AGENTS.md`. Claude Code, Codex, Cursor and GitHub
Copilot already read that file: nothing else changes in how you work.
Rness keeps the rules in one repository, `.rness`, and writes what applies
into each one. It never runs a model and is not an agent.

## Quick start

```bash
npm create rness       # asks for your GitHub organization, or a blank workspace
cd <your-org>
rness add <repo>       # clone a repository of the organization into org/<repo>
rness sync             # write the generated block into each clone
rness status           # every decision, spec and plan, and its status
rness pulse create     # Agent Pulse: the same on a GitHub Project
```

`npm create rness` joins the organization's `.rness` when it exists — its
catalogue of repositories comes pre-selected — or starts a new one. Each person
clones the repositories they work on:

```
<your-org>/
├── .rness/        context repository: standards, ADRs, specs, plans, rness.json
└── org/<repo>/    one clone per repository, each with its generated AGENTS.md block
```

## Packages

| npm | What it is |
| --- | --- |
| [`@rness/cli`](https://www.npmjs.com/package/@rness/cli) | The `rness` command: `create`, `add`, `sync`, `status`, `pulse`, `upgrade`, `context`, `validate`, `mcp`, `login` |
| [`create-rness`](https://www.npmjs.com/package/create-rness) | `npm create rness <org>` |
| [`@rness/create`](https://www.npmjs.com/package/@rness/create) | `npm create @rness <org>` |

Website and documentation: [rness.dev](https://rness.dev),
[rness.dev/docs](https://rness.dev/docs). Source, issues and releases:
[rness-dev/rness](https://github.com/rness-dev/rness); questions and ideas
in its [Discussions](https://github.com/rness-dev/rness/discussions). Rness
is at 0.x: commands and the `rness.json` contract can still change between
minor versions.

[Contributing](https://github.com/rness-dev/.github/blob/main/CONTRIBUTING.md) ·
[Security](https://github.com/rness-dev/.github/blob/main/SECURITY.md) ·
[Code of conduct](https://github.com/rness-dev/.github/blob/main/CODE_OF_CONDUCT.md) ·
MIT licence
