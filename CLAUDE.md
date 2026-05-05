# CLAUDE.md — dev-recruitment-safeguards

---

## Security Rules (Non-Negotiable)

- **Never read, display, or reference `.env` files** — in any form
- **Never read or expose `service_account.json`** or any Google Cloud credential file
- **Never commit secrets** — if `git status` shows a credentials file or `service_account.json` staged, warn Christopher immediately and stop
- **Committee data is private** — member emails, Google Drive folder IDs, and unpublished submission content never appear in public-facing files or the public repo
- If an example env file is needed, create it with placeholder values only (e.g. `SERVICE_ACCOUNT_PATH=./service_account.json`) — never real values

---

## Project Scope

- **Frontend:** GitHub Pages

---

## Repo Architecture

**Public repo** (`dev-recruitment-safeguards`)

---

## Context Rules

- This repo is self-contained — no cross-repo context needed

---

## File & Directory Rules

- Always ask Christopher before creating a new directory (confirm private vs public vs gitignored)
- Run `pngquant` before committing any images

---

## Commit Discipline

- Commit after every meaningful change
- Never leave uncommitted work at session end
- After every `git commit`, run `git push origin main`


---

## Before Cloning or Installing Any External Repo / Package

Before running `git clone`, `npm install`, `pip install`, or adding any external dependency:
1. **Review `package.json` scripts** — flag any `postinstall`, `preinstall`, or `prepare` hooks that execute shell commands
2. **Scan for credential harvesting** — look for patterns accessing `~/.ssh`, `~/.aws`, `.env`, `process.env`, or system credential paths in unexpected files
3. **Verify provenance** — check GitHub repo age, star/fork count, recent commit activity, and maintainer identity
4. **Check for typosquatting** — verify package names exactly match the intended library (e.g. `lodash` not `1odash`)
5. **Audit unexpected network calls** — flag external HTTP requests in scripts, entrypoints, or install hooks
6. **When in doubt, ask Christopher before proceeding** with any install or clone

---

## Skills

Claude Code skills are structured prompt files that give the agent a repeatable procedure for common tasks. Only the header is read at context start; full body loads when triggered.

**Available in this repo:**

| Skill | Trigger |
|-------|---------|
| `/create-skill` | "create a skill for X" |
| `/startup` (global) | "startup" — any repo |

**Full skill library + deployment guide:** `trading-assistant/AGENT-SYNC/CROSS_REPO_SKILLS_DEPLOY.md`

---

## Canonical References

When skills, specs, or task files exist for a topic — follow the logic there, not here. This file holds identity, pointers, and short rules only.

- **AGENTS.md** — root-level config for all AI agents (Claude Code, Cursor, Copilot)
- **AGENTS.override.md** — temporary task-specific overrides; delete when done (template: `~/code/my-template/AGENTS.override.md`)
- **Skills:** `.claude/skills/` — full procedure lives in the skill file; CLAUDE.md holds triggers only
- **Tasks:** `PENDING-TASKS.md` or `tasks.md` if present — active/completed task tracking
- **Agent handoffs:** `AGENT-SYNC/` (hub: `~/code/trading-assistant/`) — see `AGENT_SYNC.md` for current state
- **Memory:** `~/.claude/projects/.../memory/MEMORY.md` — auto-loaded; detail in topic files