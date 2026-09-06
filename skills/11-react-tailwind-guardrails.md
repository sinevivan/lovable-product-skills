# Display Name
React Tailwind Guardrails

## Name
react-tailwind-guardrails

## Description
Inspect and enforce architecture, UI, performance, and security guardrails for React + TypeScript + Tailwind projects before or during substantial implementation.

## Instructions

### Objective
Provide a systematic, reproducible checklist that a developer or automation can run to validate that a React/TypeScript codebase using Tailwind CSS adheres to agreed‑upon standards for component boundaries, routing, state management, semantic HTML, responsive design, error handling, security, performance, dependency hygiene, file organization, and test coverage. The output should be a concise report highlighting compliance gaps, suggested remediation, and a clear handoff point to the implementation team.

### Use when
- Initiating a new feature branch that will introduce or modify many UI components.  
- Beginning a large‑scale refactor of existing screens, routes, or state logic.  
- Integrating a third‑party library that touches UI, data fetching, or routing.  
- A CI pipeline step that must verify guardrails before allowing a merge to `main`.  

### Do not use when
- The change is a trivial bug‑fix affecting a single line of code without UI impact.  
- The repository does not use Tailwind CSS or TypeScript.  
- The project is in a prototype stage where strict guardrails would impede rapid experimentation.  

### Required inputs
1. **Project root path** – absolute or relative path to the repository.  
2. **Configuration files** – locations of `tsconfig.json`, `tailwind.config.js`, and any custom ESLint/Prettier configs.  
3. **Feature manifest** – optional JSON describing new routes, pages, or components to be added (e.g., `{ "routes": ["/dashboard"], "components": ["UserCard"] }`).  
4. **Environment context** – target browsers, Node version, and CI environment variables (if any).  

### Workflow
1. **Initialize** – Load the project’s TypeScript program using the supplied `tsconfig.json`. Resolve Tailwind configuration and any custom PostCSS plugins.  
2. **Static analysis** –  
   - Parse the file tree to locate all `.tsx` files under `src/`.  
   - Identify exported React components, their prop types, and default exports.  
   - Detect route definitions (e.g., `react-router`, `next/router`, or custom route maps).  
   - Verify that each component resides in a folder that matches its domain (e.g., `src/components/ui/`, `src/pages/`).  
3. **Semantic HTML audit** – For each JSX element, ensure the use of appropriate semantic tags (`<header>`, `<nav>`, `<section>`, `<button>`, etc.) and that ARIA attributes are present where needed.  
4. **Tailwind compliance** –  
   - Run `tailwindcss`’s JIT compiler in “dry‑run” mode to catch unused or misspelled utilities.  
   - Enforce a responsive design matrix: every component must contain at least `sm:` and `md:` variants for layout‑critical utilities.  
   - Flag any `!important` usage or arbitrary values that bypass the design system.  
5. **State & data boundaries** –  
   - Detect usage of global state libraries (`Redux`, `Zustand`, `React Context`).  
   - Ensure that data fetching occurs in dedicated hooks (`useQuery`, `useEffect`) and that loading/error states are rendered.  
   - Confirm that components do not directly mutate props or external stores without a clear action creator.  
6. **Security checks** –  
   - Scan for dangerously set inner HTML (`dangerouslySetInnerHTML`).  
   - Validate that all external URLs are sanitized and that CSP‑compatible attributes are present.  
   - Verify that authentication‑protected routes are wrapped with appropriate guards.  
7. **Performance guardrails** –  
   - Flag components lacking `React.memo` or `useCallback` where prop stability is critical.  
   - Detect large bundle imports (e.g., whole `lodash` instead of specific functions).  
   - Ensure images use `next/image` or equivalent lazy‑loading patterns.  
8. **Dependency hygiene** – Compare `package.json` against an allowlist of approved versions; warn on outdated or vulnerable packages.  
9. **File plan & test matrix** – Generate a checklist that each new component must have: a `.test.tsx` file with at least one unit test, a Storybook story, and a corresponding CSS module (if not using Tailwind exclusively).  
10. **Report generation** – Assemble findings into a markdown summary with sections: *Compliant*, *Warnings*, *Errors*, and *Action Items*. Include line numbers and file paths for each issue.  

### Output contract
- **Type**: Markdown string (`string`).  
- **Structure**:  
  ```markdown
  ## Summary
  - Total components inspected: X
  - Pass rate: Y%
  
  ## Errors
  1. <file>:<line> – description
  
  ## Warnings
  1. <file>:<line> – description
  
  ## Action Items
  - [ ] Fix semantic HTML in `Header.tsx`
  - [ ] Add `sm:` breakpoint to `Card` component
  …
  ```  
- The output must be under 2 KB to fit typical CI comment limits.  

### Quality gate
- **Pass** only if *Errors* list is empty.  
- **Warning tolerance**: no more than 5 warnings; otherwise the run fails.  
- **Performance score**: must report a “bundle impact” ≤ 5 KB for any newly added dependency.  
- **Security score**: CVE count must be zero.  

### Safety constraints
- The guardrail script must never modify source files; it is read‑only.  
- All file system access is confined to the supplied project root; no traversal outside this directory.  
- Network calls are prohibited; dependency checks rely solely on the local `node_modules` and `package-lock.json`.  
- Sensitive data (e.g., environment secrets) are never logged or included in the report.  
- If the script encounters a parsing error that could corrupt the analysis, it aborts and returns a clear error message without partial results.
