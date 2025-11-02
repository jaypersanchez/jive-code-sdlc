# Jive-Code SDLC
**Kill the jive. Ship the logic.**  
An open-source, logic-first SDLC that makes architecture and reasoning first-class citizens—so juniors and seniors don’t ship code they can’t explain.

[![License: Apache-2.0](https://img.shields.io/badge/License-Apache--2.0-blue.svg)](LICENSE)
[![Status: Draft](https://img.shields.io/badge/status-draft-informational.svg)]()

## Why this exists
Too many teams ship “jive code”: commits with no coherent logic, reviews that chase syntax instead of understanding, and systems that nobody can reason about six months later.  
**Jive-Code SDLC** fixes that by enforcing a clear path:

**Intent → Solution Architecture → Technical Architecture → Data Architecture → Logic Nodes → Implementation → Proof-of-Logic Tests → Release → Retro**

## What you get
- **Logic nodes (L-###)** with commit/test traceability (`Logic: L-013`).
- **Phase-gated artifacts** (intent, runtime diagrams, interfaces, data contracts).
- **Opinionated project skeletons** that force modularity:
  - **Frontend:** React (TypeScript)
  - **Backend (JS):** Express.js (TS), **NestJS** (recommended for larger teams)
  - **Backend (Py):** Flask (classic), **FastAPI** (recommended for typed contracts)
- **Review ritual:** “Explain-Before-Merge” (reasoning > syntax).
- **CI hooks idea:** fail PRs that don’t link code to logic nodes.

---

## Quickstart
> The CLI below is a **concept** for onboarding; you can follow the **Manual Setup** if you’re not using it yet.

```bash
# 1) Initialize Jive-Code in an existing repo
npx jive init
# or (Python)
pipx run jive-code-sdlc init

# 2) Create a new logic node and scaffolds
jive new-logic L-013 "Session timeout on inactivity"

# 3) Verify links between code/tests and logic nodes
jive check

# 4) Generate a logic coverage report
jive report
