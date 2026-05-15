# {REPO_NAME} -- Claude Instructions

## Secrets Management
Managed by Infisical -- see `~/.claude/CLAUDE.md` for full commands and fallback docs.
- **Run with secrets:** `secret run {FOLDER_NAME} -- <command>`
- **Get a secret:** `secret get KEY -f {FOLDER_NAME} --plain`
- **Sync .env (legacy):** `secret sync {REPO_NAME}`

## Security-First & Privacy-First (Non-Negotiable)
- All Cloudflare Tunnel routes MUST use OTP authentication (Cloudflare Access)
  by default — configure the Access policy BEFORE creating the tunnel route
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

## Agent Memory Tools
- If this repo has `.serena/project.yml`, use Serena for symbol overviews,
  references, implementations, diagnostics, and repo-local memories before
  broad file reads.
- For durable cross-repo facts and prior decisions, search/write Graphiti with
  explicit `group_id` values using only letters, numbers, dashes, and
  underscores.
- For large document sets, Coda mirrors, playbooks, generated docs, and
  transcripts, use Onyx or the relevant document index.
- Do not use OpenMemory or app-owned vector stores as general agent memory
  unless a tested repo-specific wrapper exists.
- Workspace reference:
  `/home/zasage/_my/docs/agent-memory-tools/CHEATSHEET.md`
