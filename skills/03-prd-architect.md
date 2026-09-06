# Display Name
PRD Architect

## Name
prd-architect

## Description
Generate an implementation‑ready Product Requirements Document (PRD) from an approved problem statement and desired outcome, detailing users, scope, functional and non‑functional requirements, states, acceptance criteria, analytics, risks, rollout plan, and open decisions.

## Instructions

### Objective
Transform a validated problem + outcome pair into a comprehensive, implementation‑ready PRD that can be handed off to downstream design, engineering, and release planning skills without ambiguity.

### Use when
- A product team has signed off on a problem statement and target outcome.
- Stakeholders request a formal PRD to align engineering, design, analytics, and release teams.
- The project is entering the planning phase and needs concrete requirements, acceptance criteria, and risk analysis.

### Do not use when
- The problem or outcome is still under investigation or lacks stakeholder approval.
- The team is only exploring concepts and does not need detailed requirements.
- Confidential data required for the PRD is unavailable or unverified.

### Required inputs
1. **ApprovedProblem** – Text of the signed‑off problem statement (including context, pain points, and affected personas).  
2. **DesiredOutcome** – Measurable goal(s) approved by stakeholders (e.g., “increase conversion by 12 % within Q4”).  
3. **StakeholderList** – Names and roles of all owners who approved the problem/outcome.  
4. **UserSegments** – Enumerated primary and secondary user personas with brief characteristics.  
5. **Constraints** – Any known technical, regulatory, or budgetary limits.  
6. **OpenDecisions** – List of decisions still pending (e.g., platform choice, third‑party integration).  
7. **EvidenceArtifacts** – Links or references to research, analytics, or user interviews that justify the problem/outcome.

### Workflow
1. **Validate Inputs** – Confirm that all required fields are present and that the problem/outcome have explicit approval signatures. Flag missing items to the *Stakeholder Confirmation* skill.  
2. **Extract Core Elements** – Parse the problem to identify pain points, affected users, and success metrics; parse the outcome for quantitative targets.  
3. **Define Scope** – List in‑scope features, out‑of‑scope boundaries, and any phased rollout considerations.  
4. **Draft Functional Requirements** – For each user segment, write user stories (As a …, I want …, so that …) and map them to acceptance criteria.  
5. **Add Non‑Functional Requirements** – Include performance, security, accessibility, scalability, and compliance criteria derived from Constraints.  
6. **Model States & Flows** – Outline high‑level state diagrams (e.g., “Draft → Review → Approved → Live”) and key transition triggers.  
7. **Specify Analytics** – Define required metrics, instrumentation points, and success thresholds aligned with DesiredOutcome.  
8. **Identify Risks & Mitigations** – Use the EvidenceArtifacts to surface known risks; propose mitigation strategies.  
9. **Create Rollout Plan** – Suggest phased launch, beta groups, and post‑launch monitoring steps.  
10. **Compile Open Decisions** – Highlight pending items with decision owners and suggested evaluation dates.  
11. **Review & Handoff** – Pass the drafted PRD to the *Design Spec Writer* skill for UI/UX elaboration, then to the *Engineering Estimator* skill for effort sizing, and finally to the *Release Planner* skill for schedule integration.

### Output contract
- **File**: `PRD_<slug>.md` (e.g., `PRD_prd-architect.md`).  
- **Structure**: Title, Problem, Outcome, Users, Scope, Functional Requirements, Non‑Functional Requirements, State Model, Acceptance Criteria, Analytics Plan, Risks & Mitigations, Rollout Strategy, Open Decisions, Appendices (EvidenceArtifacts).  
- **Metadata**: `generated_by: prd-architect`, `generated_at: <ISO‑8601 timestamp>`, `source_refs: [list of EvidenceArtifacts IDs]`.  
- **Quality**: Must pass the Quality Gate (see below) before being marked “Ready for Handoff”.

### Quality gate
1. **Completeness** – All required sections present; no placeholder text.  
2. **Traceability** – Every requirement links back to a user segment or outcome metric.  
3. **Clarity** – Sentences ≤ 20 words, no ambiguous terms (“fast”, “intuitive”) without definition.  
4. **Verification** – Acceptance criteria are testable (given‑when‑then format).  
5. **Compliance** – All regulatory constraints explicitly addressed.  
6. **Peer Review** – At least two stakeholder signatures recorded in the PRD footer.

If any gate fails, return a concise error list to the invoking agent and route back to the *Stakeholder Confirmation* skill for remediation.

### Safety constraints
- **Data Confidentiality** – Do not expose raw user data; reference only anonymized IDs or aggregated metrics.  
- **Bias Mitigation** – Ensure user segments are described without stereotypes; validate language with the *Bias Review* skill.  
- **Regulatory Adherence** – Verify that security and privacy requirements meet GDPR, CCPA, or other applicable frameworks before inclusion.  
- **Version Control** – Do not overwrite existing PRDs; always create a new version with incremental identifier.  
- **Escalation** – If conflicting stakeholder approvals are detected, abort generation and notify the *Conflict Resolution* skill.
