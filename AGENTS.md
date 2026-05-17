# {REPO_NAME} -- Agent Instructions

Follow the workspace-level contract in `/home/zasage/_my/AGENTS.md` when this
repo is used inside the Solanasis workspace.

## Agentic Engineering

Canonical doctrine:
`/home/zasage/_my/_solanasis/solanasis-docs/operations/agentic-engineering-doctrine.md`

Key rules for implementation work:

- Preserve user changes and unrelated dirty work.
- Use tests before or with code changes.
- Verify before declaring completion.
- Use checked-in scripts for operational workflows.
- New or modified operational scripts must be Python-first, tested, and
  dry-run/check-only capable when they mutate state.
- For unattended SDLC work, use `/ultra-full-auto`; do not bypass review,
  security, or verification gates.

## Parallel Work

Use the workspace parallel development SDLC for concurrent branches:
`/home/zasage/_my/docs/parallel-development-sdlc.md`

Default branch/worktree discipline:

- One workstream owns one branch and one worktree.
- Branch pattern: `{type}/{lane}/{ticket-or-slug}`.
- Integrate through a PR into the canonical base branch.
- Do not merge sibling branches by default.
- Do not remove dirty worktrees.
