# Graph Report - .  (2026-09-02)

## Corpus Check
- cluster-only mode — file stats not available

## Summary
- 17 nodes · 13 edges · 6 communities (3 shown, 3 thin omitted)
- Extraction: 92% EXTRACTED · 8% INFERRED · 0% AMBIGUOUS · INFERRED: 1 edges (avg confidence: 0.9)
- Token cost: 0 input · 0 output

## Graph Freshness
- Built from commit: `2f2202db`
- Run `git rev-parse HEAD` and compare to check if the graph is stale.
- Run `graphify update .` after code changes (no API cost).

## Community Hubs (Navigation)
- [[_COMMUNITY_Community 0|Community 0]]
- [[_COMMUNITY_Community 1|Community 1]]
- [[_COMMUNITY_Community 2|Community 2]]
- [[_COMMUNITY_Community 3|Community 3]]
- [[_COMMUNITY_Community 4|Community 4]]
- [[_COMMUNITY_Community 5|Community 5]]

## God Nodes (most connected - your core abstractions)
1. `Project Overview & Case Studies` - 5 edges
2. `Case #2 — The Lure (PDF + Code Task)` - 3 edges
3. `LinkedIn Web3 Recruiter Audits` - 2 edges
4. `Case #1 — The Repo Trap` - 2 edges
5. `Case #6 — The Weaponized Repo (RCE)` - 2 edges
6. `APOM-DAPP Project Description.pdf` - 2 edges
7. `Dev Recruitment Safeguards Portal` - 1 edges
8. `AI Agent Configuration` - 1 edges
9. `Claude Code Session Rules` - 1 edges
10. `Security Policy` - 1 edges

## Surprising Connections (you probably didn't know these)
- `Dev Recruitment Safeguards Portal` --references--> `Project Overview & Case Studies`  [INFERRED]
  index.html → README.md
- `Security Policy` --references--> `APOM-DAPP Project Description.pdf`  [EXTRACTED]
  SECURITY.md → APOM-DAPP ? Project Description.pdf
- `Case #2 — The Lure (PDF + Code Task)` --references--> `APOM-DAPP Project Description.pdf`  [EXTRACTED]
  README.md → APOM-DAPP ? Project Description.pdf
- `Claude Code Session Rules` --references--> `AI Agent Configuration`  [EXTRACTED]
  CLAUDE.md → AGENTS.md
- `Case #1 — The Repo Trap` --references--> `Jacinta Stewart`  [EXTRACTED]
  README.md → LinkedIn Security Alerts.md

## Communities (6 total, 3 thin omitted)

### Community 0 - "Community 0"
Cohesion: 0.4
Nodes (5): Case #1 — The Repo Trap, Case #3 — Brand Hijacking, Dev Recruitment Safeguards Portal, Jacinta Stewart, Project Overview & Case Studies

### Community 1 - "Community 1"
Cohesion: 0.5
Nodes (4): APOM-DAPP Project Description.pdf, Case #2 — The Lure (PDF + Code Task), Josépha Russe, Security Policy

### Community 2 - "Community 2"
Cohesion: 0.67
Nodes (3): LinkedIn Web3 Recruiter Audits, BeaverTail Infostealer, InvisibleFerret RAT

## Knowledge Gaps
- **11 isolated node(s):** `Dev Recruitment Safeguards Portal`, `Contribution Guidelines`, `AI Agent Configuration`, `Claude Code Session Rules`, `Security Policy` (+6 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **3 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Project Overview & Case Studies` connect `Community 0` to `Community 1`, `Community 4`?**
  _High betweenness centrality (0.308) - this node is a cross-community bridge._
- **Why does `Case #2 — The Lure (PDF + Code Task)` connect `Community 1` to `Community 0`?**
  _High betweenness centrality (0.192) - this node is a cross-community bridge._
- **What connects `Dev Recruitment Safeguards Portal`, `Contribution Guidelines`, `AI Agent Configuration` to the rest of the system?**
  _11 weakly-connected nodes found - possible documentation gaps or missing edges._