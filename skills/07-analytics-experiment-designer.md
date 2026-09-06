# Display Name
Experiment Designer

## Name
analytics-experiment-designer

## Description
Generates a comprehensive measurement plan for a product experiment, including product outcome, north‑star and input metrics, event taxonomy, funnel definition, hypothesis, variant design, guardrails, sampling caveats, and decision rules.

## Instructions

### Objective
Produce a structured, evidence‑aware measurement plan that enables product teams to design, run, and evaluate controlled experiments with clear success criteria and risk mitigations. The plan must be ready for implementation in an analytics platform (e.g., Mixpanel, Amplitude, GA4) and hand off to downstream skills such as **Data Pipeline Builder**, **Dashboard Generator**, and **Result Interpreter**.

### Use when
- A product team is launching a new feature, redesign, or pricing change and needs a formal experiment framework.  
- Stakeholders request a documented hypothesis, metric hierarchy, and decision logic before allocating engineering or data resources.  
- Existing analytics infrastructure is in place, and the team requires a reusable template for future experiments.

### Do not use when
- The experiment is purely qualitative (e.g., user interviews) with no measurable digital events.  
- The product lacks any tracking infrastructure; the prerequisite is to first implement event collection.  
- Regulatory or legal constraints forbid the collection of the required user data; a compliance review must precede this skill.

### Required inputs
1. **Product outcome statement** – high‑level business goal (e.g., increase monthly active users).  
2. **North‑star metric** – single metric that best reflects the product outcome.  
3. **Input metrics** – leading indicators that drive the north‑star (e.g., sign‑up conversion rate).  
4. **Event taxonomy** – list of existing or proposed events with property definitions.  
5. **Funnel stages** – ordered steps from acquisition to the product outcome.  
6. **Hypothesis** – concise, testable statement linking variant change to metric impact.  
7. **Variant description** – control and treatment definitions, including UI/UX or algorithmic changes.  
8. **Guardrails** – safety metrics (e.g., error rate, churn) that must not degrade beyond thresholds.  
9. **Sample size constraints** – minimum detectable effect, confidence level, power, and traffic allocation limits.  
10. **Decision rules** – criteria for “win”, “lose”, or “continue” based on statistical significance and business impact.

### Workflow
1. **Validate inputs** – cross‑check that the north‑star aligns with the product outcome and that required events exist in the taxonomy. Flag missing events for the **Event Collector** skill.  
2. **Define metric hierarchy** – map north‑star → input metrics → supporting metrics, noting calculation formulas and aggregation windows.  
3. **Construct funnel** – list funnel steps, assign event triggers, and specify conversion definitions. Include any segment filters (e.g., new vs. returning users).  
4. **Draft hypothesis** – use the format “If [variant change], then [metric] will [direction] by [percentage]”. Cite any prior evidence (A/B tests, user research).  
5. **Specify variants** – detail control and each treatment, including feature flags, UI mockups, or algorithm parameters.  
6. **Set guardrails** – choose safety metrics, define acceptable deviation limits (e.g., error rate ≤ 2 pp), and indicate escalation paths.  
7. **Calculate sample size** – invoke the **Statistical Planner** sub‑skill to produce required users per variant, adjusting for traffic caps and experiment duration. Document assumptions.  
8. **Outline decision rules** – combine statistical thresholds (p < 0.05) with business impact (north‑star lift ≥ X %). Include “inconclusive” handling.  
9. **Produce handoff artifacts** – generate a JSON schema for the **Data Pipeline Builder**, a markdown summary for stakeholders, and a checklist for QA.  
10. **Review & sign‑off** – route the plan to product lead, data analyst, and legal for approval before launch.

### Output contract
- **measurement_plan.md** – human‑readable markdown containing all sections above, formatted for stakeholder review.  
- **measurement_plan.json** – machine‑readable schema with fields: `productOutcome`, `northStar`, `inputMetrics[]`, `eventTaxonomy[]`, `funnelStages[]`, `hypothesis`, `variants[]`, `guardrails[]`, `sampleSize`, `decisionRules`.  
- **handoff_checklist.txt** – actionable list of items for downstream skills (event implementation, pipeline config, dashboard setup).  
All files must be UTF‑8 encoded, version‑controlled, and include a timestamp and author identifier.

### Quality gate
1. **Completeness** – every required input appears; no placeholder “TBD”.  
2. **Consistency** – metric definitions match event property names; funnel steps are logically ordered.  
3. **Statistical soundness** – sample size calculation meets the specified confidence and power.  
4. **Safety compliance** – guardrails are defined and thresholds are realistic given historical data.  
5. **Stakeholder sign‑off** – at least two approvals recorded in the output metadata.

### Safety constraints
- Do not expose raw user identifiers; reference events only by anonymized IDs.  
- Ensure that any suggested data collection complies with GDPR, CCPA, and internal privacy policies.  
- Guardrails must include a “stop‑experiment” trigger if safety metric deviation exceeds 3 × the defined limit.  
- All hypothesis statements must be falsifiable; avoid vague language such as “improve user experience”.  
- If the plan requires new events, automatically generate a **Data Privacy Review** ticket before proceeding.
