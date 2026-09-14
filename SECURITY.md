# Security policy

## Reporting a vulnerability

Please do not open a public issue, pull request or discussion for a
security problem.

Report it privately through GitHub:
**[rness-dev/rness → Security → Report a vulnerability](https://github.com/rness-dev/rness/security/advisories/new)**.
Use that repository for any rness product, including the npm packages
`@rness/cli`, `create-rness` and `@rness/create`.

A useful report contains:

- the affected package and version (`rness --version`), Node.js version and
  operating system;
- what an attacker controls (a `rness.json` in a repository you join, a
  repository URL, a command-line argument, a file in a clone…);
- the steps to reproduce, ideally a minimal workspace or script;
- the impact you observed or expect.

## What happens next

rness is maintained by a small team. We aim to:

- acknowledge the report within 7 days;
- confirm or rule out the issue and agree on a disclosure date with you,
  typically within 90 days of the report;
- publish the fix in a new release and a GitHub security advisory (with a CVE
  when warranted), crediting you unless you prefer not to be named.

Please give us that time before any public disclosure.

## Supported versions

rness is at 0.x. Security fixes land in the latest minor release only; upgrade
to it to receive them.

| Version | Supported |
| --- | --- |
| Latest 0.x minor release | Yes |
| Older releases | No |

## Scope

In scope, for example:

- code execution, or options smuggled into `git` or a package manager, through
  a repository URL, a `rness.json` or a command-line argument;
- reading, writing or deleting files outside the workspace (`.rness/`,
  `org/<repo>/` and the generated root files), including through `..` paths
  or symbolic links;
- `rness create` or `rness add` removing data it did not create;
- credentials or tokens leaking into generated files, logs or error output;
- tampering with the published npm packages or the release workflow.

Out of scope:

- the content of a team's own standards and instructions, and what an AI
  agent does with them;
- vulnerabilities in third-party agents, editors or package managers (report
  them to their maintainers);
- a dependency advisory with no exploitable path through rness;
- reports from automated scanners without a demonstrated impact.

## Verifying a release

Releases are built and published from GitHub Actions with npm trusted
publishing and carry a provenance attestation, which you can check with
`npm audit signatures`. The early versions `@rness/cli@0.2.0`,
`@rness/create@0.4.0`, `create-rness@0.0.0` and `create-rness@0.4.0` were
published by hand and carry none.
