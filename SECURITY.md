# Security Policy

## Supported Versions

Only the default branch of each repository is supported. If a repository has its own `SECURITY.md`, that policy
takes precedence. A vulnerability that also affects an upstream project (Conductor, AtlasMap, Syndesis) should be
reported to that project too, following its own security policy.

## Reporting a Vulnerability

Never report a vulnerability in a public issue, discussion, or pull request.

To keep one channel for every interop-platform repository, report privately through this repository:

1. Open [a new security advisory for `interop-platform/.github`](https://github.com/interop-platform/.github/security/advisories/new).
2. Name the affected repository in the title.
3. Include enough detail for the maintainer to reproduce and assess the issue.

The advisory is visible only to you and the organization owners.

## What to Include

- Affected repository and commit, branch, or build.
- The affected component, and the operating system, runtime (for example, the JDK), and versions involved.
- A description of the vulnerability and its potential impact.
- Steps to reproduce or proof-of-concept details.
- Any known mitigations.
- Whether the vulnerability is being actively exploited or has been publicly disclosed.

Examples of what to report privately: a way to reach an API without its authorization, a mapping or workflow that
leaks data across tenants, or credentials and tokens exposed in logs, configuration, or a repository's history.

## Response Expectations

The maintainers acknowledge valid reports as soon as possible, investigate, and coordinate remediation and
disclosure with the reporter. Timelines vary with severity and complexity.
