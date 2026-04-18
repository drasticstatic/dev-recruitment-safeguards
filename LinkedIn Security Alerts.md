# 🚨 LinkedIn Web3 Recruiter Audits

> **Heads up everyone** — sophisticated phishing campaigns are actively targeting developers on LinkedIn. Let's stay sharp and keep our dev environments clean! 🛡️💻

---

## 🪤 SECURITY ALERT #1 — The "Contagious Interview" Scam

**Persona:** "Jacinta Stewart" | **Repo:** `staufenbiel89/dtm`

### How It Works

The attack follows a predictable playbook:

1. **The "Pre-Hired" Hook** — They skip the technical screen entirely and tell you they're *"already confident in your contribution."*
2. **The "UI Review" Trap** — They ask you to clone a repo and *"review the UI workflow."*
3. **The Execution** — The goal is to get you to run `npm install` or `npm start`.

### ⚙️ The Technical Danger

These repos are **infection vectors**. Scammers hide malware in `package.json` using `preinstall` or `postinstall` scripts. The moment you run a command, the script executes a hidden payload that:

- 💸 Exfiltrates your **AWS/GCP/Azure credentials**
- 🔑 Steals your **SSH private keys** and `.env` files
- 🍪 Scrapes **browser cookies** to bypass your 2FA on other sites
- 💰 Steals **crypto wallet** browser extensions and local wallet files

### 🔍 What to Look For

- **Check `package.json`:** If you see obfuscated base64 strings or calls to unknown external URLs in the `scripts` section — delete the folder immediately
- **Mimicry repos:** The `dtm` repo mimics `dtm-labs/dtm` — a real Distributed Transaction Manager with 10,000+ stars — to appear legitimate
- **VSCode Auto-Run Trap:** These repos often include a hidden `.vscode/tasks.json` with `"runOn": "folderOpen"` — if you open the project in VSCode, a command can execute malicious scripts *immediately*, even before you run anything manually
- **Hidden payload vectors:** Look for files like `errorHandler.js` or `getCookie()` functions — often used as backdoors to fetch JavaScript from a command-and-control (C2) server

### 🛡️ Safe Practice

> Treat every "coding test" as **Untrusted Code**. Only run these in a disposable VM or a Docker container with **no access** to your host's environment variables or files.

### 📸 Evidence

![Jacinta Stewart initial DM](<screenshots/Screenshot 2026-04-13 at 12.06.39.png>)

I removed the `.git` folder to inspect the repo manually — the scammy feel was immediately obvious. I ran the URLs through VirusTotal and had Gemini analyze the repo structure.

**Key observation:** These "recruiters" are ALWAYS shown as "online/active" — as if they are bots. Their messages reflect it too: scripted, impersonal, high-pressure.

> **💡 Pro tip:** Always ask for a 15-min video call before any technical work. A large percentage of malicious actors won't show up. And don't be afraid to say you receive many scam messages and want reassurance — a real recruiter will *want* to put you at ease.

**Update:** The "Jacinta Stewart" profile was subsequently deactivated and the repo was reported to GitHub.

![Profile deactivated](<screenshots/Screenshot 2026-04-17 at 13.59.42.png>)

---

### 🧬 Malware Family: BeaverTail / InvisibleFerret

This is a known **"lure" repository** designed to deliver the **BeaverTail infostealer** or **InvisibleFerret RAT**:

- **Mimicry:** The name `dtm` mimics `dtm-labs/dtm` (10k+ stars) or `blei-lab/dtm` (dynamic topic models) — both legitimate, popular projects
- **VSCode Auto-Run:** Hidden `.vscode/tasks.json` with `runOn: folderOpen` executes before you touch a single file
- **Hidden payload vectors:** `errorHandler.js` and `getCookie()` functions act as backdoors to fetch code from C2 servers

#### What the malware steals:
| Category | Targets |
|---|---|
| 🌐 Browser Data | Cookies, saved passwords (2FA bypass) |
| 🔑 Developer Keys | `.env` files, AWS/GCP/Azure access keys, SSH private keys |
| 💰 Crypto Wallets | Browser extensions, local wallet files |

---

## 🎣 SECURITY ALERT #2 — Professional PDF & "Job Offer" Code Test Scam

**Persona:** "Josépha Russe"

### The Evidence

**Official confirmation this was fraudulent:**

![Fraudulent assignment confirmed](<screenshots/Screenshot 2026-04-18 at 12.30.53.png>)

*"The coding assignment you received was fraudulent — please do not run it"*

![Evidence 1](<screenshots/Screenshot 2026-04-18 at 12.37.49.png>)
![Evidence 2](<screenshots/Screenshot 2026-04-18 at 12.37.56.png>)
![Initial outreach 1](<screenshots/Screenshot 2026-04-13 at 09.29.13.png>)
![Initial outreach 2](<screenshots/Screenshot 2026-04-13 at 09.29.29.png>)
![Additional evidence](<screenshots/Screenshot 2026-04-18 at 12.38.45.png>)

