# Graph Report - .  (2026-09-04)

## Corpus Check
- cluster-only mode — file stats not available

## Summary
- 28 nodes · 20 edges · 9 communities (4 shown, 5 thin omitted)
- Extraction: 95% EXTRACTED · 5% INFERRED · 0% AMBIGUOUS · INFERRED: 1 edges (avg confidence: 0.9)
- Token cost: 0 input · 0 output

## Graph Freshness
- Built from commit: `83b318d6`
- Run `git rev-parse HEAD` and compare to check if the graph is stale.
- Run `graphify update .` after code changes (no API cost).

## Community Hubs (Navigation)
- [[_COMMUNITY_Community 0|Community 0]]
- [[_COMMUNITY_Community 1|Community 1]]
- [[_COMMUNITY_Community 2|Community 2]]
- [[_COMMUNITY_Community 3|Community 3]]
- [[_COMMUNITY_Community 4|Community 4]]
- [[_COMMUNITY_Community 5|Community 5]]
- [[_COMMUNITY_Community 6|Community 6]]
- [[_COMMUNITY_Community 7|Community 7]]
- [[_COMMUNITY_Community 8|Community 8]]

## God Nodes (most connected - your core abstractions)
1. `Project Overview & Case Studies` - 5 edges
2. `Case #2 — The Lure (PDF + Code Task)` - 3 edges
3. `LinkedIn Web3 Recruiter Audits` - 2 edges
4. `Case #1 — The Repo Trap` - 2 edges
5. `Case #6 — The Weaponized Repo (RCE)` - 2 edges
6. `APOM-DAPP Project Description.pdf` - 2 edges
7. `Graphify Knowledge Graph` - 2 edges
8. `Dev Recruitment Safeguards Portal` - 1 edges
9. `AI Agent Configuration` - 1 edges
10. `Claude Code Session Rules` - 1 edges

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

## Communities (9 total, 5 thin omitted)

### Community 0 - "Community 0"
Cohesion: 0.29
Nodes (7): Case #1 — The Repo Trap, Case #3 — Brand Hijacking, Case #6 — The Weaponized Repo (RCE), Dev Recruitment Safeguards Portal, Daniel Perez Valdes, Jacinta Stewart, Project Overview & Case Studies

### Community 1 - "Community 1"
Cohesion: 0.29
Nodes (5): Commit Convention, External Dependency Audit, Graphify Knowledge Graph, Project Scope, Security Rules

### Community 2 - "Community 2"
Cohesion: 0.5
Nodes (4): APOM-DAPP Project Description.pdf, Case #2 — The Lure (PDF + Code Task), Josépha Russe, Security Policy

### Community 3 - "Community 3"
Cohesion: 0.67
Nodes (3): LinkedIn Web3 Recruiter Audits, BeaverTail Infostealer, InvisibleFerret RAT

## Knowledge Gaps
- **18 isolated node(s):** `Dev Recruitment Safeguards Portal`, `Contribution Guidelines`, `AI Agent Configuration`, `Claude Code Session Rules`, `Security Policy` (+13 more)
  These have ≤1 connection - possible missing edges or undocumented components.
- **5 thin communities (<3 nodes) omitted from report** — run `graphify query` to explore isolated nodes.

## Suggested Questions
_Questions this graph is uniquely positioned to answer:_

- **Why does `Project Overview & Case Studies` connect `Community 0` to `Community 2`?**
  _High betweenness centrality (0.105) - this node is a cross-community bridge._
- **Why does `Case #2 — The Lure (PDF + Code Task)` connect `Community 2` to `Community 0`?**
  _High betweenness centrality (0.066) - this node is a cross-community bridge._
- **What connects `Dev Recruitment Safeguards Portal`, `Contribution Guidelines`, `AI Agent Configuration` to the rest of the system?**
  _18 weakly-connected nodes found - possible documentation gaps or missing edges._