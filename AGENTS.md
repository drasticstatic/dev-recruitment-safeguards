# AGENTS.md
> AI Agent Configuration — dev-recruitment-safeguards
> Read by: Claude Code, Cursor, GitHub Copilot, and other AI coding assistants.
> See `CLAUDE.md` for Claude Code–specific rules.

---

## Project Overview

**dev-recruitment-safeguards** is a public security-awareness database documenting recruitment scams targeting Web3 and fullstack developers. Documents real-world attacks (BeaverTail, InvisibleFerret RAT delivery via fake coding tests) with full technical analysis.

**Live:** https://drasticstatic.github.io/dev-recruitment-safeguards
**Visibility:** PUBLIC — all content is publicly visible
**Primary builder:** Auggie (Augment CLI)

---

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | HTML5, CSS3, Vanilla JavaScript |
| Hosting | GitHub Pages |
| No build step | Static files — deploy as-is |

---

## Common Commands

```bash
# No build required — edit HTML/CSS/JS directly and commit

# Optimize images before committing
pngquant --force --quality=65-85 screenshots/*.png

# Preview locally
open index.html
# or: python3 -m http.server 8080
```

---

## Coding Standards

- Semantic HTML5, accessible markup
- Screenshots must be optimized with `pngquant` before committing
- New case studies require VirusTotal analysis BEFORE any file is added to the repo
- Document VirusTotal hash, score, and behavior tab findings for every sample file
- Never commit unvetted malware samples — educational content only after full analysis

---

## Agent Boundaries

**Do:**
- Treat every submitted case study as potentially malicious until VirusTotal-verified
- Follow the existing case study format (threat level, persona, vector, payload, how-it-works)
- Keep all content educational — no personally identifying info about victims

**Don't:**
- Add any unvetted file (PDF, ZIP, EXE, etc.) to the repo
- Commit without running `pngquant` on new screenshots
- Include private information about specific victims or internal agent references

---

## Security Rules

- **PUBLIC repo:** Every committed file is publicly visible
- Never commit unvetted files — VirusTotal analysis required first
- Never expose committee member emails, internal references, or private contacts
- Before adding any external script or CDN link: verify it's from a trusted source

---

## Override System

Create `AGENTS.override.md` for temporary task-specific rules. Delete when done. Template: `~/code/my-template/AGENTS.override.md`

---

## Canonical References

- `CLAUDE.md` — Agent roles, scope boundaries, and session rules
- `AGENTS.md` (this file) — Universal AI agent config
- `README.md` — Project overview, case studies, security checklist
- `CONTRIBUTING.md` — Case study submission process
- `SECURITY.md` — Security policy
