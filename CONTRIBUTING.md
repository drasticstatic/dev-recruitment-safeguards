# Contributing to Dev Recruitment Safeguards

Thank you for helping protect developers from recruitment scams. Every documented case makes the community safer.

## How to Contribute

### Submitting a New Case Study

1. **Analyze the material first** — run any file or URL through [VirusTotal](https://virustotal.com) and document:
   - File hash (SHA-256)
   - VT score (X / total engines)
   - Behavior tab findings — `/OpenAction`, `/JS`, dropped files, contacted domains
   - Your verdict and reasoning

2. **Redact personal information** — remove your name, email, phone, and any identifying details from screenshots or documents before submitting.

3. **Open a Pull Request or Issue** with:
   - The threat level (🔴 Critical / 🟠 High / 🟡 Medium)
   - The attack vector (Repo Trap / PDF Lure / Impersonation / Other)
   - The persona/platform used (LinkedIn / Email / Discord / etc.)
   - Any indicators of compromise (IoCs) — domains, hashes, wallet addresses

### Guidelines

- **Do not include live malware.** Vetted, defanged samples only — confirm 0-detection VT score before including any file.
- **Accuracy over speed.** If you're unsure about a detail, flag it as unconfirmed rather than guessing.
- **One case per PR** — keeps review focused and history clean.
- **Screenshots go in `screenshots/`** — use descriptive filenames (e.g., `case4-linkedin-dm-impersonation.png`).

### What Counts as a Case

- Unsolicited recruiter contact that led to a technical test, repo clone, or file download
- Professional-looking PDFs, spec documents, or "coding assignments" from unverified sources
- Brand impersonation targeting Web3 / DeFi / fullstack roles
- Any infostealer or RAT delivery via the recruitment pipeline

### Not Sure?

Open an Issue and describe what you received. The community can help assess whether it's worth documenting.

---

*This project is maintained under the MIT License. Contributions are licensed the same way.*
