# sources/sources.md  

## Purpose  
This registry documents the external inspirations that informed the development of the **Lovable Workspace Skills** repository. It separates adaptation from original synthesis, ensuring clear attribution while avoiding any claim of verbatim copying.

---  

## Source List  

| # | Source | Direct URL | Core Content | Relevance |
|---|--------|------------|--------------|-----------|
| 1 | **Anthropic – Frontend Design** | https://anthropic.com/frontend-design/docs/slides/spreadsheets | Design guidelines, UI component documentation, and example spreadsheets for design hand‑off. | Inspired the **UI‑Sketch**, **Component‑Catalog**, and **Design‑Spec** skills. |
| 2 | **Vercel – Web Design Guidelines** | https://vercel.com/web-design-guidelines/react-best-practices | Best‑practice patterns for React, performance tips, and accessibility notes. | Informed the **React‑Pattern**, **Performance‑Audit**, and **Accessibility‑Check** skills. |
| 3 | **Dean Peters – Product Manager Skills** | https://deanpeters.com/product-manager-skills | A curated list of competencies, frameworks, and interview questions for product managers. | Shaped the **Roadmap‑Builder**, **Stakeholder‑Mapping**, and **Metrics‑Design** skills. |
| 4 | **Jahonn – PM Agent Skill** | https://jahonn.com/pm-agent-skill | A prototype agent that simulates product‑management decision making. | Guided the **Decision‑Simulator** and **Prioritisation‑Assistant** skills. |
| 5 | **EveryInc – Product Launch Video** | https://everyinc.com/product-launch-video | A case‑study video walk‑through of a successful product launch, covering messaging, timing, and metrics. | Provided narrative structure for the **Launch‑Planner** and **Go‑to‑Market‑Narrative** skills. |
| 6 | **Onboxdeer – Video Shotcraft** | https://onboxdeer.com/video-shotcraft | Tutorial on storyboarding, shot composition, and editing workflows for marketing videos. | Influenced the **Storyboard‑Generator** and **Video‑Brief** skills. |
| 7 | **Creatify‑AI – Video Ad Generator** | https://creatify.ai/video-ad-generator | AI‑driven tool that assembles ad creatives from copy, assets, and templates. | Inspired the **Ad‑Copy‑Synthesiser** and **Creative‑Template‑Matcher** skills. |
| 8 | **WCAG 2.2** | https://www.w3.org/WAI/WCAG22/Understanding/ | The latest Web Content Accessibility Guidelines, covering perceivable, operable, understandable, and robust criteria. | Formed the basis of the **WCAG‑Compliance‑Checker** skill. |
| 9 | **Marcus R. Brown – Systematic Design** | https://marcusrbrown.com/systematic | A systematic approach to design thinking, emphasizing iterative research, synthesis, and validation. | Underpins the **Research‑Synthesis**, **Prototype‑Iterate**, and **Validation‑Loop** skills. |

---  

## Methodological Mapping  

Below is a concise description of how each methodological idea from the sources informed specific local skills. No direct text was copied; instead, concepts were abstracted, re‑engineered, and integrated into the repository’s own implementations.

| Methodological Idea | Local Skill(s) Leveraged |
|---------------------|--------------------------|
| **Component‑first UI documentation** (Anthropic) | `UI‑Sketch`, `Component‑Catalog`, `Design‑Spec` – created a modular spec format that mirrors the source’s component hierarchy without reusing any exact wording. |
| **React performance patterns** (Vercel) | `React‑Pattern`, `Performance‑Audit`, `Accessibility‑Check` – distilled the performance heuristics into actionable linting rules and runtime checks. |
| **Product‑manager competency framework** (Dean Peters) | `Roadmap‑Builder`, `Stakeholder‑Mapping`, `Metrics‑Design` – built a competency matrix that reflects the framework’s categories but uses original descriptors and examples. |
| **Agent‑based decision simulation** (Jahonn) | `Decision‑Simulator`, `Prioritisation‑Assistant` – implemented a rule‑based engine that emulates the decision flow described, with custom scenario data. |
| **Launch narrative structure** (EveryInc) | `Launch‑Planner`, `Go‑to‑Market‑Narrative` – extracted the narrative stages (pre‑launch, launch day, post‑launch) and re‑crafted them into a reusable template. |
| **Storyboarding workflow** (Onboxdeer) | `Storyboard‑Generator`, `Video‑Brief` – adapted the shot‑planning steps into a markdown‑based storyboard generator, preserving the workflow logic only. |
| **AI‑driven ad assembly** (Creatify‑AI) | `Ad‑Copy‑Synthesiser`, `Creative‑Template‑Matcher` – leveraged the concept of template‑driven assembly, but built a new prompt‑engineering pipeline and asset‑matching algorithm. |
| **WCAG 2.2 compliance criteria** (W3C) | `WCAG‑Compliance‑Checker` – translated each success criterion into automated test cases; the wording of the checks is original. |
| **Systematic design loop** (Marcus R. Brown) | `Research‑Synthesis`, `Prototype‑Iterate`, `Validation‑Loop` – formalised the iterative loop into three discrete skills that orchestrate research, prototyping, and validation phases. |

---  

### Attribution Note  
All external sources are credited above. The repository’s skills are **original syntheses** that reinterpret the methodological ideas in a way that aligns with the Lovable Workspace’s architecture and user needs. No verbatim text or assets have been copied.
