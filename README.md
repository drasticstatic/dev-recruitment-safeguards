# 🛡️ Dev Recruitment Safeguards

> **A living database of high-fidelity recruitment scams targeting Web3 and fullstack developers.**

[![VirusTotal — APOM-DAPP PDF](https://img.shields.io/badge/VirusTotal%20APOM--DAPP%20PDF-0%2F72%20engines-brightgreen?style=flat-square&logo=virustotal&logoColor=white)](https://www.virustotal.com/gui/file/a4c04694e8e703f30e64423d60148de58d7f6f9829f356f40acf9596b4442b57)
[![Portal Live](https://img.shields.io/badge/portal-live-0a7bff?style=flat-square&logo=githubpages&logoColor=white)](https://drasticstatic.github.io/dev-recruitment-safeguards)
[![Cases Documented](https://img.shields.io/badge/cases_documented-8-critical?style=flat-square&logo=databricks&logoColor=white)](https://github.com/drasticstatic/dev-recruitment-safeguards#-documented-case-studies)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-orange?style=flat-square&logo=github&logoColor=white)](https://github.com/drasticstatic/dev-recruitment-safeguards/blob/main/CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)](LICENSE)
[![Security Policy](https://img.shields.io/badge/security_policy-active-blueviolet?style=flat-square&logo=shieldsdotio&logoColor=white)](SECURITY.md)
[![Pages](https://github.com/drasticstatic/dev-recruitment-safeguards/actions/workflows/pages/pages-build-deployment/badge.svg)](https://github.com/drasticstatic/dev-recruitment-safeguards/actions/workflows/pages/pages-build-deployment)

In the current job market, scammers are deploying sophisticated **"long-con" tactics** — professional 15-page PDFs, fake company identities, shell corporations, hijacked/aged LinkedIn profiles, and confirmed remote-code-execution backdoors disguised as job-application take-home tests — to deliver infostealers, RATs, and crypto-wallet drainers. This project documents real-world examples with full technical analysis, sourced evidence chains, and reproducible verification steps to help developers stay safe.

## 🚀 Live Portal

**[dev-recruitment-safeguards.github.io](https://drasticstatic.github.io/dev-recruitment-safeguards)** ← GitHub Pages

---

## 🔍 Documented Case Studies

> **8 cases** — 6 fully confirmed, 1 under active investigation, 1 illustrative/hypothetical. Full technical deep-dives, evidence screenshots, and source-code walkthroughs live on the [portal](https://drasticstatic.github.io/dev-recruitment-safeguards) — this README covers the summary. Click any case on the portal for the full modal writeup.

### 🪤 Case #1 — The Repo Trap
| Field | Detail |
|---|---|
| **Threat Level** | 🔴 Critical |
| **Persona** | "Jacinta Stewart" (hijacked LinkedIn profile) |
| **Vector** | Malicious `npm preinstall` scripts in a cloned GitHub repo |
| **Payload** | BeaverTail infostealer / InvisibleFerret RAT |
| **Mimics** | `dtm-labs/dtm` (legitimate ★10k+ project) |
| **Steals** | AWS/GCP keys, SSH private keys, `.env` files, browser cookies, crypto wallets |

**How it works:** The "recruiter" skips technical screening and asks you to clone a repo and "review the UI workflow." The moment you run `npm install`, a hidden `preinstall` hook executes an obfuscated payload. The repo also includes a `.vscode/tasks.json` with `runOn: folderOpen` — meaning just *opening* the folder in VSCode can trigger the attack.

---

### 🎣 Case #2 — The Lure (PDF + Code Task)
| Field | Detail |
|---|---|
| **Threat Level** | 🟠 High |
| **Persona** | "Josépha Russe" |
| **Vector** | 12-page professional DeFi spec PDF → secondary malicious coding task |
| **PDF Risk** | `/OpenAction` JavaScript triggers on file open |
| **VT Score** | 0/70 (unknown ≠ safe — always check the **Behavior tab**) |
| **Confirmed** | *"The coding assignment you received was fraudulent — please do not run it"* |

**How it works:** A polished, 12-18 month DeFi roadmap PDF (complete with EVM architecture, tokenomics, and AMM design) is sent to build trust. After you're invested, a follow-up "coding task" arrives — which is the same Repo Trap playbook delivered to an already-trusting target. The PDF itself may also contain `/OpenAction` scripts that execute on open in Adobe Acrobat.

---

### 🎭 Case #3 — The Impersonation (Brand Hijacking)
| Field | Detail |
|---|---|
| **Threat Level** | 🟣 High |
| **Personas** | "Zam Villalon" (email) + "Sujon Pramanik" (LinkedIn) |
| **Impersonates** | Kuru Labs (legitimate DEX on Monad — real funded project) |
| **Shell Company** | Genusix Labs (Woodbridge, VA — address shared with medical offices) |
| **Pattern** | Identical scripted DMs sent simultaneously via email + LinkedIn |
| **FOMO Bait** | $180k–$220k + token upside for a "quick 30-min chat" |

**How it works:** Two personas from the same fake org contact you on different platforms using the exact same copy-paste template, borrowing the brand equity of a legitimate Web3 project. Pressure to "book HR first" via an external Calendly link bypasses normal verification. The next step is the Repo Trap.

---

### 🔗 Case #4 — The Wrapped Link
| Field | Detail |
|---|---|
| **Threat Level** | 🟠 High |
| **Persona** | "Daniel Perez Valdes" |
| **Vector** | LinkedIn redirect wrapper (`linkedin.com/safety/go?url=...`) hiding the real destination of a Google Doc lure |
| **VT Flag** | "Phishing Attachment IOC" — but attached to `linkedin.com` itself, a stale 2-year-old entry VirusTotal's own classification calls "legitimate" |
| **Real Risk** | Not the doc load itself — links clicked *inside* it, or an OAuth "connect this app" prompt |

**How it works:** A high-reputation wrapper domain (LinkedIn, Google) tells you nothing about the content it's wrapping. This case is a walkthrough of how to correctly read a VirusTotal IOC flag instead of panicking at the first red badge — and how the entry point to this developer's outreach led directly to Case #6.

---

### 🪤 Case #5 — The Typosquat *(illustrative, not a documented incident)*
| Field | Detail |
|---|---|
| **Threat Level** | 🧪 Hypothetical teaching example |
| **Vector** | Typosquatted npm package (`web3-react-modall` vs. `web3-react-modal`) |
| **Payload** | `postinstall` hook wraps `window.ethereum.send()`, silently rewrites the transaction recipient |
| **Key Insight** | Attacks #1–4 need a recruiter. This one doesn't — the most dangerous scams need the least social engineering |

**How it works:** A teaching scenario illustrating a real class of npm supply-chain risk, distinct from the other reported incidents on this page. Clearly labeled as hypothetical — no real persona, no documented victim.

---

### 💣 Case #6 — The Weaponized Repo (Flagship — Confirmed RCE)
| Field | Detail |
|---|---|
| **Threat Level** | 🔴 Critical — Confirmed Remote Code Execution |
| **Persona** | "Daniel Perez Valdes" — mutual connection with a trusted instructor |
| **Repo** | `nitroe1/TokenPromotingDapp` |
| **Backdoor** | `frontController.js: verifyToken()` — fetches and `eval`s attacker-controlled code from a private Google Doc, on `npm start` |
| **Also** | A real front-running/sniper bot underneath, requiring a live wallet private key from environment |
| **Provenance** | 194 commits backdated 3 months before the repo/org existed; a real Uniswap developer's identity (Eric Zhong) forged onto the fake history; underlying code traced to a separate, unrelated victim company (Cowchain/CoinProperty) via a license mismatch |

**How it works:** A fully sourced forensic investigation — GitHub API timestamps, commit-signature verification data, and direct source-code review, not inference. `verifyToken()` fires unconditionally at module load: it fetches a private Google Doc, base64-decodes it, and runs `new Function('axios','require', code)(axios, require)` — a direct remote-code-execution backdoor the attacker can repoint at any time without touching the repo again. Verdict: **DO NOT FORK, DO NOT RUN.** Full evidence chain, code walkthrough, and the license/provenance trail live on the portal.

---

### 🎭 Case #7 — The Real Project, Fake Recruiter *(investigation pending)*
| Field | Detail |
|---|---|
| **Threat Level** | 🔵 Investigating |
| **Persona** | "Joe Gump Linda Gump" |
| **Impersonates** | Ritual / Infernet — confirmed real, funded AI/Web3 project |
| **Red Flag** | Double-first/double-last-name profile — a known signature of merged, purchased, or repurposed accounts |

**How it works:** Same playbook as Case #3 — borrow a real, verifiable project's name for instant credibility, then pitch via an unsolicited Google Doc. Marked pending because the outcome isn't resolved yet; will be updated (not deleted) once it is.

---

### ⏱️ Case #8 — The Pre-Hired Take-Home
| Field | Detail |
|---|---|
| **Threat Level** | 🔴 Critical |
| **Persona** | "Justin Miller" |
| **Pitch** | Blockchain real-estate platform, $80–$120/hr, fully remote |
| **Pattern** | "Strong match" verdict with zero technical screen → immediate 24-hour take-home pressure — near-identical to Case #1's playbook |

**How it works:** A real-time transcript documenting the classic pre-hired-framing-to-take-home-pressure pipeline, including a shared mutual connection that did **not** clear the account as safe — a mutual connection is a social-proof signal, not identity verification.

---

### 🔓 Cross-Case Analysis — How These Profiles Get This Convincing
Covering Cases #4, #7, and #8: LinkedIn profile metadata on all three personas (join dates 2008–2012, two with genuine LinkedIn verification badges on file) points to **aged-account takeover, not fabrication**. A verification badge is a point-in-time snapshot, not a live guarantee — and the real, decade-plus-old mutual-connection networks riding these compromised accounts are exactly what makes them pass every "is this fake?" gut-check. Full breakdown on the portal.

---

## 🛡️ Quick Security Checklist

Before responding to **any** unsolicited recruiter message:

- [ ] 🔍 **Scan First:** Upload files/URLs to [VirusTotal.com](https://virustotal.com) and check the **Behavior tab** for `/OpenAction` or `/JS` flags
- [ ] 🕵️ **Verify Identity:** Check the LinkedIn "Activity" tab — dormant accounts with sudden DMs = major red flag
- [ ] 📦 **Sandbox Everything:** Use **Apple Preview** (no JS support) for PDFs; **Docker/VMs** for technical tests
- [ ] 📞 **Demand a Video Call:** Ask for a 15-min video before cloning anything — most malicious actors won't show
- [ ] 📄 **Audit package.json:** Look for obfuscated base64 strings or external URL calls in `preinstall`/`postinstall`
- [ ] 🔗 **Verify the Domain:** Confirm the recruiter's email domain matches the company's official channels
- [ ] 🔁 **Cross-Reference:** If the company only exists in a PDF they sent — it's a scam
- [ ] 🛡️ **Confirm via Official Channels:** Ask in the company's Discord/Twitter if the recruiter is a verified partner
- [ ] 💣 **Read Before You Run:** Never `npm install`/`npm start` an unaudited take-home repo with real credentials present — `gh api` timestamp/signature data reveals forged commit history a rendered GitHub page hides (see Case #6)
- [ ] 🔓 **A Badge Isn't Proof of Today:** LinkedIn verification is a point-in-time snapshot, not a live guarantee — an old, verified account can still be a live takeover (see Cross-Case Analysis)

> ⚠️ **Remember:** A "0/70" VirusTotal score means *unknown*, not safe. The real story is in the **Behavior tab**.

---

## 🧪 VirusTotal Analysis — APOM-DAPP PDF

The sample PDF included in this repo was fully vetted via VirusTotal before inclusion:

- **Hash:** `a4c04694e8e703f30e64423d60148de58d7f6f9829f356f40acf9596b4442b57`
- **Score:** 0/72 (no detections)
- **Contacted domains:** `acroipm2.adobe.com`, `a1672.dscr.akamai.net` (both legitimate Adobe/Akamai)
- **Dropped files:** 13 temporary cache files — no `.exe`, `.dll`, or `.ps1`
- **Verdict:** ✅ Safe for educational use

This specific file is safe — it's included so you can see what a professional scam "lure" looks like and learn how to read a VirusTotal Behavior report.

---

## 🛠️ How to Contribute

Received a suspicious "technical test" or professional-looking spec doc?

1. **Analyze:** Run the file/URL through [VirusTotal](https://virustotal.com) and check the **Behavior** tab
2. **Document:** Take screenshots, redact your personal info
3. **Submit:** Open an Issue or Pull Request with the details

---

## 📁 Repo Structure

```
dev-recruitment-safeguards/
├── index.html                                    ← GitHub Pages portal (8 cases + cross-case analysis)
├── screenshots/                                   ← Evidence screenshots (used in portal)
├── APOM-DAPP Project Description.pdf              ← Vetted sample lure PDF (educational)
├── APOM-DAPP Project Description_VirusTotal-ThreatGraph-Export.json
├── LinkedIn Security Alerts.md                    ← Raw incident documentation
├── AGENTS.md / CLAUDE.md                          ← AI agent config for contributors using AI tooling
├── CONTRIBUTING.md
├── SECURITY.md
├── LICENSE
└── README.md
```

---

**⚠️ Disclaimer:** *The materials in this repository are for educational and security-awareness purposes only. All examples were vetted and sanitized before inclusion. Screenshots are used under fair use for educational reporting.*
