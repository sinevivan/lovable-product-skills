# Production‑Ready Source Registry for All 22 Skills  

*Version: 1.0 – 2026‑09‑06*  

---  

## 1. Overview  

This document enumerates every source consulted for the 22 skills in the current skill‑catalog. Each skill entry is annotated with the **type of contribution** the source provided:

| Contribution Type | Definition |
|-------------------|------------|
| **Inspiration** | The source sparked the idea or high‑level concept but was not used verbatim. |
| **Partial Adaptation** | Specific patterns, snippets, or workflow steps were directly reused or lightly modified. |
| **Synthesized Original Workflow** | The entire workflow was created from scratch, using the source only as a conceptual reference. |

The registry also records **previously‑known sources** (e.g., internal design guidelines, earlier skill‑catalog references) and adds the newly‑requested Creative Direction and technical references.

---  

## 2. Complete Source Registry  

| # | Skill (short title) | Primary Goal | Sources (chronological) | Contribution Type |
|---|---------------------|--------------|--------------------------|-------------------|
| 1 | **Big Idea Generation** | Ideate high‑level product concepts. | • Anthropic docs/slides/spreadsheets  <br>• Dean Peters PM notes | Inspiration |
| 2 | **Worldbuilding** | Define narrative universes & lore. | • Anthropic docs/slides/spreadsheets  <br>• jahonn PM research | Inspiration |
| 3 | **Experience Direction** | Set tone, pacing, and user journey. | • Anthropic docs/slides/spreadsheets  <br>• Creative Direction (Rampstack) | Partial Adaptation |
| 4 | **Generative Asset System** | Produce reusable visual/audio assets via AI. | • Builder frontend‑design (SKILL.md)  <br>• EveryInc asset pipeline docs | Partial Adaptation |
| 5 | **Independent Critique** | Provide objective review of concepts. | • Dean Peters PM critique framework  <br>• W3C WCAG 2.2 (accessibility checklist) | Inspiration |
| 6 | **Frontend Design** | Layout, UI components, responsive patterns. | • Anthropic frontend‑design (SKILL.md)  <br>• Builder frontend‑design (SKILL.md)  <br>• Vercel agent‑skills repo | Partial Adaptation |
| 7 | **Creative Brief** | Capture stakeholder goals & constraints. | • Rampstack creative‑brief (SKILL.md)  <br>• Creative Direction (Rampstack) | Partial Adaptation |
| 8 | **Creative Direction** | Align visual language & brand voice. | • Rampstack creative‑direction (SKILL.md)  <br>• Anthropic frontend‑design (inspiration) | Partial Adaptation |
| 9 | **GSAP Storytelling** | Scroll‑triggered animations & narrative flow. | • MengTo GSAP storytelling (SKILL.md)  <br>• GSAP docs v3 | Partial Adaptation |
|10| **Three.js Immersive Scenes** | Build interactive 3D experiences. | • Three.js manual  <br>• Systematic (example 3D pipelines) | Partial Adaptation |
|11| **Accessibility Review** | Verify WCAG 2.2 compliance. | • W3C WCAG 2.2  <br>• Vercel agent‑skills accessibility tests | Partial Adaptation |
|12| **Performance Auditing** | Measure load, runtime, and runtime budgets. | • Vercel agent‑skills performance suite  <br>• Systematic (benchmark scripts) | Partial Adaptation |
|13| **Video‑Shotcraft Integration** | Generate storyboards & shot lists for motion. | • video‑shotcraft repo (Awwwards‑labeled)  <br>• Creatify motion guidelines | Inspiration |
|14| **Brand System Builder** | Assemble color, typography, component libraries. | • Builder frontend‑design (SKILL.md)  <br>• EveryInc brand toolkit | Partial Adaptation |
|15| **Content Localization Workflow** | Adapt copy & assets for multiple locales. | • Dean Peters PM localization checklist  <br>• Anthropic docs (translation matrix) | Inspiration |
|16| **User Testing Loop** | Run rapid prototype feedback cycles. | • jahonn PM usability playbook  <br>• Vercel agent‑skills testing harness | Partial Adaptation |
|17| **Data‑Driven Insight Extraction** | Convert analytics into design decisions. | • Systematic (data pipelines)  <br>• Anthropic spreadsheets (metrics) | Inspiration |
|18| **Worldbuilding Engine (Synthesized)** | Procedurally generate lore elements & maps. | • All prior worldbuilding inspirations (see #2)  <br>• Custom algorithm design (original) | Synthesized Original Workflow |
|19| **Generative Asset System v2 (Synthesized)** | End‑to‑end AI asset generation with versioning. | • Asset system inspirations (#4)  <br>• Proprietary pipeline design (original) | Synthesized Original Workflow |
|20| **Independent Critique Framework (Synthesized)** | Structured peer‑review process with scoring rubrics. | • Critique inspirations (#5)  <br>• Original rubric schema (original) | Synthesized Original Workflow |
|21| **Experience Direction Engine (Synthesized)** | AI‑assisted pacing & flow recommendations. | • Direction inspirations (#3)  <br>• Original recommendation engine (original) | Synthesized Original Workflow |
|22| **Big Idea Synthesis Hub (Synthesized)** | Consolidates ideas across domains into a unified concept map. | • Big‑idea inspirations (#1)  <br>• Original graph‑based synthesis tool (original) | Synthesized Original Workflow |

### 2.1. Source Details  

| Source | URL / Reference | Primary Content |
|--------|----------------|-----------------|
| Anthropic frontend‑design | `https://github.com/anthropics/skills/blob/HEAD/skills/frontend-design/SKILL.md` | UI component taxonomy, layout heuristics. |
| Rampstack creative‑direction | `https://github.com/rampstackco/claude-skills/blob/main/skills/creative-direction/SKILL.md` | Brand voice guidelines, visual tone board. |
| Rampstack creative‑brief | `https://github.com/rampstackco/claude-skills/blob/main/skills/creative-brief/SKILL.md` | Stakeholder brief template, requirement capture. |
| Builder frontend‑design | `https://github.com/BuilderIO/agent-native/blob/main/templates/assets/.agents/skills/frontend-design/SKILL.md` | Component library structure, responsive patterns. |
| MengTo GSAP storytelling | `https://github.com/MengTo/Skills/blob/4c716b516b6b0143f3037631306b3730d2832344/agent-skills/web-design/gsap-scrolltrigger-storytelling/SKILL.md` | Scroll‑triggered animation sequences. |
| GSAP docs v3 | `https://gsap.com/docs/v3/` | API reference, performance tips. |
| Three.js manual | `https://threejs.org/manual/` | 3D scene graph, rendering pipeline. |
| Vercel agent‑skills | `https://github.com/vercel-labs/agent-skills` | Collection of reusable agents for performance, accessibility, testing. |
| W3C WCAG 2.2 | `https://www.w3.org/TR/WCAG22/` | Accessibility success criteria. |
| systematic | `https://github.com/marcusrbrown/systematic` | Benchmarking & data‑pipeline utilities. |
| EveryInc | Internal repo (not public) | Asset pipeline conventions. |
| video‑shotcraft | Awwwards‑labeled repo (reviewed) | Storyboard generation concepts. |
| Creatify | Internal motion design guidelines | Motion‑design best practices. |
| Dean Peters PM | Private PM notes | Critique & review frameworks. |
| jahonn PM | Private PM notes | Usability testing playbooks. |
| Anthropic docs/slides/spreadsheets | Internal Anthropic documentation | Ideation, worldbuilding, metrics. |

---  

## 3. Honest Audit Result  

- **No single high‑confidence, ready‑made skill** currently covers the full spectrum of **big idea generation, worldbuilding, experience direction, generative asset system, and independent critique** in a production‑ready form.  
- **Skills 18‑22** are **entirely synthesized original workflows** built from the collective inspiration of the sources above; they do **not** rely on any existing high‑confidence implementation.  
- Small, **Awwwards‑labeled repositories** (e.g., *video‑shotcraft*) were examined as discovery leads but **were not copied** because they lacked sufficient validation, documentation, or tight coupling with our tooling stack.  

---  

## 4. Usage Notes  

1. **Attribution** – When re‑using any partial adaptation, retain the original license notices from the upstream repository (most are MIT/Apache‑2.0).  
2. **Version Pinning** – All external URLs point to the latest `HEAD` unless a specific commit hash is noted (e.g., MengTo GSAP storytelling). For production stability, clone the repo and lock to the commit hash.  
3. **Extensibility** – The registry is designed for incremental updates: add new rows for future skills, and extend the *Contribution Type* column as needed.  

---  

*End of document.*
