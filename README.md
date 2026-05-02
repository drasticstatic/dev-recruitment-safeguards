# 🛡️ Dev Recruitment Safeguards

> **A living database of high-fidelity recruitment scams targeting Web3 and fullstack developers.**

[![VirusTotal — APOM-DAPP PDF](https://img.shields.io/badge/VirusTotal%20APOM--DAPP%20PDF-0%2F72%20engines-brightgreen?style=flat-square&logo=virustotal&logoColor=white)](https://www.virustotal.com/gui/file/a4c04694e8e703f30e64423d60148de58d7f6f9829f356f40acf9596b4442b57)
[![Portal Live](https://img.shields.io/badge/portal-live-0a7bff?style=flat-square&logo=githubpages&logoColor=white)](https://drasticstatic.github.io/dev-recruitment-safeguards)
[![Cases Documented](https://img.shields.io/badge/cases_documented-3-critical?style=flat-square&logo=databricks&logoColor=white)](https://github.com/drasticstatic/dev-recruitment-safeguards#-documented-case-studies)
[![Contributions Welcome](https://img.shields.io/badge/contributions-welcome-orange?style=flat-square&logo=github&logoColor=white)](https://github.com/drasticstatic/dev-recruitment-safeguards/blob/main/CONTRIBUTING.md)
[![License: MIT](https://img.shields.io/badge/license-MIT-lightgrey?style=flat-square)](LICENSE)
[![Security Policy](https://img.shields.io/badge/security_policy-active-blueviolet?style=flat-square&logo=shieldsdotio&logoColor=white)](SECURITY.md)

In the current job market, scammers are deploying sophisticated **"long-con" tactics** — professional 15-page PDFs, fake company identities, shell corporations, and hijacked LinkedIn profiles — to deliver infostealers and Remote Access Trojans (RATs). This project documents real-world examples with full technical analysis to help developers stay safe.

## 🚀 Live Portal

**[dev-recruitment-safeguards.github.io](https://drasticstatic.github.io/dev-recruitment-safeguards)** ← GitHub Pages

---

## 🔍 Documented Case Studies

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
├── index.html              ← GitHub Pages portal
├── screenshots/            ← Evidence screenshots (used in portal)
├── APOM-DAPP ?.pdf         ← Vetted sample lure PDF (educational)
├── LinkedIn Security Alerts.md  ← Raw incident documentation
└── README.md
```

---

**⚠️ Disclaimer:** *The materials in this repository are for educational and security-awareness purposes only. All examples were vetted and sanitized before inclusion. Screenshots are used under fair use for educational reporting.*
