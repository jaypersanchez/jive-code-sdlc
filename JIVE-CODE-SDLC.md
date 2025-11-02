
---

# `JIVE-CODE-SDLC.md`

```markdown
# Jive-Code SDLC — Logic-First Development Framework

> **Motto:** No logic, no merge.  
> **Goal:** Make software explainable, modular, and teachable by forcing logic and architecture to lead the code.

---

## 1) Philosophy
1. **No Code Without Logic** — Every unit of work begins with a Logic Note and a diagram.
2. **Trace Everything** — Commits, tests, and PRs map to logic node IDs (e.g., `L-013`).
3. **Teach Through Artifacts** — Seniors encode their mental model in templates/examples.
4. **Composition > Configuration** — Clear module boundaries beat magical config.
5. **Small, Observable Steps** — Every change should be demo-able or measurable.

**Roles (lightweight):**
- **Solution Architect (SA):** value, scope, product fit.
- **Technical Architect (TA):** boundaries, runtime view, NFRs.
- **Data Architect (DA):** schemas, contracts, lineage, privacy/security.
- **Lead Dev / Devs / Reviewers:** implement and verify logic alignment.

> On small teams, one person can wear multiple hats—**keep the artifacts, not the ceremony**.

---

## 2) Lifecycle (phase gates)

### 0) Intake → **Intent Brief**
**Artifact:** `/architecture/intent.md`
- Problem statement, user story, success metric(s)
- Constraints & assumptions
- Out-of-scope

### 1) Solution Architecture → **Capability Sketch**
**Artifacts:** `/architecture/sa/overview.md`, `/architecture/sa/context-diagram.mmd`
- Context diagram (Mermaid/PlantUML)
- Capabilities impacted, cross-team touch points
- Risks & unknowns

### 2) Technical Architecture → **Interface Contracts**
**Artifacts:** `/architecture/ta/runtime.mmd`, `/architecture/ta/interfaces.yml`
- Runtime view (services, modules, data flow)
- API/spec contracts (requests/responses, error model)
- Non-functional requirements (latency, throughput, availability, cost)

### 3) Data Architecture (if applicable) → **Data Contracts**
**Artifacts:** `/architecture/da/schemas.sql|yaml`, `/architecture/da/lineage.mmd`
- Schema changes, versioning, migration plan
- Data classification (PII), retention, governance
- Lineage diagram (ingest → transform → serve)

### 4) Logic Mapping → **Logic Nodes**
**Artifacts:** `/logic/L-XXX.md`, `/logic/flows/*.mmd`
- Break work into numbered logic nodes: `L-001`, `L-002`, …
- For each node: preconditions, flow, postconditions, edge cases
- Minimal happy-path pseudocode

### 5) Implementation Planning → **Module Plan**
**Artifacts:** `/implementation/module-plan.md`, `/implementation/code-map.yml`
- Map logic nodes → modules/files/functions
- Choose stack skeletons (React/Express/NestJS/Flask/FastAPI)
- Define feature flags & toggles

### 6) Build → **Traceable Commits**
**Rules:**
- Branch: `feat|fix|chore/L-###-short-desc`
- Commit footer: `Logic: L-###`
- Test filenames include logic ID: `session.L013.test.ts`

### 7) Proof-of-Logic Testing → **Test Matrix**
**Artifact:** `/tests/matrix.csv`
- Each row = logic node → test IDs → coverage notes
- Include property-based or fuzz tests for edge cases where useful

### 8) Review → **Explain-Before-Merge**
**PR template must answer:**
- What problem is solved?
- How do tests prove the logic?
- Architecture deltas (links to updated diagrams)?
- Rollback plan & blast radius

### 9) Release → **Runbook & Observability**
**Artifacts:** `/ops/runbook.md`, `/ops/dashboards.md`
- Feature flags, migration commands, playbooks
- Metrics/logs/alerts mapped to logic nodes where relevant

### 10) Retro → **Learning Notes**
**Artifact:** `/learning/retro.md`
- What confused us? What templates should tighten? What examples to add?

---

## 3) Required templates

### `/architecture/intent.md`
```md
# Intent Brief
- Feature/Change:
- Primary user story:
- Success metric(s):
- Constraints/Assumptions:
- Out-of-scope:
