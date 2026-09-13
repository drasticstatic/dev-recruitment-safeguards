# AGENTS.md
> AI Agent Configuration — dev-recruitment-safeguards
> Read by: Claude Code, Cursor, GitHub Copilot, and other AI coding assistants.
> See `CLAUDE.md` for Claude Code–specific rules.

---

## ⚠ FIRST: sync this clone before you touch anything

```sh
git pull --rebase --autostash
```

Run this at the **start of every session**, before reading deeply or editing. Several agents and
Christopher push to these repos — including Cosmos agents that run unattended while nobody is at the
machine — so a clone can be behind by the time you open it.

**`--autostash` is what makes this safe on a dirty tree.** It stashes uncommitted changes, rebases
onto the remote, then reapplies them. Your in-progress work survives. Without it, `git pull --rebase`
refuses to run and you are tempted into something worse.

Why it matters more than it sounds:

- A stale clone **does not fail early.** It fails at push time, after the work is done, as a
  non-fast-forward rejection — the most expensive moment to discover it.
- The tempting fix at that point is `git push --force`, which discards whatever someone else pushed
  in the meantime. Syncing first removes the temptation.
- If a rebase does conflict, stop and resolve it deliberately. A conflict is information: someone
  else changed the same lines, and you want to know that *before* building on top of them.

**Fresh clone?** Also run `sh scripts/install-hooks.sh` — git hooks are not version-controlled, so
the commit-attribution hook stays inert until this clone is pointed at `.githooks/`. Details:
[`scripts/README.md`](./scripts/README.md).

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

## Commit attribution (enforced by hook)

Every commit must carry two git trailers:

```
Co-Authored-By: <Agent> · <Engine> · <Provider> [<Model>]                  # direct
Co-Authored-By: <Agent> · <Engine> · <Gateway> · <Provider> [<Model>]      # proxied
<Platform>-Session: <full session URL>
```

Model in **square brackets**, separator is U+00B7 MIDDLE DOT ( · ). Add `<Gateway>` **only when
inference is proxied** — it names what *routed* the request (`NVIDIA NIM`, `OpenRouter`), never who
made the model (`Z.ai`, `Moonshot AI`, `MiniMaxAI`). The field order mirrors the `/model` selector
string, so `anthropic/nvidia_nim/z-ai/glm4.7` transcribes to `NVIDIA NIM · Z.ai [GLM-4.7]` —
read it left to right rather than memorising it. Local runtimes (`Ollama`, `llama.cpp`,
`LM Studio`) have no gateway: the weights ran on your machine, so the runtime is the Provider. The session
trailer is a **separate** line — folding it onto the `Co-Authored-By:` line breaks git trailer
parsing. Use the full session URL, never a truncated prefix. Key varies by platform:
`Claude-Session:` for Claude Code CLI, `Cosmos-Session:` for Cosmos.

`.githooks/commit-msg` rejects non-conforming commits. **Activate it once per clone:**

```sh
sh scripts/install-hooks.sh
```

Human-only commits: `git commit --no-verify`. **Canonical spec — single source of truth. Do not restate the field table locally; link it:**
[`my-template/AGENT-SYNC/README.md`](https://github.com/drasticstatic/my-template/blob/main/AGENT-SYNC/README.md)
