# Security Policy

## About This Repository

This repository documents recruitment scams and contains **vetted, defanged sample materials** for educational purposes. All files were analyzed and confirmed safe before inclusion. This policy covers the repository itself — not the threat actors documented within it.

## Included Materials — Safety Status

| File | VT Score | Verdict |
|------|----------|---------|
| `APOM-DAPP ? Project Description.pdf` | 0/72 engines | ✅ Safe — educational lure sample |
| `APOM-DAPP ?...ThreatGraph-Export.json` | N/A — metadata only | ✅ Safe — VirusTotal export data |

All included files:
- Were scanned via VirusTotal (72+ engines) with zero detections
- Had their Behavior tab reviewed for `/OpenAction`, `/JS`, dropped files, and network calls
- Were confirmed safe by the maintainer before committing

**The PDF is safe to open in Apple Preview.** Do not open it in Adobe Acrobat without understanding the `/OpenAction` JavaScript risk — see the analysis section in README.md for details.

## Reporting a Problem

### Found a security issue with this repository itself?

If you discover that a file in this repo is actually malicious, a link is broken and redirects to a harmful site, or there's any concern about the safety of included materials:

1. **Do not open a public Issue** — open a private discussion or email the maintainer directly.
2. Include the file name, hash, VirusTotal link, and your specific concern.
3. A response will be provided within 48 hours.

### Found a new recruitment scam to report?

That's a contribution, not a security report — see [CONTRIBUTING.md](CONTRIBUTING.md).

## Safe Handling Reminder

Even "safe" files from this repository exist because they were used in real attacks. Best practices:

- Open PDFs in **Apple Preview** (no JavaScript engine) or a sandboxed viewer
- Do not run any code samples in this repo on a non-isolated machine
- Treat all documented links and domains as potentially active threat infrastructure — do not visit them without a VPN and isolated browser profile

---

*Maintained by [drasticstatic](https://github.com/drasticstatic)*
