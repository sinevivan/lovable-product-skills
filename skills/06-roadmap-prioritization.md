# Display Name
Roadmap Prioritization

## Name
roadmap-prioritization

## Description
Prioritizes product initiatives using transparent scoring methods (RICE, ICE, WSJF, or custom criteria). Calculates scores, flags missing inputs, quantifies confidence, runs sensitivity checks, and outputs a clear Now / Next / Later recommendation with rationale.

## Instructions

### Objective
Generate a data‑driven ranking of initiatives that balances business impact, effort, risk, and time‑to‑value. The output must be reproducible, explain assumptions, and highlight where additional evidence is required before committing to a decision.

### Use when
- A product team needs to decide which features, bugs, or experiments to schedule in the upcoming planning cycle.  
- Stakeholders request a transparent justification for the ordering of work items.  
- Multiple scoring frameworks are being considered and a comparative view is useful.

### Do not use when
- The initiative list is incomplete or lacks any quantitative or qualitative inputs required for the chosen framework.  
- Decisions are driven solely by political or contractual obligations that cannot be expressed in the scoring model.  
- Real‑time emergency fixes must be deployed without a formal prioritization step.

### Required inputs
1. **Initiative list** – array of objects with `id`, `title`, and optional `description`.  
2. **Scoring framework** – one of `RICE`, `ICE`, `WSJF`, or a custom JSON schema defining factor names, weights, and formulas.  
3. **Factor values** – for each initiative, provide numeric values for every factor required by the selected framework (e.g., Reach, Impact, Confidence, Effort for RICE).  
4. **Confidence level** – optional per‑factor confidence score (0–1) to be used in sensitivity analysis.  
5. **Business constraints** – optional tags such as `must‑deliver`, `regulatory`, or `dependency` that affect handoff logic.  

If any required factor is missing, the skill must flag the initiative and request clarification before scoring.

### Workflow
1. **Validate inputs** – ensure every initiative contains all factors required by the chosen framework; emit a **MissingData** warning for gaps.  
2. **Normalize factors** – apply min‑max scaling across the initiative set to keep scores comparable.  
3. **Compute raw scores**  
   - **RICE**: `Score = (Reach × Impact × Confidence) / Effort`  
   - **ICE**: `Score = Impact × Confidence × Ease`  
   - **WSJF**: `Score = (User‑Business Value + Time‑Criticality + Risk‑Reduction‑Opportunity‑Enablement) / Job‑Size`  
   - **Custom**: evaluate the user‑supplied formula using the normalized factor values.  
4. **Apply confidence weighting** – multiply each raw score by the geometric mean of its factor confidences to obtain a **Confidence‑Adjusted Score**.  
5. **Run sensitivity analysis** – perturb each factor by ±10 % and recompute scores; record the range (`minScore`, `maxScore`).  
6. **Rank initiatives** – sort by descending Confidence‑Adjusted Score; break ties using business constraints (`must‑deliver` > others).  
7. **Segment timeline** – assign the top 20 % to **Now**, the next 30 % to **Next**, and the remainder to **Later**. Adjust boundaries if a `must‑deliver` item falls outside **Now**; promote it and shift the lowest‑scoring **Now** item to **Next**.  
8. **Generate rationale** – for each tier, list the top three drivers (factors with highest contribution) and note any high‑variance scores from the sensitivity step.  
9. **Hand off** – produce a JSON payload for the downstream skill **roadmap‑sequencing** containing the tiered list and any unresolved data gaps.  

### Output contract
```json
{
  "framework": "RICE|ICE|WSJF|custom",
  "ranking": [
    {
      "id": "string",
      "title": "string",
      "score": number,
      "confidenceAdjustedScore": number,
      "scoreRange": {"min": number, "max": number},
      "tier": "Now|Next|Later",
      "topDrivers": ["factor1","factor2","factor3"],
      "missingData": false,
      "notes": "optional rationale"
    }
  ],
  "handOff": {
    "toSkill": "roadmap-sequencing",
    "payload": { /* same ranking array */ }
  },
  "warnings": ["MissingData: initiative XYZ lacks Effort", "LowConfidence: average confidence < 0.4"]
}
```
All numeric values are rounded to two decimal places. The output must be valid JSON and free of markdown formatting.

### Quality gate
- **Completeness**: ≥ 95 % of required factor values present; otherwise fail with a MissingData warning.  
- **Confidence threshold**: average confidence ≥ 0.6; if lower, flag a **LowConfidence** warning and suggest data refinement.  
- **Sensitivity stability**: for ≥ 80 % of initiatives, `maxScore - minScore` ≤ 15 % of the raw score; otherwise add a **HighVariance** note.  
- **Determinism**: given identical inputs, the ranking order must be repeatable.

### Safety constraints
- Do not infer or fabricate factor values; always request explicit input.  
- Avoid exposing proprietary business metrics in the public output; mask any field named `cost` or `revenue` unless explicitly allowed in the input schema.  
- Ensure that any handoff payload complies with the receiving skill’s schema; validate against the `roadmap‑sequencing` contract before transmission.  
- Log all warnings and confidence adjustments for auditability, but do not store raw initiative descriptions longer than 30 days.
