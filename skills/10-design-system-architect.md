# Display Name
Design System Architect

## Name
design-system-architect

## Description
Defines product‑specific design system foundations—including principles, semantic tokens, layout rules, primitives, compositions, components, variants, states, content guidelines, responsive behavior, accessibility, governance, and migration strategy—after visual direction approval, while preventing premature abstraction.

## Auto‑trigger
When visual direction is approved, automatically initiate the design system architecture workflow.

## Instructions

### Objective
Create a cohesive, scalable design system that translates the approved visual direction into concrete, reusable assets and rules for the product. The output must balance specificity with flexibility, enabling rapid UI development while safeguarding brand integrity, accessibility, and future evolution.

### Use when
- The visual direction (brand colors, typography, mood boards, high‑level UI mockups) has been formally signed off by stakeholders.  
- A product team needs a concrete design foundation before engineering begins component implementation.  
- There is a requirement to align multiple squads on a shared visual language and governance model.

### Do not use when
- Visual direction is still under discussion or pending stakeholder sign‑off.  
- The product is a one‑off prototype with no intention of reuse or long‑term maintenance.  
- Existing design system already satisfies all product needs without modification.

### Required inputs
1. **Approved visual direction package** – brand assets, mood boards, high‑fidelity mockups, and any style guides.  
2. **Product scope document** – list of screens, user flows, and key interaction patterns.  
3. **Accessibility standards** – WCAG level (e.g., AA) and any internal accessibility policies.  
4. **Technology stack details** – framework (React, Vue, etc.), design token format (JSON, SCSS, etc.).  
5. **Governance preferences** – versioning policy, contribution workflow, and migration timeline.

### Workflow
1. **Ingest & Align** – Review visual direction and product scope; map high‑level brand attributes to product goals.  
2. **Define Principles** – Draft 3‑5 product‑specific design principles that guide decisions (e.g., “Clarity first”, “Micro‑interactions reinforce feedback”).  
3. **Create Semantic Tokens** – Translate colors, typography, spacing, elevation, and motion into token groups (e.g., `color.brand-primary`, `spacing.base`). Document token purpose, usage, and fallback values.  
4. **Establish Layout Rules** – Specify grid system, breakpoints, column ratios, and spacing conventions. Include rules for fluid vs. fixed layouts.  
5. **Design Primitives** – Build atomic UI elements (e.g., buttons, inputs, icons) with token bindings and state definitions (default, hover, focus, disabled, error).  
6. **Compose Patterns** – Combine primitives into higher‑order compositions (e.g., card, modal, form field group) with documented interaction flows.  
7. **Component Catalog** – List all components, their variants, and state diagrams. Provide usage examples and API signatures for developers.  
8. **Content Rules** – Define tone, copy hierarchy, placeholder guidelines, and localization considerations.  
9. **Responsive Behavior** – Map each component/composition to breakpoint‑specific adaptations, including fluid scaling and re‑flow rules.  
10. **Accessibility Checklist** – Attach ARIA roles, contrast ratios, focus order, and keyboard navigation requirements to each component.  
11. **Governance Model** – Outline contribution process, review gates, versioning scheme, and deprecation policy.  
12. **Migration Plan** – If an existing system exists, produce a phased migration roadmap with risk assessment and rollback procedures.  
13. **Review & Sign‑off** – Conduct cross‑functional review (design, engineering, product, QA) and capture approvals in the repository.

### Output contract
- **design-system.yaml** – Structured definition of principles, tokens, layout, and governance.  
- **tokens/** – JSON/SCSS files containing all semantic tokens.  
- **components/** – Markdown documentation for each component, including variants, states, usage examples, and accessibility notes.  
- **patterns/** – Composition diagrams and responsive behavior tables.  
- **migration-plan.md** – Step‑by‑step migration schedule with milestones and owners.  
All artifacts must be stored under the `skills/design-system-architect/` directory and referenced in the repository’s index.

### Quality gate
- **Consistency** – All tokens follow the naming convention and map to a single source of truth.  
- **Accessibility compliance** – Every component passes automated WCAG AA checks.  
- **Review coverage** – Minimum of two designers, one engineer, and one product manager approve each section.  
- **Testability** – Generated token files can be imported without syntax errors; component docs include runnable code snippets.  
- **Documentation completeness** – No “TODO” placeholders remain; every component lists at least one example usage.

### Safety constraints
- Do not introduce brand‑changing colors or typography without explicit stakeholder approval.  
- Avoid abstracting patterns that are not yet demonstrated in the approved mockups; keep abstractions grounded in concrete use cases.  
- Ensure no proprietary or confidential assets are exposed in token files; strip any watermark or licensed imagery.  
- Validate that all generated files are free of malicious code or executable scripts before committing to the repository.
