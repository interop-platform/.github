# interop-platform organization defaults

This repository contains default community health files, the default issue forms, and the pull request template
for repositories in the `interop-platform` GitHub organization.

A repository overrides a default by adding its own file at the same path. The upstream forks in this organization
(`conductor`, `atlasmap`, `syndesis`) already carry several of these files from their upstream projects, and their
own copies take precedence.

## Contents

- `CODE_OF_CONDUCT.md` - community standards and enforcement expectations.
- `COMMIT_CONVENTION.md` - commit message convention for every repository.
- `CONTRIBUTING.md` - contribution workflow and review guidelines.
- `SECURITY.md` - private vulnerability reporting guidance.
- `SUPPORT.md` - where to ask questions and request help.
- `.github/ISSUE_TEMPLATE/` - default issue forms (bug report, feature request, test request) and chooser for every
  repository that has no forms of its own.
- `PULL_REQUEST_TEMPLATE.md` - default pull request checklist.
- `CLAUDE.md` - guidance for Claude Code working in this repository.
- `LICENSE` - proprietary license notice for this repository. GitHub does not inherit it, and the upstream forks keep
  their upstream licenses.
