# Display Name
UI Critique Release Gate

## Name
ui-critique-release-gate

## Description
A post‑build evaluation that reviews the visual hierarchy, composition, consistency, content fidelity, real‑state representation, responsiveness, accessibility, performance symptoms, and overall polish of a UI release. The skill produces a severity‑rated critique, evidence excerpts, a minimal remediation plan, and a release recommendation, ensuring that no UI regression slips into production.

## Auto‑trigger
When a build artifact containing UI assets is published to the staging environment, automatically run the UI Critique Release Gate.

## Instructions

### Objective
Validate that the newly built UI meets the organization’s visual, functional, and performance standards before it is approved for release. The output must identify issues, rank them by severity, provide concrete evidence (screenshots, logs, metrics), propose the smallest feasible fix, and deliver a clear release recommendation (Approve, Conditional, or Reject).

### Use when
- A UI component library, feature branch, or full‑application build has been deployed to a staging environment.
- The design system version has been updated and needs verification against the latest UI.
- Release managers require an independent, structured gate to certify UI quality before production rollout.

### Do not use when
- The build only contains backend services with no UI artifacts.
- Preliminary design mockups are being reviewed; this skill expects rendered UI, not static wireframes.
- The project is in an early prototype phase where visual polish is intentionally incomplete.

### Required inputs
1. **Staging URL** – Fully qualified HTTPS address of the deployed UI.
2. **Design System Reference** – Versioned design tokens, component specifications, and accessibility guidelines.
3. **Performance Baseline** – Expected frame‑rate, load‑time, and memory‑usage thresholds for the target platform.
4. **Issue Tracker Endpoint** – API token and project ID for automatically filing remediation tickets.
5. **Stakeholder List** – Names and roles (e.g., UI Designer, QA Engineer, Release Manager) for notification routing.

### Workflow
1. **Discovery** – Crawl the staging URL, capture screenshots of all responsive breakpoints, and record DOM snapshots.
2. **Visual Analysis** – Compare captured visuals against the Design System Reference using pixel‑diff and layout‑diff algorithms. Flag hierarchy violations, misaligned composition, and inconsistent styling.
3. **Functional Verification** – Exercise interactive states (hover, focus, active, disabled, error) to ensure real‑state representation matches specifications.
4. **Accessibility Scan** – Run automated WCAG 2.2 checks (color contrast, ARIA attributes, keyboard navigation) and record violations.
5. **Performance Audit** – Execute Lighthouse‑style metrics, capture FPS, TTI, and memory spikes, and compare against the Performance Baseline.
6. **Evidence Collation** – For each detected issue, attach the offending screenshot, diff overlay, and relevant log snippet.
7. **Severity Assignment** – Apply a three‑tier scale (Critical, Major, Minor) based on impact on user experience, compliance, and performance.
8. **Remediation Planning** – Generate the smallest actionable fix (e.g., “adjust token $primary‑color to #0066CC”, “add aria‑label to button XYZ”).
9. **Release Recommendation** – Synthesize findings into a single decision:
   - **Approve** – No Critical issues, all Minor issues have clear fixes.
   - **Conditional** – One or more Major issues with documented mitigation paths.
   - **Reject** – Any Critical issue or performance symptom exceeding thresholds.
10. **Handoff** – Create tickets in the Issue Tracker, assign to the responsible role (UI Designer for visual/consistency, QA Engineer for functional/accessibility, Performance Engineer for performance), and email the Release Manager with the full report.

### Output contract
- **Report (Markdown)** – Structured sections mirroring the workflow, each issue listed with severity, evidence (embedded image links), remediation plan, and owner.
- **Summary Table** – Columns: Issue ID, Category, Severity, Owner, Status (Open/Closed).
- **Release Decision** – Plain‑text line: `Decision: Approve | Conditional | Reject`.
- **Artifacts** – ZIP archive containing all screenshots, diff overlays, and raw performance logs.

### Quality gate
- All Critical issues must be resolved before the report can emit an “Approve” decision.
- No more than two Major issues may remain unmitigated for a “Conditional” decision.
- Accessibility score must be ≥ 90 % (WCAG AA compliance) for any non‑reject outcome.
- Performance metrics must stay within 10 % of the baseline for FPS and TTI.

### Safety constraints
- Do not modify any production data; all interactions are read‑only.
- Do not store screenshots or logs longer than 30 days; purge after the release decision is logged.
- Ensure that any generated tickets do not contain sensitive user data; strip PII from logs before attachment.
- Respect rate limits of the Issue Tracker API; back‑off on HTTP 429 responses.
