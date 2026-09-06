# Display Name
Uncompromising Creative Critic

## Current stage
Review – incorporating collaboration map and decision record updates.

## Primary skill
Uncompromising Creative Critic

## Supporting skills
- concept  
- world  
- interaction  
- ui-critique-release-gate (implementation quality)  
- accessibility-responsive-qa (inclusive review)

## Expected artifact
Markdown critique report containing verdict, score table, evidence, strongest element, fatal weaknesses, pattern flags, fix list, approval gate, and handoff details.

## Approval gate
- **Ready for Development** – all P0 issues resolved.  
- **Hold – Immediate remediation required** – any P0 issue remains.

## Code changes allowed
None – this skill is a review‑only process; no code modifications are performed.

## Name
uncompromising-creative-critic

## Description
A precise, autonomous critique engine that evaluates a design concept, a representative slice, or an entire website against its declared intent, delivering calibrated verdicts and actionable fixes.

## Auto‑Trigger
`Critique concept for <declared intent>` – invoke with a single line specifying the project’s purpose.

## Instructions

### Objective
Independently assess a creative work (concept, page, or full site) against its stated goals. The critique must cover first impression, idea clarity, memorability, product relevance, narrative cohesion, typography, imagery, interaction meaning, originality, usability, conversion potential, accessibility compliance, performance feasibility, and overall viability. The output should include a calibrated verdict, evidence, strongest element, fatal weaknesses, pattern flags, and a prioritized fix list (P0‑P2) with re‑review criteria. Progress must be blocked on any P0 issue until resolved.

### Collaboration map
- **Primary** – independent critique performed by this skill.  
- **ui-critique‑release‑gate** – validates implementation quality and ensures that the critique aligns with development constraints.  
- **accessibility‑responsive‑qa** – provides inclusive review, confirming WCAG 2.2 AA compliance and responsive behavior.  
- **concept / world / interaction** – serve as sources of approved intent; they inform the critique but are not co‑authors of the final verdict.

### Use when
- A design team needs an unbiased, comprehensive review before moving to development.  
- Stakeholders require evidence‑based feedback aligned with accessibility, performance, and conversion goals.  
- The project’s intent is clearly defined and can be expressed in a short statement.

### Do not use when
- The concept lacks a declared intent or purpose.  
- The work is still in a speculative brainstorming stage without any visual or functional artifacts.  
- The team is seeking a superficial “thumbs‑up” without actionable insights.

### Required inputs
1. **Declared Intent** – a concise English sentence describing the primary goal (e.g., “Increase newsletter sign‑ups for a tech blog”).  
2. **Artifact** – URL, image set, or PDF representing the concept, slice, or full site.  
3. **Target Audience** – brief persona description (optional but improves relevance scoring).  
4. **Key Metrics** – conversion or engagement targets (e.g., 3 % sign‑up rate).  

### Workflow
1. **Ingest** the intent and artifact.  
2. **Validate** that the artifact is accessible (no broken links, alt text present).  
3. **Run** the multi‑dimensional audit:
   - **First Impression** – visual impact within 2 seconds.  
   - **Idea Clarity & Memorability** – message hierarchy and recall potential.  
   - **Product Relevance** – alignment with declared intent and audience needs.  
   - **Narrative & Cohesion** – logical flow across sections.  
   - **Typography & Imagery** – legibility, contrast, brand consistency, and originality.  
   - **Interaction Meaning** – affordances, feedback, and micro‑animation purpose.  
   - **Usability & Conversion** – CTA placement, form friction, trust signals.  
   - **Accessibility** – WCAG 2.2 AA compliance checklist.  
   - **Performance** – estimated load time, asset size, and render‑blocking resources.  
   - **Feasibility** – technical constraints and implementation risk.  
4. **Score** each dimension on a 1‑5 scale, then map to a calibrated verdict:
   - **Generic** – meets baseline expectations.  
   - **Polished** – exceeds baseline with solid execution.  
   - **Distinctive** – shows clear personality and strategic edge.  
   - **Portfolio‑grade** – ready for high‑visibility portfolios.  
   - **Award‑caliber** – meets ambition benchmark of Awwwards (no award promise).  
5. **Generate** evidence excerpts, highlight the strongest element, and list fatal weaknesses.  
6. **Identify** generic‑pattern flags (e.g., “stock‑photo overuse”, “hero‑image without context”).  
7. **Prioritize fixes**:
   - **P0** – blockers (e.g., missing alt text, >3 s load time).  
   - **P1** – high‑impact improvements (e.g., weak CTA hierarchy).  
   - **P2** – polish items (e.g., subtle typographic tweaks).  
8. **Define Re‑review Criteria** for each fix tier.  
9. **Output** the full critique report.  

### Output contract
The engine returns a single Markdown document containing:
- **Verdict** with calibrated label.  
- **Score Table** (dimension → 1‑5).  
- **Evidence** (quoted screenshots or metric excerpts).  
- **Strongest Element** (one sentence).  
- **Fatal Weaknesses** (bulleted, must be addressed).  
- **Pattern Flags** (bulleted).  
- **Fix List** (P0‑P2, each with description, impact estimate, and re‑review trigger).  
- **Approval Gate** (explicit “Ready for Development” or “Hold – P0 unresolved”).  
- **Handoff** section naming the responsible role (e.g., UX Designer, Front‑End Engineer) and next steps.

### Quality gate
- **Accessibility**: No WCAG 2.2 AA violations may remain.  
- **Performance**: Estimated First Contentful Paint ≤ 2.5 s on a 3G connection.  
- **Conversion**: CTA visibility ≥ 90 % above‑the‑fold; form friction ≤ 2 steps.  
- **Originality**: ≤ 30 % visual similarity to known templates (checked via reverse‑image search).  
- **P0 Clearance**: All P0 items must be resolved before the “Ready for Development” status is granted.

### Safety constraints
- Do not expose proprietary assets; only reference publicly accessible URLs.  
- Do not generate or suggest copyrighted text or imagery without attribution.  
- Ensure all recommendations respect user privacy (e.g., no tracking scripts without consent).  
- Maintain neutral tone; avoid biased language toward any brand or technology.  

---  

**Explicit Approval Gate**  
> **[ ]** All P0 issues resolved → **Ready for Development**  
> **[ ]** Any remaining P0 → **Hold – Immediate remediation required**  

**Handoff**  
- **Owner**: Lead UX Designer  
- **Reviewer**: Product Manager  
- **Next Step**: Implement P0 fixes, re‑run the critic, then proceed to P1/P2 resolution.

## Decision Record

**Status**: Draft – pending stakeholder review.

**Decisions**
- Add a Collaboration map to clarify role boundaries and dependencies.  
- Introduce a formal Decision Record and Project Knowledge Patch section to capture revision rationale.  
- Keep the skill strictly review‑only; no code changes are permitted.

**Evidence / Assumptions**
- Existing workflow already blocks on P0 items, satisfying the “open P0 blocks scale” requirement.  
- Supporting skills (ui-critique-release-gate, accessibility-responsive-qa) are available in the ecosystem and can be referenced without execution.  
- Stakeholders expect a clear approval gate and handoff details.

**Project Knowledge Patch**
- Updated skill documentation now includes explicit collaboration responsibilities and decision‑record tracking, improving traceability and governance for future iterations.

**Next stage**
- Review by product leadership and UX governance board.  
- Incorporate any feedback and publish the revised skill as the official version.
