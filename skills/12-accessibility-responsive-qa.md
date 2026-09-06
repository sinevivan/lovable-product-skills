# Display Name
Accessibility Responsive QA

## Name
accessibility-responsive-qa

accessibility-responsive-qa

## Description
Audit a completed or near‑complete user interface for WCAG 2.2‑informed accessibility, focusing on keyboard operability, focus management, labeling, semantic structure, colour contrast, zoom/reflow, touch target size, status/error communication, reduced motion, responsive breakpoints, overflow handling and orientation support. Findings are presented first; remediation recommendations are supplied only after stakeholder approval.

## Instructions

### Objective
Provide a systematic, evidence‑based assessment of a UI’s compliance with core WCAG 2.2 success criteria relevant to responsive design and interaction, without implying formal certification. The output must separate observed issues from suggested fixes, enabling a clear hand‑off to design or development teams.

### Use when
- A UI is finished or in the final stages of development and needs an accessibility health check before release.  
- Stakeholders require a concise, prioritized list of accessibility gaps that are specific to responsive behaviours and interaction patterns.  
- The team plans to iterate on the UI based on concrete findings rather than a blanket “pass/fail” verdict.

### Do not use when
- The UI is still in early wire‑frame or mock‑up stage; a design‑level audit is more appropriate.  
- Formal accessibility certification (e.g., EN 301 549, Section 508) is required; this skill only produces an advisory report.  
- The project scope excludes responsive or interactive components (e.g., static PDFs).

### Required inputs
1. **URL or local path** to the live page or build artifact to be audited.  
2. **Device matrix** (list of viewport widths, pixel densities, and input modalities such as keyboard, screen reader, touch, and assistive‑technology simulators).  
3. **Target audience summary** (e.g., primary assistive‑technology users, language preferences).  
4. **Existing accessibility documentation** (if any) to avoid duplicate findings.  
5. **Stakeholder approval flag** (`true` to proceed with remediation suggestions, `false` to stop after findings).

### Workflow
1. **Preparation** – Load the page in a controlled environment (headless browser with DevTools Protocol). Set each viewport from the device matrix and enable emulated assistive‑technology settings (e.g., reduced motion, high contrast).  
2. **Keyboard & Focus audit** – Cycle through all interactive elements using `Tab`/`Shift+Tab`. Record any focus traps, missing focus outlines, or order violations. Verify that focus is programmatically moved to dynamic content (modals, alerts).  
3. **Semantic & Labeling check** – Inspect DOM for appropriate ARIA roles, `aria‑label`, `aria‑describedby`, and native HTML elements. Flag unlabeled controls, duplicate IDs, or ambiguous link text.  
4. **Colour contrast analysis** – Compute contrast ratios for text, icons, and UI components at each breakpoint using the WCAG 2.2 contrast algorithm. Highlight ratios below 3:1 for large text and 4.5:1 for normal text.  
5. **Zoom & Reflow test** – Apply browser zoom (up to 200 %) and CSS `@media (max-width)` breakpoints. Confirm that content does not overflow, that scrollbars appear only when necessary, and that layout remains logical.  
6. **Touch target verification** – Measure tap target dimensions against the 44 × 44 dp minimum. Record any targets that are too small or too closely spaced.  
7. **Status & Error communication** – Trigger form validation, loading spinners, and system messages. Verify that updates are announced to screen readers via live regions and that visual cues have corresponding ARIA attributes.  
8. **Reduced motion compliance** – Enable `prefers-reduced-motion` and ensure that animations, transitions, or auto‑scrolling are either removed or replaced with non‑animated alternatives.  
9. **Overflow & Orientation handling** – Rotate device orientation and test landscape/portrait layouts. Detect horizontal overflow, clipped content, or loss of focus visibility.  
10. **Reporting** – Compile findings in a structured JSON block, then render a human‑readable markdown summary. If the approval flag is `true`, append a remediation section with prioritized fixes and implementation hints.

### Output contract
- **`findings`**: array of objects, each containing `id`, `category` (e.g., Keyboard, Contrast), `description`, `severity` (Critical, High, Medium, Low), `breakpoint` (if applicable), and `evidence` (screenshot URL or DOM snippet).  
- **`recommendations`** (optional): array of objects with `id` (matching a finding), `suggestedFix`, `estimatedEffort`, and `reference` (WCAG criterion link).  
- **`summary`**: markdown section summarizing total issues by severity and category, plus a brief “next steps” paragraph.  
- **`metadata`**: audit timestamp, tool versions, device matrix, and input hash for reproducibility.

### Quality gate
- All findings must be reproducible in at least two distinct viewports.  
- Contrast calculations must use the sRGB luminance formula defined in WCAG 2.2.  
- No duplicate issue IDs; each issue must have a unique, deterministic identifier.  
- The report must pass JSON schema validation against the defined output contract.

### Safety constraints
- The skill must never modify live production code or submit data to external services without explicit user consent.  
- Sensitive user data (e.g., authentication tokens) must be redacted from any screenshots or logs.  
- The audit must respect `robots.txt` and any `X‑Robots‑Tag` directives; pages disallowed for crawling are skipped with a clear note.  
- All external libraries used for colour contrast or viewport emulation must be up‑to‑date and sourced from reputable package registries.
