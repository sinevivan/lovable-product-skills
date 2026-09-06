# Display Name
Competitive Intelligence

## Name
competitive-intelligence

## Description
Researches, compares, and synthesizes evidence on direct and indirect competitors and substitute products, delivering a structured analysis that highlights source discipline, confidence levels, category conventions, identified gaps, and strategic implications.

## Auto‑trigger
“Analyze competitor landscape”

## Instructions

### Objective
Generate a comprehensive, evidence‑backed competitor matrix that enables product and strategy teams to understand market positioning, feature differentials, pricing models, go‑to‑market tactics, and emerging threats. The output must be ready for downstream synthesis by the **Market Analysis** and **Strategic Recommendations** skills.

### Use when
- A product team needs a fresh snapshot of the competitive environment for a launch or pivot.
- Stakeholders request a side‑by‑side comparison of key players and substitutes.
- Evidence from public sources, internal data feeds, or paid databases is available and can be cited.

### Do not use when
- The request lacks verifiable sources or relies solely on speculation.
- The analysis would require confidential, non‑public data that the system cannot legally access.
- The scope exceeds the defined time horizon (e.g., “all competitors since 2000” without a clear focus).

### Required inputs
1. **Target domain** – industry or product category (e.g., “cloud‑based CRM”).  
2. **Competitor list** – optional explicit list; if omitted, the skill will generate a shortlist of top‑5 direct and 3 indirect competitors based on market share and relevance.  
3. **Evidence sources** – URLs, database identifiers, or document references. If not supplied, the skill will query approved public APIs (e.g., Crunchbase, SEC filings) and annotate each source.  
4. **Confidence rubric** – optional custom scale; defaults to: *High* (primary source, recent), *Medium* (secondary source, ≤2 years old), *Low* (blog, analyst opinion).  
5. **Comparison dimensions** – mandatory list (e.g., “pricing, feature set, integration, customer base, go‑to‑market”).  

### Workflow
1. **Validate inputs** – ensure domain, dimensions, and source list are present; reject if missing.  
2. **Scope competitors** – if no explicit list, run a market‑size query, rank by revenue or user base, and select top candidates.  
3. **Collect evidence** – for each competitor and dimension, retrieve up to three recent, reputable sources. Tag each with discipline (e.g., *Financial filing*, *Press release*, *Analyst report*) and timestamp.  
4. **Assess confidence** – apply the confidence rubric automatically; allow manual override via optional input.  
5. **Synthesize matrix** – populate a markdown table: rows = competitors, columns = dimensions; each cell contains a concise bullet (≤ 15 words) plus source citation and confidence label.  
6. **Identify gaps** – flag dimensions where evidence is missing or confidence is *Low*; list as “Evidence Gap”.  
7. **Derive strategic implications** – write 2‑3 short insights (≤ 30 words each) that connect gaps or strengths to potential strategic actions.  
8. **Hand‑off** – embed a JSON pointer to the next skill:
   ```json
   {"next_skill":"market-analysis","reason":"needs aggregated market sizing for deeper context"}
   ```
   and another pointer to **Strategic Recommendations** for action planning.

### Output contract
- **File**: `competitor_matrix.md` – markdown table with citations, confidence tags, and a “Gaps & Implications” section.  
- **Metadata**: JSON block at the end containing:
  - `timestamp_utc`
  - `source_summary` (list of disciplines and counts)
  - `confidence_distribution` (percentage per label)
  - `gap_summary` (count of missing evidence per dimension)
- **Length**: ≤ 2 pages of markdown; table rows ≤ 10, columns ≤ 8.  
- **Formatting**: Use fenced code blocks for JSON, markdown tables for the matrix, and bullet lists for gaps/implications.

### Quality gate
1. **Source verification** – every citation must resolve to a live URL or document ID; broken links cause rejection.  
2. **Confidence consistency** – at least 80 % of cells must have *High* or *Medium* confidence; otherwise, request clarification.  
3. **Completeness** – all requested dimensions must appear; missing dimensions trigger a “Missing Dimension” error.  
4. **Clarity** – each cell text ≤ 15 words; no jargon without definition.  
5. **Peer review flag** – if any *Low* confidence appears, add a `review_needed: true` flag in the metadata.

### Safety constraints
- **Data privacy** – never expose non‑public internal documents; if a source is flagged as confidential, replace with “Confidential source – not disclosed”.  
- **Bias mitigation** – ensure at least two independent sources per competitor where possible; avoid over‑reliance on a single analyst firm.  
- **Legal compliance** – exclude any content that could infringe on copyright or trademark; use only fair‑use excerpts (≤ 30 words) with proper attribution.  
- **Escalation** – if the skill cannot locate sufficient evidence for a core competitor, raise a `escalation` flag directing the user to the **Data Acquisition** skill for targeted data collection.
