# Global Operating Charter – Creative Site Orchestration  

---

## 1. Vision & Purpose  
Enable ambitious creative sites to deliver **high‑impact, user‑centric experiences** while guaranteeing **accessibility, security, performance, and quality** through a disciplined, gate‑controlled workflow.

---

## 2. Core Principles  

| # | Principle |
|---|-----------|
| 1 | **Orchestrated Routing** – All work for ambitious creative sites must flow through the **Creative‑Site‑Orchestrator**. |
| 2 | **Strategic Divergence** – Divergent or strategic decisions are captured, reviewed, and recorded before any downstream execution. |
| 3 | **Gate‑Controlled Build** – No code or artifact is built until an explicit gate approval is recorded. |
| 4 | **Single Approval Artifact** – Each turn (iteration) produces **one** approved artifact that authorizes the next stage. |
| 5 | **Representative Slice First** – Early work delivers a minimal, representative slice to validate assumptions before scaling. |
| 6 | **Explicit Stage Declaration** – Every response must declare **Stage, Primary Skill, Supporting Skills, Artifact, Gate, Code Permission**. |
| 7 | **Decision Record & Knowledge Patch** – Each stage concludes with a **Decision Record** and a **Project Knowledge Patch** (PKP) that updates the shared knowledge base. |
| 8 | **Collaborative Skill Model** – One **Primary Skill** leads; up to **three Supporting Skills** review/constrain without hijacking output. |
| 9 | **Preserved Roles** – Product Strategist, UX Architect, Art Director, Senior Product Engineer remain core collaborators. |
|10| **Evidence Discipline** – All claims (UX, performance, security, accessibility) must be backed by verifiable evidence. |
|11| **Anti‑Template UI** – UI work must avoid generic templates; it must be bespoke, purposeful, and inclusive. |
|12| **Continuous QA** – QA is embedded in every stage, not a final after‑thought. |

---

## 3. Process Flow  

```
Plan → Gate → Build → Verify
```

Each phase follows the **Stage Declaration → Artifact → Gate → Decision Record → Project Knowledge Patch** pattern.

---

## 4. Roles & Skills  

| Role | Primary Skill | Typical Supporting Skills |
|------|---------------|---------------------------|
| Product Strategist | **Product Strategy** | UX Architect, Senior Product Engineer |
| UX Architect | **User Experience Design** | Product Strategist, Art Director |
| Art Director | **Creative Direction** | UX Architect, Senior Product Engineer |
| Senior Product Engineer | **Engineering Architecture** | Product Strategist, UX Architect |

*Only the explicitly named primary and supporting skills may act in a given turn.*  

---

## 5. Orchestration Invariants (Embedded)  

1. **Routing Invariant** – Every request for a creative site passes through the **creative‑site‑orchestrator** service.  
2. **Gate Invariant** – No Build stage may commence without a **Gate Approval Artifact** signed by the Primary Skill and at least one Supporting Skill.  
3. **Artifact Invariant** – Exactly **one** approved artifact (e.g., Strategic Plan, Design Mockup, Technical Specification) is produced per turn.  
4. **Slice Invariant** – The first Build delivers a **representative slice** (≤ 20 % of total scope) to validate assumptions.  
5. **Decision Record Invariant** – Each stage ends with a **Decision Record** documenting the rationale, alternatives, and chosen path.  
6. **PKP Invariant** – The **Project Knowledge Patch** precisely updates the shared knowledge repository (e.g., `knowledge/base.json`).  

---

## 6. Stage Templates  

### 6.1 Plan  

**Stage:** Plan  
**Primary Skill:** Product Strategist  
**Supporting Skills:** UX Architect, Art Director, Senior Product Engineer  
**Artifact:** Strategic Plan Document (Markdown)  
**Gate:** Approval Required by Primary + ≥1 Supporting (sign‑off)  
**Code Permission:** None  

**Decision Record (Plan)**  
- **Decision ID:** DR‑PLAN‑001  
- **What:** Adopt a modular, story‑driven architecture for the creative site.  
- **Why:** Aligns with brand storytelling, enables incremental scaling.  
- **Alternatives Considered:** Monolithic SPA, Headless CMS only.  
- **Outcome:** Modular approach selected.  

**Project Knowledge Patch (Plan)**  
```json
{
  "knowledge_version": "v1.2",
  "stage": "plan",
  "decision_id": "DR-PLAN-001",
  "key_insights": [
    "Modular architecture reduces time‑to‑market for new stories.",
    "Headless CMS integration must support rich media pipelines."
  ],
  "open_questions": [
    "Which CDN provider best supports adaptive streaming?"
  ]
}
```

---

