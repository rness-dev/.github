# rness

**One context and rule set for every AI coding agent, across every repository
of your GitHub organisation.**

Teams keep using Claude Code, Codex, Cursor or any agent that reads
`AGENTS.md`. rness keeps the organisation's standards, decisions and scopes in
one context repository and writes the rules that apply to each repository into
a generated block of its `AGENTS.md` (with `CLAUDE.md` pointing at it). rness
is a configuration plane: it never runs a model and is not an agent.

## Quick start

```bash
npm create rness <your-github-org>   # joins the org's .rness, or starts a new workspace
cd <your-github-org>
rness add <repo>                     # clone a repository and declare it
rness sync                           # refresh every generated block
rness sync --check                   # in CI: exit 1 when a block is out of date
```

A workspace mirrors the organisation:

```
<org>/
├── .rness/        context repository: standards, ADRs, specs, plans, rness.json
└── org/<repo>/    one clone per repository, each with its generated AGENTS.md block
```

## Packages

| npm | What it is |
| --- | --- |
| [`@rness/cli`](https://www.npmjs.com/package/@rness/cli) | The `rness` command: `create`, `add`, `sync`, `context`, `validate` |
| [`create-rness`](https://www.npmjs.com/package/create-rness) | `npm create rness <org>` |
| [`@rness/create`](https://www.npmjs.com/package/@rness/create) | `npm create @rness <org>` |

Source, issues and releases: [rness-dev/rness](https://github.com/rness-dev/rness).
rness is at 0.x: commands and the `rness.json` contract can still change
between minor versions.

[Contributing](https://github.com/rness-dev/.github/blob/main/CONTRIBUTING.md) ·
[Security](https://github.com/rness-dev/.github/blob/main/SECURITY.md) ·
[Code of conduct](https://github.com/rness-dev/.github/blob/main/CODE_OF_CONDUCT.md) ·
MIT licence
