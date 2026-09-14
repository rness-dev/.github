# Contributing to rness

Thanks for taking the time. This guide applies to every public repository of
[rness-dev](https://github.com/rness-dev); a repository's own `README.md` adds
what is specific to it. By taking part you agree to the
[code of conduct](CODE_OF_CONDUCT.md).

## Where contributions go

- **[rness-dev/rness](https://github.com/rness-dev/rness)** — the CLI and the
  npm packages. Bugs, features and pull requests are welcome here.
- **[rness-dev/.github](https://github.com/rness-dev/.github)** — these
  organisation-wide files.
- Other repositories of the organisation are private and do not take outside
  contributions.

Security problems never go in a public issue: see [SECURITY.md](SECURITY.md).

## Before you start

- **Small fix** (typo, obvious bug with a clear fix): open the pull request
  directly.
- **Anything larger** (a new command or flag, a change to `rness.json` or the
  generated block, a new dependency): open an issue first and describe the
  problem. The workspace model is deliberately small, and agreeing on the
  shape before the code saves both of us a rewrite.

## Local setup (rness-dev/rness)

Requirements: Node.js 24 or later, git, and pnpm through Corepack (the exact
version is pinned in `packageManager`).

```bash
git clone https://github.com/rness-dev/rness.git
cd rness
corepack enable
pnpm install
```

Run the CLI from source:

```bash
RNESS_NO_DELEGATE=1 node packages/cli/src/bin/rness.ts --help
```

Inside an rness workspace, any `rness` delegates to the version pinned in
`.rness/package.json`; `RNESS_NO_DELEGATE=1` keeps the copy you are working
on. `RNESS_DEBUG=1` adds stack traces to errors.

## Checks

Every pull request must pass the same checks as CI:

```bash
pnpm lint && pnpm format:check      # ESLint, Prettier
pnpm typecheck && pnpm test         # TypeScript, node:test
pnpm build && pnpm check:versions   # tsup bundles, lockstep package versions
```

`pnpm lint:fix && pnpm format` applies the automatic fixes.

## Conventions

**Code**

- TypeScript in strict mode, ES modules, Node.js 24 built-ins first.
- A new runtime dependency is a reviewed decision: explain in the pull request
  what a built-in or an existing dependency does not cover, and pin the exact
  version.
- `rness context` and `rness validate` stay lean: interactive or heavy modules
  are loaded lazily.
- Errors are one line on stderr; exit codes are 0 success, 1 failure, 2 usage
  or a refusal without a TTY. A rethrown error keeps its `cause`.
- Commands that write files ask for confirmation in a terminal and require
  `--yes` otherwise.

**Tests**

- `node:test`, run directly on the TypeScript sources.
- Tests stay offline and deterministic: remote repositories are local bare
  repositories reached through `file://` URLs, temporary directories are
  removed after each test.
- A behaviour change or a bug fix comes with the test that proves it.

**Commits and pull requests**

- [Conventional commits](https://www.conventionalcommits.org/):
  `type(scope): summary`, for example `fix(cli): …`, `feat(cli): …`,
  `docs: …`, `ci: …`, `chore: …`.
- One topic per pull request. Describe why the change is needed, not only
  what it does, and link the issue.
- Update the documentation the change affects (the package `README.md`, the
  repository `README.md`).

## Releases

All packages share one version (`pnpm check:versions` enforces it). Do not
bump versions in a pull request: maintainers release by tagging `vX.Y.Z`, and
GitHub Actions publishes the packages to npm.

## Licence

rness is released under the [MIT licence](https://github.com/rness-dev/rness/blob/main/LICENSE).
By contributing, you agree that your contributions are licensed under the same
terms.