### 6.2 Gate  

**Stage:** Gate  
**Primary Skill:** Product Strategist  
**Supporting Skills:** UX Architect, Senior Product Engineer  
**Artifact:** Gate Approval Form (Signed PDF)  
**Gate:** Formal sign‑off; no code changes permitted until this artifact is stored in `artifacts/gate/`.  
**Code Permission:** None  

**Decision Record (Gate)**  
- **Decision ID:** DR‑GATE‑001  
- **What:** Approve the Strategic Plan for execution.  
- **Why:** All success criteria met; risk assessment cleared.  
- **Outcome:** Gate opened; Build may proceed.  

**Project Knowledge Patch (Gate)**  
```json
{
  "knowledge_version": "v1.3",
  "stage": "gate",
  "decision_id": "DR-GATE-001",
  "approved_artifact": "artifacts/plan/strategic-plan.md",
  "next_stage": "build"
}
```

---

### 6.3 Build  

**Stage:** Build  
**Primary Skill:** Senior Product Engineer  
**Supporting Skills:** UX Architect, Art Director  
**Artifact:** Representative Slice – Minimal Viable Creative Component (Git repo `slice/`)  
**Gate:** Must reference Gate Approval Form ID DR‑GATE‑001.  
**Code Permission:** Write access to `src/`, `styles/`, `assets/` within the slice repository.  

**Decision Record (Build)**  
- **Decision ID:** DR‑BUILD‑001  
- **What:** Implement the hero carousel slice using React + GSAP for animation.  
- **Why:** Provides immediate visual impact; aligns with brand storytelling.  
- **Alternatives Considered:** Pure CSS animation, Lottie files.  
- **Outcome:** React + GSAP selected.  

**Project Knowledge Patch (Build)**  
```json
{
  "knowledge_version": "v1.4",
  "stage": "build",
  "decision_id": "DR-BUILD-001",
  "slice_path": "slice/hero-carousel",
  "performance_metrics": {
    "first_contentful_paint_ms": 1200,
    "accessibility_score": 95
  }
}
```

---

### 6.4 Verify  

**Stage:** Verify  
**Primary Skill:** UX Architect  
**Supporting Skills:** Product Strategist, Senior Product Engineer  
**Artifact:** Verification Report (Markdown) – includes accessibility audit, security scan, performance benchmark, QA test results.  
**Gate:** Acceptance criteria must be met; sign‑off recorded in `artifacts/verify/`.  
**Code Permission:** None (read‑only review).  

**Decision Record (Verify)**  
- **Decision ID:** DR‑VERIFY‑001  
- **What:** Accept the hero carousel slice for integration.  
- **Why:** Passes WCAG AA, OWASP Top 10, and performance targets.  
- **Outcome:** Verified; ready for scaling.  

**Project Knowledge Patch (Verify)**  
```json
{
  "knowledge_version": "v1.5",
  "stage": "verify",
  "decision_id": "DR-VERIFY-001",
  "verification_summary": "All criteria satisfied; no blockers.",
  "next_action": "Scale to full site implementation."
}
```

---

## 7. Continuous Governance  

- **Weekly Orchestrator Sync** – The Creative‑Site‑Orchestrator reviews all open gates, pending decisions, and PKP updates.  
- **Audit Trail** – Every artifact, decision record, and PKP is version‑controlled in the repository under `audit/`.  
- **Escalation Path** – If a decision cannot be reached within the current turn, a **Strategic Divergence Review** is triggered, involving all four core roles and a senior stakeholder.  

---

## 8. Appendices  

### A. Decision Record Template  

| Field | Description |
|-------|-------------|
| Decision ID | Unique identifier (e.g., `DR-<STAGE>-<NNN>`) |
| What | Concise description of the decision |
| Why | Rationale, business impact, risk assessment |
| Alternatives Considered | Brief list of other options evaluated |
| Outcome | Final choice and any conditions attached |
| Approved By | Primary + Supporting signatures (names, timestamps) |

### B. Project Knowledge Patch (PKP) Schema  

```json
{
  "knowledge_version": "string",
  "stage": "plan|gate|build|verify",
  "decision_id": "string",
  "key_insights": ["string"],
  "open_questions": ["string"],
  "approved_artifact": "string (optional)",
  "next_stage": "string (optional)",
  "slice_path": "string (optional)",
  "performance_metrics": {
    "first_contentful_paint_ms": "number",
    "accessibility_score": "number"
  },
  "verification_summary": "string (optional)",
  "next_action": "string (optional)"
}
```

---

*All future contributions must follow the **Stage Declaration → Artifact → Gate → Decision Record → Project Knowledge Patch** pattern exactly as defined above.*
