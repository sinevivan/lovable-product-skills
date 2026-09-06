# Display Name
Product Narrative Deck Builder

## Name
product-narrative-deck

## Description
Generate a decision‑oriented presentation storyboard that defines audience, decision, thesis, tension, insight, mechanism, evidence, implications, and ask. Each slide gets a single purpose, with separate copy for slide content and speaker notes, visual role, timing, and identified evidence gaps.

## Instructions

### Objective
Create a complete, production‑ready storyboard for a product narrative deck that can be handed off to a design team and a presenter. The output must be structured slide‑by‑slide, clearly separating slide copy, speaker notes, visual guidance, estimated timing, and any missing evidence that needs to be sourced before finalization.

### Use when
- A product team needs a concise, decision‑focused deck to persuade stakeholders or investors.  
- The deck must align with a specific decision point (e.g., go/no‑go, funding request, market entry).  
- The team has core research, but visual design and exact phrasing still need to be crafted.  

### Do not use when
- The audience requires a deep technical deep‑dive beyond a narrative overview.  
- The presentation is intended as a training module or product tutorial.  
- The required evidence is unavailable or the decision is not yet defined.  

### Required inputs
1. **Audience profile** – role, seniority, and key concerns.  
2. **Decision sought** – the exact action the presenter wants the audience to take.  
3. **Core thesis** – one‑sentence statement that frames the narrative.  
4. **Key insights** – up to three data‑driven insights that support the thesis.  
5. **Mechanism** – the product or solution that resolves the identified tension.  
6. **Available evidence** – links or citations for market data, user research, financial projections, etc.  
7. **Time budget** – total presentation length (e.g., 20 minutes).  

### Workflow
1. **Validate inputs** – confirm that audience, decision, and thesis are mutually consistent.  
2. **Map storyboard** – assign each of the nine narrative elements (audience, decision, thesis, tension, insight, mechanism, evidence, implications, ask) to a dedicated slide.  
3. **Draft slide copy** – write concise bullet or headline text for the slide itself (max 6 words per bullet).  
4. **Write speaker notes** – expand each slide’s copy into a 60‑90 second narrative, including anecdotes or data points.  
5. **Define visual role** – specify the primary visual (e.g., chart, diagram, photo) and its intended impact.  
6. **Estimate timing** – allocate seconds per slide based on copy density and speaker notes.  
7. **Identify evidence gaps** – flag any claim lacking a citation and suggest a source type.  
8. **Review handoff** – produce two deliverables:  
   - **Storyboard markdown** – the final output (this document).  
   - **Design brief** – a concise list of visual assets, dimensions, and branding guidelines for the design team.  

### Output contract
The skill returns a single markdown file with the following structure:

```
## Slide 1 – Audience
**Slide copy:** …
**Speaker notes:** …
**Visual role:** …
**Timing:** xx s
**Evidence gaps:** none / list

## Slide 2 – Decision
...
```

All nine slides must be present, ordered as listed above. Each section must contain the exact headings shown (Slide X – Title, Slide copy, Speaker notes, Visual role, Timing, Evidence gaps). No extraneous commentary, no code fences, and no placeholder text such as “Lorem ipsum”.

### Quality gate
- **Clarity:** Every slide purpose is singular and unambiguous.  
- **Brevity:** Slide copy ≤ 30 words total; speaker notes ≤ 120 words.  
- **Consistency:** Terminology (e.g., “decision”, “thesis”) matches the input values verbatim.  
- **Completeness:** All nine narrative elements are represented, and every evidence gap is explicitly listed.  
- **Timing alignment:** Sum of slide timings ≤ total presentation time ± 10 %.  

### Safety constraints
- Do not fabricate data, quotes, or citations. If a required piece of evidence is missing, mark it as an evidence gap and suggest a realistic source (e.g., “latest Gartner Magic Quadrant”).  
- Avoid disclosing any confidential or proprietary information that was not provided in the inputs.  
- Ensure language is neutral and free of bias; do not make unverified claims about market size, competitor performance, or regulatory approval.  
- Respect copyright: only reference publicly available reports or clearly attribute proprietary sources supplied by the user.
