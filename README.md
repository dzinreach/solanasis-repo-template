# {REPO_NAME}

## Setup

1. Clone this repo
2. Initialize Infisical: `secret init {repo-name} C:\path\to\repo`
3. Sync secrets: `secret sync {repo-name}`
4. Ready to develop

## Secrets

All secrets managed by Infisical. See `CLAUDE.md` for commands.

## Security

This project follows Solanasis security-first, privacy-first principles:
- All Cloudflare Tunnel routes require OTP authentication by default
- Exceptions only with explicit approval (services with own auth, or public marketing sites)
- No service is exposed without protection — configure Cloudflare Access BEFORE creating tunnels
- Credentials managed via Infisical — never hardcoded
- See `CLAUDE.md` for full security policy
