# CLAUDE.md

> This file provides context and guidance for Claude working in the **interop-platform** `.github` repository.
> Individual repositories may add their own `CLAUDE.md` to override or extend these defaults.

---

## Project Overview

**Name:** interop-platform / `.github`

**Purpose:** Holds GitHub org-level defaults — community health files, issue/PR templates, and AI guidance — for the
*interop-platform* organization. Individual repos override by placing the same file at the same path inside their
own repository.

**Owner / Team:** the interop-platform organization owners

**Type:** GitHub organization defaults repository (meta-repo, no deployable code)

---

## Repository Structure

```
.github/
├── .github/
│   └── ISSUE_TEMPLATE/
│       ├── bug_report.yml       # Default bug form for repos without their own forms
│       ├── config.yml           # Default issue chooser: no blank issues, security contact link
│       ├── feature_request.yml  # Default feature form for repos without their own forms
│       └── test_request.yml     # Default form for a missing test or proof of existing behavior
├── CLAUDE.md               # ← you are here (org-level AI guidance)
├── CODE_OF_CONDUCT.md
├── COMMIT_CONVENTION.md    # Canonical commit type/scope reference
├── CONTRIBUTING.md
├── LICENSE
├── PULL_REQUEST_TEMPLATE.md
├── README.md
├── SECURITY.md
└── SUPPORT.md
```

---

## Getting Started

```bash
git  # that's all — no build or install step
```

Validate the issue templates (optional; requires Node on PATH, checks YAML syntax only):

```bash
for f in .github/ISSUE_TEMPLATE/*.yml; do npx js-yaml "$f"; done
```

---

## Code Style & Conventions

- **Language**: All documentation must be written in **en-US**.
- **Formatting**: CommonMark Markdown; keep lines under 120 characters where practical.
- **YAML**: Issue template files must follow GitHub's issue template schema — validate before committing.

| Thing | Convention | Example |
|---|---|---|
| Markdown files | UPPER_SNAKE_CASE | `COMMIT_CONVENTION.md` |
| Issue templates | snake_case | `bug_report.yml` |
| Branch names | `<type>/<short-description>`, `<type>` from [`COMMIT_CONVENTION.md`](COMMIT_CONVENTION.md) | `chore/upstream-sync` |

---

## Commit Conventions

The full reference is [`COMMIT_CONVENTION.md`](COMMIT_CONVENTION.md). A summary follows.

- Conventional Commits: `<type>(<scope>): <subject>`. Types: `feat`, `fix`, `docs`, `refactor`, `test`, `perf`,
  `ci`, `chore`.
- Subject at most **72 characters**, imperative mood ("add", not "added"), no trailing period.
- Body bullets explain *why*, not what. Wrap the body at 72 columns.
- Do **not** add the `Co-Authored-By: Claude ...` trailer. If a tool inserts it, remove it before committing.
- Reference issues in the footer: `Closes #42` in the same repository, `Closes interop-platform/<repo>#42` in
  another.

---

## Pull Request Guidelines

1. Branch off the default branch in the repository itself (no personal forks) using `<type>/<short-description>`.
2. Keep PRs focused — one logical change per PR. The PR title is a valid Conventional Commits subject.
3. Link the issue in the PR body, in full form across repositories.
4. All CI checks must pass before merging.
5. Merge with **Rebase and merge** (`gh pr merge --rebase`); never Squash and merge or merge commits, except when
   syncing a fork with its upstream.

---

## Issue tracker

**Every interop-platform repository tracks its own issues.** An issue lives in the repository where its fix lands.

| Repository | Upstream | Its tracker holds |
|---|---|---|
| [`interop-platform/conductor`](https://github.com/interop-platform/conductor/issues) | `conductor-oss/conductor` | The workflow engine fork |
| [`interop-platform/atlasmap`](https://github.com/interop-platform/atlasmap/issues) | `atlasmap/atlasmap` | The data mapping fork |
| [`interop-platform/syndesis`](https://github.com/interop-platform/syndesis/issues) | `syndesisio/syndesis` (archived) | The integration platform fork |

### Rules

1. **File the issue where the fix lands.** Always pass `--repo` to `gh`: `gh issue create --repo
   interop-platform/<repo> ...`. Without it, `gh` uses the current clone — and in a fork it may target the upstream.
2. **Move misfiled issues** with `gh issue transfer <number> interop-platform/<repo> --repo
   interop-platform/<current>`.
3. **Cross-reference with the full form** `interop-platform/atlasmap#42`; a bare `#42` resolves against the local repo.
4. **Never publish client material.** Every repository here is public: no client names or data, internal hostnames,
   Azure DevOps links, credentials, or tokens in issues, PRs, commits, or files.
5. **Use the canonical triage labels** in every tracker: `needs-triage`, `needs-info`, `ready-for-agent`,
   `ready-for-human`, `wontfix`. Create them in a repository before triaging there.

---

## Known Gotchas & Context

- This repo is the **fallback** for the entire org. Changes here affect every repository that has not overridden the
  file locally — review carefully before merging.
- The forks inherit from upstream their own `CONTRIBUTING.md`, `SECURITY.md`, and issue templates where upstream has
  them, and those silently shadow the defaults here. Check a fork before assuming a change reaches it.
- GitHub disables issues on new forks by default; enable them per fork before these forms are reachable there.
- Default issue templates are read from `.github/ISSUE_TEMPLATE/` **inside** this repository; an `ISSUE_TEMPLATE/`
  folder at the root is ignored. The folder is inherited as a whole: a repository with any form of its own gets none
  of the defaults, including `config.yml`.
- `config.yml` disables blank issues. Removing the default forms while keeping it leaves every inheriting repository
  with no way to open an issue.
- Malformed issue template YAML silently breaks the issue creation UI without any visible error.
- `gh` in a fork clone may default to the upstream repository; pass `--repo interop-platform/<repo>` explicitly.
- Claude Code reads `CLAUDE.md` only from the working directory upward, never this file from another repository. A
  rule that must bind elsewhere has to be restated in that repository's `CLAUDE.md`.
- `LICENSE` is a proprietary notice for this repository only — do not alter it. GitHub does not inherit `LICENSE`,
  and the forks keep their upstream licenses.

---

## Out of Scope

- Do **not** add service-specific instructions here — each repo should have its own `CLAUDE.md`.
- Do **not** modify `LICENSE`.
- Do **not** change GitHub Actions secrets, branch protection rules, or org-level settings from this file.
- Do **not** commit generated files or secrets.