> **Note:** I didn't think about this at the time, but I did open the PDF. Gemini confirmed it's possible for malicious code (scripts) to be embedded in a downloaded PDF.

I'm sharing the attached PDF (APOM-DAPP) as a **cautionary example**. This specific file has been vetted and is safe to view for educational purposes — but it represents the exact type of "lure" scammers use to target tech students and developers.

---

### ⚠️ Why "Professional" Documents Can Be Dangerous

A PDF isn't just a digital piece of paper — **it's a container for code.** Scammers use highly detailed documents like this one to build trust before launching an attack:

#### The Attack Vectors:
- **Hidden Scripts:** PDFs support JavaScript. Malicious files can trigger a download the moment they are opened (`/OpenAction`) to install keyloggers or ransomware — before you've read a single word
- **The "Technical Test" Trap:** In our field, these proposals often lead to a "hiring task" where you're asked to run a GitHub repo or "test" a DApp. That code is often designed to drain your crypto wallet or steal your browser cookies

---

### ✅ Vet Checklist (PDF Edition)

Before opening **any** unsolicited attachment from a recruiter or "founder":

- [ ] **Scan the File:** Upload to [VirusTotal.com](https://virustotal.com). Look for `OpenAction` or `JavaScript` flags in the **Behavior tab**
- [ ] **Check the Sender-to-Role Ratio:** Does a "CEO" of a major project have only 50 connections and no post history? The account is likely a bot or hijacked profile
- [ ] **Verify the Domain:** Does the recruiter's email or project website end in a suspicious TLD (e.g., `.xyz-jobs.com` instead of `.com`)?
- [ ] **Cross-Reference:** Search the company name on Google and LinkedIn separately. If the project *only* exists in the PDF they sent — it's a scam
- [ ] **Use a Sandbox:** Open it in a browser preview (Google Drive) rather than downloading directly to your OS

---

### 🧪 APOM-DAPP PDF — VirusTotal Analysis

**This PDF is a perfect template for a scam:** it uses professional terminology (DeFi, EVM, Smart Contracts) and a 12-18 month roadmap to look legitimate. Use this file to learn how these "pitches" are structured so you can spot the fake ones in your inbox.

#### Deep Dive Analysis

Even though flagged as "Safe" (0/70 detections), the behavior logs show what happens when this PDF is opened in a standard Adobe Acrobat environment:

**Contacted Domains & IPs:**
- `acroipm2.adobe.com` and `a1672.dscr.akamai.net`
- **Verdict:** ✅ Legitimate — Adobe Acrobat pings these for "In-Product Messaging" (IPM), updates, and certificate checks. Standard behavior.
- `8.8.8.8` (Google DNS) — standard DNS resolution for the above Adobe domains

**Dropped Files:**
- Several files created (a `.zip` + alphanumeric file strings)
- **Verdict:** ✅ Standard PDF reader cache and temporary files. None were flagged as malicious by VirusTotal's subsidiary scans.

**Conclusion:**
> ✅ VT Result: 0/70 (No security vendors flagged this hash)
> ✅ Behavior Log: Only traffic to Adobe.com for standard license/update checks
> ✅ Dropped Files: Temporary system cache, not hidden executables
>
> **This specific PDF is safe** — but always check these three areas (Domains, Dropped Files, and Scripts) before trusting any document from a stranger.

---

### 🔍 What to Look for in Your Sandbox Reports

Even if the main VirusTotal page is green, the **Behavior and Sandbox tabs** often tell a different story:

| Check | 🚩 Suspicious | ✅ Normal |
|---|---|---|
| **Network DNS/IP** | Connections to `pastebin.com`, `discord.com`, or random IPs | Known vendor domains (Adobe, Google) |
| **Dropped Files** | `.tmp`, `.exe`, `.dll` in temp folders | PDF reader cache files only |
| **Shell Commands** | Any `cmd.exe` or `powershell.exe` execution | None |
| **PDF Flags** | `/JS` or `/OpenAction` in a simple text doc | Absent |

> 💡 **"A 'Clean' score on the main screen just means the file isn't in a database of known threats yet. The real story is in the Behavior tab."**

---

### 🍎 Apple Preview vs. Adobe Acrobat

**Apple Preview is significantly safer for viewing untrusted PDFs** because it lacks support for the complex features hackers exploit most:

| Feature | Apple Preview | Adobe Acrobat |
|---|---|---|
| JavaScript support | ❌ None | ✅ Full engine |
| /OpenAction execution | ❌ Blocked | ✅ Runs automatically |
| Attack surface | 🟢 Minimal | 🔴 Large |
| Sandboxing | ✅ macOS sandbox | Partial |
| Targeting frequency | 🟢 Low | 🔴 High (global standard) |

**When Adobe Reader is still necessary:**
- Complex government/corporate forms with digital signature requirements
- Dynamic portfolios with embedded file structures or server-generated content

For everything else — **use Apple Preview**.

---

## 🎭 SECURITY ALERT #3 — Brand Impersonation (Kuru Labs / Monad)

### The Outreach (Email)

```
Hi Christopher,

Came across your work — really liked your fullstack experience, especially in Web3/DeFi.

We're building a DeFi startup focused on trading infrastructure (AMM, aggregation,
perps, and AI-driven strategies). We've raised early-stage funding and are building
across EVM chains (Ethereum, Arbitrum, Base) and Monad, with a focus on deep
liquidity and cross-chain execution.

We're hiring a Fullstack Developer (remote, full-time).
Comp: $180k–$220k + token upside

Role is hands-on across:
  Frontend: trading UI
  Backend: execution systems, APIs

Small team, fast execution, high ownership.

— Zam Villalon, Talent Acquisition Team
  www.kurulabs.org  |  Genusix Labs  |  +1 (929) 233-9909
  📍 3826 O Ogilvie Ct, Woodbridge, Virginia 22192, US
```

### The LinkedIn DM (Near-Identical Template)

From **Sujon Pramanik** (3rd-degree connection, "Chief Growth at Kuru Labs | Blockchain Fund Ventures"):

> *"Hi Christopher, Came across your work — really liked your fullstack experience, especially in Web3/DeFi. We're building a DeFi startup focused on trading infrastructure..."*

**Observation:** I received nearly identical messages from two different people on two different platforms within the same 24-hour window.

---

### 🚩 Critical Red Flags — Analysis by Gemini

> While **Kuru Labs is a legitimate DEX project on Monad**, it is highly likely that "Zam Villalon" and "Sujon Pramanik" are impersonators.

| 🚩 Red Flag | Detail |
|---|---|
| **Shell Company** | "Genusix Labs" address at 3826 O Ogilvie Ct, Woodbridge, VA — shared with **medical diagnostic centers**, not a known Web3/tech hub |
| **Identical Scripts** | Near-identical messages sent via email + LinkedIn from two different "people" — copy-paste template at scale |
| **Speed & Salary FOMO** | $180k–$220k + tokens for a "quick 30-min chat" — designed to create urgency and lower defensive guard |
| **"Book HR First" Pressure** | Immediate redirect to external Calendly before any identity verification |
| **The Lure Repo Setup** | These "intro chats" pivot quickly to a "UI review" or "technical test" — the exact playbook for BeaverTail/InvisibleFerret delivery |

---

### 🔎 Real vs. Potential Impersonator

| | ✅ Real Kuru Labs | 🚩 Impersonator |
|---|---|---|
| **Official Presence** | Active on Monad, backed by verified seed funding | "Genusix Labs" shell company |
| **Recruitment** | Via official channels or verified founders | DMs from 3rd-degree connections + cold email |
| **Next Steps** | Standard technical interviews | High pressure to "book HR first" via external links |
| **Domain** | Official verified domain | `kurulabs.org` + `genusix.com` |

---

### 🛡️ Recommended Actions

1. **Stop Local Execution:** Do not clone any repo they send or run `npm install`
2. **Verify via Official Channels:** Go to the official Kuru Labs Twitter/X or Discord and ask if "Zam Villalon" or "Genusix Labs" are authorized hiring partners
3. **Check Recent Activity:** Look at Sujon Pramanik's LinkedIn activity — 500+ connections but zero original posts or engagement in the last year = likely hijacked account
4. **Sandbox the Interview:** If you proceed with the "tech interview," use a dedicated VM or GitHub Codespaces — **no access to your local `.env` files or SSH keys**

---

## 💡 General Tips — Applicable to All Cases

- **Always ask for a video call** before cloning anything. Real recruiters want to put you at ease. Bots and scam ops will ghost or cite camera problems.
- **"Always online" profiles** with scripted, impersonal messages are a bot signal.
- **The Scripted Opener:** It almost always starts with a vague but urgent compliment: *"I saw your profile and your background in [X] is exactly what our stealth startup needs."*
- **The Vibe Shift:** If someone who normally posts about UI/UX design suddenly DMs you about a "Decentralized High-Yield Gaming Project" — the account has likely been compromised.
- **Silence on Other Channels:** If you suspect a profile is hijacked, message them on another platform. Scammers rarely have access to all of a victim's accounts simultaneously.

---

*All materials documented here are for educational and security-awareness purposes. Examples were vetted and sanitized before publication.*
