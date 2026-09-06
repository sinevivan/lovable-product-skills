# Display Name
Scroll Narrative Interaction Director

## Header
- **Current stage**: Planning
- **Primary skill**: scroll-narrative-interaction-director
- **Supporting skills**: frontend-web-expression, accessibility-responsive-qa, react-tailwind-guardrails
- **Expected artifact**: `skills/20-scroll-narrative-interaction-director.md`
- **Approval gate**: checklist in `approval-gate.md`
- **Code changes allowed**: No code changes; planning only

## Name
scroll-narrative-interaction-director

## Description
A specification that choreographs a scroll‑driven narrative experience, mapping emotional and informational arcs to visual beats, spatial transitions, interaction triggers, state feedback, and performance constraints.

### Collaboration map
- **Primary** at Experience/Interaction  
- **Distinctive frontend** supports web expression  
- **Accessibility‑responsive‑QA** constrains motion/access  
- **React‑Tailwind‑Guardrails** provides feasibility and budget only  
- **Visual world** is approved upstream  

## Instructions

### Objective
Define a production‑ready interaction blueprint that guides designers and engineers in creating a meaningful, accessible, and performant scroll‑based storytelling flow. The blueprint must translate the approved concept and visual world into concrete beats, section purposes, transition mechanics, trigger conditions, feedback loops, and fallback behaviors, while ensuring progressive enhancement, mobile/touch/keyboard parity, reduced‑motion alternatives, and strict performance budgets.

### Use when
- A narrative‑driven web page or microsite has received concept approval and visual design sign‑off.  
- The experience relies on scroll as the primary navigation metaphor but must avoid scroll hijacking.  
- Stakeholders require a detailed, implementation‑neutral contract before engineering begins.  
- Accessibility, conversion, and originality are non‑negotiable requirements.

### Do not use when
- The project mandates a fully custom JavaScript animation library that already defines its own interaction contract.  
- The experience is purely static or does not involve progressive storytelling.  
- Legal or compliance constraints forbid any form of motion or dynamic content.  
- The team intends to ship a single‑page app without any scroll‑based narrative elements.

### Required inputs
1. **Concept brief** – high‑level story premise, target audience, conversion goal.  
2. **Visual world assets** – approved color palette, typography, illustration style, and key visual mockups for each narrative beat.  
3. **Emotional arc map** – a list of emotional states (e.g., curiosity, tension, relief) aligned with content sections.  
4. **Performance budget** – maximum total weight (KB), first‑contentful‑paint target (ms), and interaction latency ceiling (ms).  
5. **Accessibility guidelines** – WCAG 2.2 success criteria relevant to motion, focus order, and keyboard operability.

### Workflow
1. **Ingest inputs** – Review the concept brief, visual assets, and emotional arc map. Validate that all assets meet the accessibility checklist.  
2. **Define beats** – Break the narrative into 4–7 logical beats. For each beat, document:  
   - *Purpose* (inform, persuade, delight)  
   - *Emotional state*  
   - *Key visual elements* (hero image, illustration, typographic treatment)  
   - *Spatial layout* (full‑bleed, split‑screen, inset)  
3. **Map scroll positions** – Assign a scroll‑percentage range to each beat (e.g., 0‑15 % for Intro, 15‑45 % for Exploration). Ensure ranges leave a 5 % buffer for device‑specific viewport variations.  
4. **Specify transitions** – For each boundary:  
   - *Trigger* (entering/exiting viewport, scroll velocity threshold)  
   - *Effect* (fade‑in, slide‑up, scale, parallax depth)  
   - *Duration* (ms) and *easing* (cubic‑bezier)  
   - *Reduced‑motion fallback* (instant state change)  
5. **Define interaction states** – Enumerate normal, hover/focus, active, error, and loading states for all interactive elements (buttons, links, media controls). Include ARIA role and label recommendations.  
6. **Performance budgeting** – Allocate budget per beat (e.g., image ≤ 150 KB, animation ≤ 30 KB). Specify lazy‑load thresholds and pre‑fetch hints.  
7. **Error & loading behavior** – Outline placeholder skeletons, retry logic for failed assets, and graceful degradation paths when network conditions exceed 3 s latency.  
8. **Review & sign‑off** – Present the specification to concept owners, visual designers, and accessibility leads. Capture approvals in the “Approval Gate” checklist.  
9. **Handoff** – Export the specification as a Markdown artifact, attach to the project repository, and tag the engineering lead for implementation.

### Output contract
- **Document format** – Markdown file adhering to the headings defined in this template.  
- **Scope** – Complete beat‑by‑beat map, transition definitions, interaction state table, performance budget table, and fallback strategies.  
- **Deliverables** – One file (`skills/20-scroll-narrative-interaction-director.md`) and an accompanying checklist (`approval-gate.md`).  
- **Versioning** – Semantic version `v1.0.0` on first release; increment major for scope changes, minor for added beats, patch for typo fixes.  
- **Acceptance criteria** – All required inputs are referenced, every beat has a defined purpose and transition, reduced‑motion alternatives are present, and total asset weight ≤ performance budget.

### Quality gate
1. **Concept alignment** – Narrative beats reflect the approved story arc.  
2. **Visual fidelity** – All visual references match the signed‑off design system.  
3. **Accessibility compliance** – No motion that violates WCAG 2.2 §2.3.3; all interactive elements are keyboard‑navigable and have appropriate ARIA attributes.  
4. **Performance check** – Simulated page load under 3 s on a 2G connection; first‑contentful‑paint ≤ 800 ms on desktop.  
5. **Approval Gate** – Checklist must be completed:  
   - [ ] Concept Owner sign‑off  
   - [ ] Visual Designer sign‑off  
   - [ ] Accessibility Lead sign‑off  
   - [ ] Performance Engineer sign‑off  
6. **Handoff readiness** – Specification stored in the repository, linked to the issue tracker, and engineering lead notified via project management tool.  

### Safety constraints
- **No scroll hijacking** – The specification must never force the viewport to jump or lock scroll position; all motion is user‑driven.  
- **Reduced‑motion mandatory** – Users with `prefers-reduced-motion` must experience instantaneous state changes without animation.  
- **Data privacy** – No third‑party tracking scripts are introduced as part of the interaction flow.  
- **Error containment** – If any asset fails to load, the fallback UI must remain fully functional and not expose stack traces or raw error messages.  
- **Device parity** – All interactions must be operable via mouse, touch, and keyboard; no feature is exclusive to a single input modality.  

## Decision Record
- **Status**: Proposed  
- **Decisions**: Revise skill to include Collaboration map; limit supporting skills to three orchestrated selections; keep artifact as Markdown plan only, no code.  
- **Evidence/Assumptions**: Existing workflow already satisfies production needs; orchestrator identified three most relevant supports (frontend‑web‑expression, accessibility‑responsive‑qa, react‑tailwind‑guardrails).  
- **Project Knowledge Patch**: Updated skill definition now explicitly ties experience/interaction primary focus to upstream visual approval and budget constraints, ensuring alignment across design, accessibility, and feasibility domains.  
- **Next stage**: Review by orchestrator and stakeholder sign‑off before moving to Implementation Planning.  

---  

*End of specification.*
