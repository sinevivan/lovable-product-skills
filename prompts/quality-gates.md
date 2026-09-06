# Quality Gates

_Reusable English‑language approval gates for Lovable Workspace Skills._  
Each gate defines **Pass Criteria**, **Fail Action**, and **Required Evidence** to ensure consistent, high‑quality deliverables.

---

## 1. Evidence Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | All claims are supported by verifiable, publicly available data (e.g., research papers, official statistics, reputable articles). |
| **Fail Action** | Halt progression. The author must provide or locate appropriate evidence before proceeding. |
| **Required Evidence** | • Direct citations (URL, DOI, or reference) for every factual statement.<br>• Screenshots or archived copies for time‑sensitive sources.<br>• A brief rationale linking the evidence to the claim. |

---

## 2. Problem Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | The problem statement is **clear**, **specific**, and **user‑centered**, with measurable impact. |
| **Fail Action** | Return to the problem definition phase. Refine the scope and user research. |
| **Required Evidence** | • User research summary (interviews, surveys, analytics).<br>• Quantitative metrics (e.g., % of users affected, time lost).<br>• Example scenarios illustrating the pain point. |

---

## 3. MVP Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | The Minimum Viable Product (MVP) includes only the core features that solve the problem at a **usable** level. |
| **Fail Action** | Trim scope or add missing core features. Re‑evaluate the MVP definition. |
| **Required Evidence** | • List of included features with a justification for each.<br>• Exclusion rationale for non‑core features.<br>• Acceptance criteria that can be validated in a single sprint. |

---

## 4. PRD Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | The Product Requirements Document (PRD) is **complete**, **unambiguous**, and **testable**. |
| **Fail Action** | Iterate on the PRD until all sections meet the checklist. |
| **Required Evidence** | • Document covering: purpose, scope, user stories, functional & non‑functional requirements, UI mock‑ups, and success metrics.<br>• Traceability matrix linking requirements to user stories and acceptance tests. |

---

## 5. Narrative Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | The product narrative (tone, voice, story) aligns with brand guidelines and resonates with the target audience. |
| **Fail Action** | Rewrite the narrative, optionally conducting a quick user test. |
| **Required Evidence** | • Narrative draft with highlighted brand voice elements.<br>• Review notes from a brand steward or copy editor.<br>• Sample user feedback confirming resonance. |

---

## 6. Art Direction Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | Visual assets follow the approved style guide (color palette, typography, iconography) and maintain accessibility contrast ratios. |
| **Fail Action** | Revise assets to meet style and accessibility standards. |
| **Required Evidence** | • Annotated mock‑ups or style‑checked screenshots.<br>• Contrast ratio report (WCAG AA minimum).<br>• Sign‑off from the Art Director or design lead. |

---

## 7. Representative Slice Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | A functional slice (e.g., a vertical prototype) demonstrates end‑to‑end flow for a representative user journey. |
| **Fail Action** | Build or extend the slice until the complete journey is covered. |
| **Required Evidence** | • Recorded walkthrough or interactive prototype link.<br>• Checklist of user steps covered.<br>• Usability notes confirming the slice is representative. |

---

## 8. Implementation Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | Code meets the project’s coding standards, passes automated tests, and is reviewed by peers. |
| **Fail Action** | Refactor or add missing tests; reopen the code review. |
| **Required Evidence** | • CI pipeline badge(s) (e.g., build passed, coverage ≥ 80%).<br>• Pull‑request review approvals (≥ 2 reviewers).<br>• Link to the merged PR or commit hash. |

---

## 9. Accessibility Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | All user‑facing components satisfy WCAG 2.1 **AA** criteria. |
| **Fail Action** | Fix identified accessibility issues and re‑run audits. |
| **Required Evidence** | • Automated audit report (e.g., axe, Lighthouse) with zero AA violations.<br>• Manual test checklist confirming keyboard navigation, screen‑reader labeling, and focus order.<br>• Sign‑off from an accessibility specialist. |

---

## 10. Release Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | The release package is versioned, documented, and passes a final smoke‑test in the staging environment. |
| **Fail Action** | Block the release; address missing items before re‑submission. |
| **Required Evidence** | • Release notes with version number and change log.<br>• Staging smoke‑test report (all critical paths passed).<br>• Approval from Release Manager or Product Owner. |

---

## 11. Creative Claims Gate

| Item | Description |
|------|-------------|
| **Pass Criteria** | All marketing or creative claims are truthful, non‑exaggerated, and legally compliant. |
| **Fail Action** | Remove or revise the claim; obtain legal review if needed. |
| **Required Evidence** | • Claim statement with supporting evidence (e.g., test results, certifications).<br>• Legal or compliance sign‑off.<br>• Documentation of any required disclaimer or attribution. |

---

### How to Use

1. **Integrate** each gate into your workflow (e.g., checklist, CI gate, or stage gate meeting).  
2. **Document** the required evidence in a shared location (Confluence, GitHub, or project folder).  
3. **Review** the evidence before moving to the next gate; enforce the *Fail Action* when criteria are not met.  

By applying these gates consistently, Lovable Workspace Skills maintain rigor, transparency, and user‑centric quality across every project.
