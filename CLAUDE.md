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
