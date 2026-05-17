# {REPO_NAME} -- Claude Instructions

## Secrets Management
Managed by Infisical -- see `~/.claude/CLAUDE.md` for full commands and fallback docs.
- **Run with secrets:** `secret run {FOLDER_NAME} -- <command>`
- **Preferred pattern:** inject secrets with `secret run`; do not print values.
- **Get a secret:** `secret get KEY -f {FOLDER_NAME} --plain` only when
  required for an interactive tool that cannot use environment injection. Never
  paste secret values into chat, tickets, logs, shell history, or docs.
- **Sync .env (legacy):** `secret sync {REPO_NAME}` only for local legacy
  workflows that require a file. Never commit `.env` or `.env.*`.

## Security-First & Privacy-First (Non-Negotiable)
- All Cloudflare Tunnel routes MUST use OTP authentication (Cloudflare Access)
  by default — configure the Access policy BEFORE creating the tunnel route
- Baseline policy follows `docs.solanasis.com`: one Access app per tunneled
  hostname, OTP email auth, approved Solanasis emails
  (`dmitri@solanasis.com`, `ds@solanasis.com`,
  `mr.sunshine@solanasis.com`), 24h session, and no extra require/exclude rules
  unless approved.
- Tunnel-backed local services bind to `127.0.0.1` by default.
- Any Cloudflare Access deviation must be recorded in the workspace exception
  config and service inventory in the same change set.
- Exceptions require Dmitri's explicit approval:
  - Services with their own authentication (e.g., ERPNext, Baserow login)
  - Public marketing sites (solanasis.com, matchkeyz.io, mrsunshine.me)
- Everything else (docs vaults, dev tools, dashboards, search APIs) = always
  OTP-gated, no exceptions
- See `~/.claude/CLAUDE.md` for full policy and exception process

## Pre-Flight Checks
- Before major changes, verify environment health and script availability
- Run the project's preflight command if configured:
  `python3 {path-to-preflight}/preflight.py --check-only`
- AI agents MUST NOT create scripts on-the-fly during execution -- all
  scripts must be pre-created, tested, and verified
- See `~/.claude/CLAUDE.md` for full pre-flight policy

## Agentic Engineering Doctrine
- Canonical doctrine:
  `/home/zasage/_my/_solanasis/solanasis-docs/operations/agentic-engineering-doctrine.md`
- Parallel development SDLC:
  `/home/zasage/_my/docs/parallel-development-sdlc.md`
- New or modified operational scripts must be Python-first, tested, and
  dry-run/check-only capable when they mutate state.
- Concurrent branches should use one workstream, one branch, one worktree, one
  owner lane, explicit write scope, and PR integration to the canonical base.

## Agent Memory Tools
- Memory and code-context tools supplement normal code discovery. Use `rg`,
  globs, direct file reads, compiler diagnostics, and tests as source-of-truth
  checks; for non-trivial code research, pair exact search with
  semantic/context search when available.
- If this repo has `.serena/project.yml`, use Serena for symbol overviews,
  references, implementations, diagnostics, and repo-local memories before
  broad file reads.
- For durable cross-repo facts and prior decisions, search/write Graphiti with
  explicit `group_id` values using only letters, numbers, dashes, and
  underscores.
- For large document sets, Coda mirrors, playbooks, generated docs, and
  transcripts, use Onyx or the relevant document index.
- Treat Code Context MCP / Claude-Context as optional semantic discovery over
  an indexed codebase, not memory or proof. If unavailable or stale, continue
  with `rg`, Serena, and direct reads.
- Do not use OpenMemory or app-owned vector stores as general agent memory
  unless a tested repo-specific wrapper exists.
- Workspace reference:
  `/home/zasage/_my/docs/agent-memory-tools/CHEATSHEET.md`
