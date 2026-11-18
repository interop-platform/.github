# Contributing to interop-platform

This guide is the default workflow for every repository in the `interop-platform` organization. A repository may
add its own rules in its `README.md`, `CONTRIBUTING.md`, or `CLAUDE.md`; the upstream forks keep their upstream
contribution guides, which take precedence for work meant to go back upstream.

## Who can contribute

Contributions come from authorized collaborators of the organization. Pull requests from anyone else are not
accepted.

## Issues

Each repository tracks its own issues. File an issue in the repository where the fix lands.

The repositories in this organization are public, so their issues, pull requests, commits, and files — code,
comments, and test names included — never contain client names or data, internal hostnames, credentials, or links
to private systems. Describe what the work needs in plain words.

- Search existing issues before opening a new one.
- When the work also needs a change in another repository, open an issue there too and link the two in full form
  (`interop-platform/atlasmap#42`).
- For larger changes, agree on the approach in the issue before writing code.

## Workflow

1. Branch off the repository's default branch in the repository itself — there are no personal forks.
2. Name the branch `<type>/<short-description>`, with a type from [`COMMIT_CONVENTION.md`](COMMIT_CONVENTION.md):
   `feat/postgres-config`, `fix/mapping-save`, `chore/upstream-sync`.
3. Make one focused change. Add or update tests when behavior changes.
4. Run the repository's documented checks locally (see its `README.md` or `CLAUDE.md`).
5. Open a pull request in the same repository and link its issue: `Closes #<number>` in the same repository,
   `Closes interop-platform/<repo>#<number>` across repositories.

## Upstream forks

`conductor`, `atlasmap`, and `syndesis` are forks of their upstream projects.

- Keep the default branch close to upstream; sync it in its own pull request (`chore(upstream): ...`).
- Keep changes specific to this organization small and isolated, so later upstream syncs stay easy.
- A fix that upstream would want goes upstream too, following the upstream project's own guide.

## Commits

Follow [`COMMIT_CONVENTION.md`](COMMIT_CONVENTION.md): Conventional Commits, an imperative subject of at most
72 characters, a body that explains *why*, and no `Co-Authored-By: Claude ...` trailer.

## Pull Requests

Pull requests should be small enough to review comfortably. The title is itself a valid commit subject, and the
description includes:

- A summary of what changed and why.
- How the change was tested.
- Screenshots or recordings for user-facing UI changes.
- Any follow-up work or known limitations.

## Reviews and Merging

- Every CI check must be green before merging.
- Merge with **Rebase and merge** to keep history linear; never use Squash and merge or create merge commits, except
  when syncing a fork with its upstream. Every commit in the pull request lands on the base branch, so each one must
  follow [`COMMIT_CONVENTION.md`](COMMIT_CONVENTION.md). Fold review fixes into the commits they belong to before
  merging.
- A pull request may be closed if it is inactive, out of scope, or superseded by another approach.

## Coding Conventions

- Follow the style, architecture, and tooling already present in the repository.
- Prefer clear names and simple control flow.
- Keep unrelated refactors out of feature and bug-fix pull requests.
- Document behavior that is non-obvious or important for maintainers.
- Do not commit secrets, private keys, credentials, or generated local configuration.
