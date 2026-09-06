# Display Name
Product Discovery Synthesizer

## Name
product-discovery-synthesizer

## Description
Automatically aggregates raw interview transcripts, survey responses, support tickets, and sales notes into a structured evidence matrix, distinguishing raw data, analyst interpretation, confidence levels, contradictions, and identified research gaps. Triggers when a new collection of user‑facing evidence is uploaded to the repository.

## Instructions

### Objective
Transform heterogeneous user‑research artifacts into a single, machine‑readable synthesis that enables downstream Jobs‑to‑Be‑Done (JTBD) analysis, hypothesis generation, and roadmap prioritization. The output must clearly separate evidence, interpretation, confidence, contradictions, and gaps, and be version‑controlled for auditability.

### Use when
- A batch of qualitative data (interviews, open‑ended survey answers, support tickets, sales call notes) has been collected for a product area.
- The research team needs a concise, evidence‑based briefing before moving to JTBD framing or hypothesis testing.
- Stakeholders require a transparent audit trail of how raw signals were interpreted.

### Do not use when
- The data set consists solely of quantitative metrics (e.g., NPS scores, usage analytics) without narrative context.
- The evidence is still being actively collected; the synthesis would be premature.
- Sensitive personal data (PII) is present and has not been anonymized according to privacy policy.

### Required inputs
1. **Evidence bundle** – a folder (or zip) containing:
   - Interview transcripts (TXT/JSON)
   - Survey open‑ended responses (CSV/JSON)
   - Support ticket excerpts (CSV/JSON)
   - Sales call notes (TXT/Markdown)
2. **Metadata file** (`metadata.yaml`) with:
   - `project_id`
   - `collection_date_range`
   - `source_labels` (e.g., interview, survey, support, sales)
   - `anonymization_status` (true/false)
3. **Confidence rubric** – optional YAML defining confidence thresholds for each source type.

### Workflow
1. **Validate inputs** – check file formats, ensure `anonymization_status: true`. Abort with a clear error if PII is detected.
2. **Parse raw evidence** – ingest each source, tag with `source_label` and timestamp.
3. **Deduplicate** – collapse identical statements across sources, preserving original citations.
4. **Thematic clustering** – apply zero‑shot LLM prompting to group statements into emergent themes; retain original excerpts.
5. **Interpretation layer** – for each theme, generate a concise analyst interpretation, citing supporting excerpts.
6. **Confidence scoring** – assign a confidence level (High/Medium/Low) based on source reliability, sample size, and rubric.
7. **Contradiction detection** – flag themes where statements from different sources directly oppose each other; list opposing excerpts.
8. **Research gap identification** – highlight themes with sparse evidence or low confidence, recommending follow‑up questions.
9. **Assemble evidence matrix** – output a structured JSON (`synthesis.json`) with top‑level keys: `evidence`, `interpretation`, `confidence`, `contradictions`, `gaps`.
10. **Hand off** – write a lightweight handoff file (`handoff.yaml`) containing `next_skill: jtbd-framer`, `synthesis_path: synthesis.json`, and a brief “ready for JTBD” flag.

### Output contract
- **synthesis.json** – schema:
  ```json
  {
    "themes": [
      {
        "id": "T001",
        "label": "string",
        "evidence": ["source_id: excerpt_id"],
        "interpretation": "string",
        "confidence": "High|Medium|Low",
        "contradictions": ["source_id: excerpt_id"],
        "research_gap": "string | null"
      }
    ],
    "metadata": {
      "project_id": "string",
      "generated_at": "ISO8601",
      "input_hash": "SHA256"
    }
  }
  ```
- **handoff.yaml** – keys: `next_skill`, `synthesis_path`, `ready_for_jtbd: true`.
- All files stored under `output/<project_id>/`.

### Quality gate
- **Completeness**: ≥ 90 % of raw excerpts must be represented in at least one theme.
- **Consistency**: No theme may contain both a `High` confidence label and a contradictory excerpt flagged as `High` without an explicit “contradiction” entry.
- **Traceability**: Every interpretation sentence must reference at least one raw excerpt ID.
- **Performance**: Synthesis generation must finish within 5 minutes for ≤ 10 k excerpts.

### Safety constraints
- Enforce strict PII detection; any residual personal identifiers trigger an automatic abort and log a security incident.
- Limit LLM token usage to prevent model hallucination; enforce a maximum of 2 k tokens per thematic clustering pass.
- All generated text must be reviewed by a human analyst before publishing; the skill adds a `review_required: true` flag in `handoff.yaml` if confidence is below `Medium` for any theme.
- Preserve version history: each run creates a new `synthesis_<timestamp>.json` to avoid overwriting prior evidence.
