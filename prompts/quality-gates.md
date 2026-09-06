# prompts/quality-gates.md

## Standard Header
| Field                | Description |
|----------------------|-------------|
| **Current stage**    | The lifecycle stage of the prompt (e.g., Ideation, Draft, Review, Approved, Deployed). |
| **Primary skill**    | The single most important skill the prompt exercises (must be one of the 23 library skills). |
| **Supporting skills**| Up to three additional skills that complement the primary skill. |
| **Expected artifact**| The deliverable the prompt is intended to produce (e.g., Markdown guide, JSON schema, UI mock‑up). |
| **Approval gate**    | The gate that must be cleared before the artifact can be considered approved (e.g., Orchestration Gate). |
| **Code changes allowed** | Yes / No – indicates whether the prompt may trigger code modifications. |

## Decision Record
| Field                     | Description |
|---------------------------|-------------|
| **status**                | Draft / Proposed / Accepted / Rejected / Superseded |
| **decisions**             | Concise list of key decisions made for this prompt (e.g., skill selection, scope, constraints). |
| **evidence/assumptions**  | Links or references to data, research, or assumptions that support the decisions. |
| **Project Knowledge Patch** | Summary of new knowledge added to the project repository (e.g., updated README, new examples). |
| **next stage**            | The subsequent lifecycle stage after this decision record is approved. |

---

## Quality Gates

### 1. Evidence Gate
- **Pass criteria**: All claims in the prompt are backed by verifiable data, citations, or reproducible experiments.  
- **Fail action**: Prompt is sent back to the author for additional research or clarification.  
- **Evidence required**: Links to studies, benchmark results, or internal data sets; annotated screenshots if applicable.

### 2. Problem Gate
- **Pass criteria**: The problem statement is clearly defined, scoped, and aligned with user needs or business objectives.  
- **Fail action**: Re‑write the problem description; add user stories or use‑case diagrams.  
- **Evidence required**: User research summary, stakeholder interview notes, or market analysis excerpt.

### 3. MVP Gate
- **Pass criteria**: The Minimum Viable Prompt (MVP) is identified, delivering core value with the smallest viable scope.  
- **Fail action**: Reduce scope or split the prompt into multiple incremental versions.  
- **Evidence required**: MVP definition table, success metrics, and a risk‑reduction plan.

### 4. PRD Gate
- **Pass criteria**: A concise Product Requirements Document exists, covering functional and non‑functional requirements.  
- **Fail action**: Draft or update the PRD before proceeding.  
- **Evidence required**: PRD link or embedded excerpt; traceability matrix linking requirements to the prompt.

### 5. Narrative Gate
- **Pass criteria**: The narrative flow (intro, context, instructions, examples, conclusion) is logical and engaging.  
- **Fail action**: Restructure the narrative; add missing sections or improve transitions.  
- **Evidence required**: Outline diagram or storyboard; readability scores (e.g., Flesch‑Kincaid).

### 6. Art Direction Gate
- **Pass criteria**: Visual or stylistic guidance (tone, branding, formatting) aligns with project style guide.  
- **Fail action**: Apply the style guide; iterate with a designer if needed.  
- **Evidence required**: Style guide reference, annotated mock‑ups, or color/font palettes.

### 7. Representative Slice Gate
- **Pass criteria**: A representative slice (sample prompt segment) demonstrates end‑to‑end behavior across all involved skills.  
- **Fail action**: Expand the slice or create additional examples covering missing skill interactions.  
- **Evidence required**: Executable snippet, test logs, and expected vs. actual output comparison.

### 8. Implementation Gate
- **Pass criteria**: Implementation details (algorithms, API calls, data pipelines) are fully specified and feasible.  
- **Fail action**: Refine the technical design; address any missing dependencies.  
- **Evidence required**: Architecture diagram, pseudo‑code, dependency list, and performance estimates.

### 9. Accessibility Gate
- **Pass criteria**: Prompt complies with accessibility standards (WCAG 2.1 AA or equivalent) for language, structure, and interaction.  
- **Fail action**: Add alternative text, simplify language, or adjust interaction patterns.  
- **Evidence required**: Accessibility audit checklist, screen‑reader test results, and remediation plan.

### 10. Release Gate
- **Pass criteria**: All release criteria (versioning, documentation, rollback plan) are satisfied.  
- **Fail action**: Complete missing release artifacts; update changelog.  
- **Evidence required**: Release notes, version tag, deployment script, and sign‑off from release manager.

### 11. Creative Claims Gate
- **Pass criteria**: Any creative or marketing claims are truthful, substantiated, and do not violate policy.  
- **Fail action**: Revise claims; add supporting evidence or remove unverified statements.  
- **Evidence required**: Claim justification document, legal review sign‑off, and A/B test results if applicable.

### 12. Orchestration Gate (Standard Header & Governance)
- **Purpose**: Ensures the prompt package conforms to project governance before any downstream work begins.  
- **Pass criteria**:  
  1. **Standard Header** – All required fields are present and correctly populated.  
  2. **Primary / Supporting Skills** – Exactly one primary skill and no more than three supporting skills are listed, each from the approved 23‑skill taxonomy.  
  3. **Plan/Build Permission** – The header’s “Code changes allowed” field matches the intended activity (e.g., “No” for pure content prompts).  
  4. **Upstream Approvals** – All required upstream approvals (e.g., product owner, compliance, UX) are documented with signatures or approved tickets.  
  5. **Approval Artifact** – A single, definitive approval artifact (e.g., signed Decision Record PDF or approved JIRA ticket) is attached.  
  6. **Decision Record** – A complete Decision Record (see section above) is present and linked.  
  7. **Project Knowledge Patch** – Any new knowledge introduced is captured in the project knowledge base and referenced.  
- **Fail action**: Block further progress; return to author with a checklist of missing/incorrect items.  
- **Evidence required**:  
  - Filled Standard Header table.  
  - Skill taxonomy verification screenshot or link.  
  - Permission flag screenshot or policy reference.  
  - Approval artifact (link or attachment).  
  - Decision Record (link or embedded).  
  - Knowledge patch commit hash or documentation URL.  

---

*All gates must be documented in the prompt’s repository with the above pass/fail criteria and evidence links. The Orchestration Gate is the final gate before a prompt can move from **Draft** to **Approved**.*
