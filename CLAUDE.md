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
