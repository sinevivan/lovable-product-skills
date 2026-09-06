# Display Name
JTBD Problem Framing

## Name
jtbd-problem-framing

## Description
Transforms synthesized research evidence into a situation‑specific Job‑to‑Be‑Done (JTBD) statement, identifies forces of progress, frames the problem in a solution‑neutral way, and enumerates desired outcomes. This skill prepares the foundation for a Product Requirements Document (PRD) and hands off to the “PRD Drafting” skill.

## Instructions

### Objective
Create a concise, evidence‑backed JTBD narrative that captures the user’s core job, the circumstances prompting the job, and the progress the user seeks. Articulate the forces of progress (push, pull, anxiety, habit) and list measurable desired outcomes. The output must be ready for direct ingestion by the PRD Drafting skill.

### Use when
- A research synthesis (e.g., interview themes, survey insights, competitive analysis) is complete and needs to be operationalized into product‑level problem statements.
- Stakeholders require a shared, solution‑agnostic description of the user need before ideation.
- The team is preparing to write a PRD and needs a clear JTBD foundation.

### Do not use when
- Raw data collection is still ongoing; the evidence base is incomplete or unvalidated.
- The team is already deep in solution design or feature brainstorming; JTBD framing would be premature.
- Legal or compliance constraints prevent sharing of user quotes or sensitive data.

### Required inputs
1. **Evidence bundle** – Structured JSON or markdown containing:
   - Key user quotes (anonymized)
   - Quantitative findings (e.g., NPS, usage frequency)
   - Competitive gaps
   - Contextual triggers (situational factors)
2. **Target persona identifier** – Reference to the persona the JTBD applies to.
3. **Scope definition** – Optional boundaries (e.g., “mobile checkout flow only”).

### Workflow
1. **Validate evidence** – Confirm that each piece of evidence is sourced, dated, and has a confidence rating ≥ 0.7. Flag any low‑confidence items for review.
2. **Extract core job** – Synthesize user statements to a single verb‑object phrase (e.g., “securely purchase groceries online”). Ensure the phrasing is action‑oriented and outcome‑focused.
3. **Map forces of progress** – Using the evidence, populate:
   - *Push*: Pain or dissatisfaction driving the need.
   - *Pull*: Aspirations or benefits attracting the user.
   - *Anxiety*: Risks or uncertainties that deter action.
   - *Habit*: Existing routines that compete with the new job.
4. **Draft solution‑neutral problem framing** – Write a one‑sentence statement that describes the problem without implying a specific solution (e.g., “Users struggle to complete checkout when payment options are limited”). Cite at least two evidence items.
5. **Define desired outcomes** – List 3‑5 outcome metrics (e.g., “Reduce checkout abandonment rate by 20 % within 3 months”) with a clear measurement method.
6. **Review handoff checklist** – Verify that all required fields are populated and that the output complies with the Quality gate and Safety constraints.
7. **Export** – Produce a JSON payload (see Output contract) and a human‑readable markdown summary for stakeholder review.

### Output contract
```json
{
  "jtbd_statement": "string",
  "forces_of_progress": {
    "push": ["string"],
    "pull": ["string"],
    "anxiety": ["string"],
    "habit": ["string"]
  },
  "problem_framing": "string",
  "desired_outcomes": [
    {
      "outcome": "string",
      "metric": "string",
      "target": "string"
    }
  ],
  "evidence_refs": ["evidence_id_1", "evidence_id_2"],
  "handed_off_to": "prd-drafting"
}
```
Additionally, a markdown section titled **“Stakeholder Summary”** must be included, containing the JTBD, forces, problem framing, and outcomes in plain language.

### Quality gate
- **Evidence coverage**: ≥ 80 % of cited evidence must have a confidence rating ≥ 0.7.
- **Clarity**: JTBD statement ≤ 12 words; problem framing ≤ 20 words.
- **Outcome measurability**: Each outcome includes a quantitative metric and a time‑bound target.
- **Consistency**: Terminology matches the referenced persona and scope definitions.
- **Peer review**: At least one UX researcher and one product manager must approve the markdown summary.

### Safety constraints
- **Privacy**: No raw personally identifiable information (PII) or protected health information (PHI) may appear in the output. All user quotes must be anonymized.
- **Bias mitigation**: Verify that the JTBD does not over‑represent a single demographic unless explicitly scoped. Include a brief bias note if evidence is skewed.
- **Legal compliance**: Ensure that any competitive gap statements do not disclose confidential competitor data beyond public sources.
