# Display Name
MVP Scope Cutter

## Name
mvp-scope-cutter

## Description
Automatically trims an oversized product concept into a single, coherent value loop for a Minimum Viable Product (MVP). It surfaces hypotheses, categorises features (Must, Manual, Later, Remove), defines release boundaries, non‑goals, operational constraints, validation criteria, and stop/pivot signals.

## Instructions

### Objective
Produce a focused MVP definition that delivers measurable user value while limiting scope creep. The output must be a single, end‑to‑end value loop with clearly labelled hypotheses, feature buckets, release boundary, non‑goals, operational constraints, validation plan, and explicit stop/pivot criteria.

### Use when
- A product vision or roadmap is too large for the next iteration.
- Stakeholders request a concrete MVP definition before committing resources.
- Validation data suggests the current scope exceeds the team’s capacity or market risk tolerance.
- You need a hand‑off to downstream skills such as **MVP Validation Planner**, **Release Planning Scheduler**, or **Feature Prioritisation Matrix**.

### Do not use when
- The concept is already scoped to a single, well‑defined user story.
- Regulatory or compliance constraints dominate the scope decision (use the **Compliance Scope Auditor** instead).
- The team lacks any hypothesis or user research data; first run a **User Insight Gatherer**.

### Required inputs
1. **Concept Overview** – 2‑3 paragraph description of the product idea.
2. **Target Persona(s)** – List of primary user archetypes with key pain points.
3. **Current Feature List** – Raw list of all envisioned features, each with a brief purpose.
4. **Assumed Hypotheses** – Explicit statements about why the product will succeed (e.g., “Users will pay $X for Y”).
5. **Resource Constraints** – Team size, budget ceiling, timeline limits, technical dependencies.
6. **Success Metrics** – Quantitative targets for adoption, engagement, or revenue.

### Workflow
1. **Parse Inputs** – Extract entities, map features to personas, and tag each hypothesis.
2. **Cluster Features** – Group features by the user journey step they support; identify overlapping or duplicate items.
3. **Bucket Classification**  
   - **Must**: Directly validates a core hypothesis and fits within constraints.  
   - **Manual**: Requires human‑in‑the‑loop work (e.g., onboarding assistance) and is optional for the first release.  
   - **Later**: Valuable but not needed for hypothesis validation; slated for post‑MVP.  
   - **Remove**: Does not support any hypothesis, exceeds constraints, or duplicates another feature.
4. **Define Value Loop** – Select the smallest set of Must features that creates a closed loop from user problem → solution → value capture.
5. **Set Release Boundary** – List the Must and Manual items that will be shipped; note any “soft launch” constraints.
6. **Specify Non‑Goals** – Explicitly state what will NOT be delivered in this MVP (e.g., “No multi‑language support”).  
7. **Operational Constraints** – Document technical, security, or compliance limits that shape implementation.
8. **Validation Plan** – Map each hypothesis to a measurable test (e.g., A/B test, pilot cohort) and define data collection methods.
9. **Stop/Pivot Signals** – Enumerate quantitative thresholds (e.g., <5% activation rate) and qualitative cues (e.g., repeated user frustration) that trigger a pivot.
10. **Hand‑off Generation** – Produce structured JSON sections for downstream skills:
    - `validation_plan` → **MVP Validation Planner**  
    - `release_schedule` → **Release Planning Scheduler**  
    - `feature_matrix` → **Feature Prioritisation Matrix**  

### Output contract
A single Markdown document containing:
- **Value Loop Diagram** (ASCII or mermaid syntax) summarising the MVP flow.  
- **Feature Buckets** table with columns: Feature, Bucket, Supporting Hypothesis, Owner.  
- **Release Boundary** list with Must & Manual items.  
- **Non‑Goals** bullet list.  
- **Operational Constraints** table.  
- **Validation Plan** table (Hypothesis → Metric → Method → Success Threshold).  
- **Stop/Pivot Signals** table (Signal → Metric → Threshold → Action).  
- **Hand‑off JSON** block (pretty‑printed) for downstream skills.

### Quality gate
- All Must features must map 1:1 to at least one core hypothesis.  
- No feature appears in more than one bucket.  
- Validation plan covers 100 % of core hypotheses.  
- Stop/pivot signals include at least one quantitative and one qualitative trigger.  
- Hand‑off JSON validates against the schema defined in `skill-contracts/mvp-scope.json`.

### Safety constraints
- Do not suggest removing features that address accessibility, privacy, or legal compliance without explicit stakeholder approval.  
- Ensure any data‑driven validation respects user consent and GDPR/CCPA requirements.  
- Flag any feature that could introduce security vulnerabilities for review by the **Security Review** skill.  
- If resource constraints indicate infeasibility (e.g., budget < 50 % of estimated cost), abort and recommend a **Scope Re‑assessment** hand‑off.
