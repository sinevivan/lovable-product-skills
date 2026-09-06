# Landing Workflow  
*Repository: **Lovable Workspace Skills** – `workflows/landing-workflow.md`*  

---  

## Overview  

A **Russian‑language landing chain** that moves a concept from a brief to a production‑ready landing page. The workflow is linear but includes **gates** (review/approval checkpoints) and **stop conditions** (criteria that abort or loop back). All copy prompts are provided in a **copy‑ready** format ready for insertion into a content management system (CMS) or AI writer.

---  

## Table of Contents  

1. [Inputs & Brief](#1-inputs--brief)  
2. [Problem Definition](#2-problem-definition)  
3. [Competitive Evidence (Optional)](#3-competitive-evidence-optional)  
4. [Landing Conversion Architecture](#4-landing-conversion-architecture)  
5. [Copy / Content Gap Analysis](#5-copy--content-gap-analysis)  
6. [Design Directions (3 concepts)](#6-design-directions-3-concepts)  
7. [Hero + Proof Slice](#7-hero--proof-slice)  
8. [Approval Gate](#8-approval-gate)  
9. [Build & Development](#9-build--development)  
10. [Accessibility & UI Audit](#10-accessibility--ui-audit)  
11. [Gates & Stop Conditions Summary](#11-gates--stop-conditions-summary)  

---  

## 1. Inputs & Brief  

| Item | Description | Owner | Due |
|------|-------------|-------|-----|
| **Brief** | High‑level business goal, target persona, KPI (e.g., CVR ≥ 12 %) | Product Owner | Day 0 |
| **Stakeholder List** | Names, roles, contact channels | PM | Day 0 |
| **Brand Guidelines** | Tone, voice, visual assets | Brand Lead | Day 0 |
| **Technical Constraints** | CMS, headless, A/B testing tool | Tech Lead | Day 0 |

> **Copy‑Ready Prompt – Brief Extraction**  
> ```
> Сформулируй короткое описание продукта (≤ 30 слов), целевую аудиторию (2‑3 сегмента) и ключевую бизнес‑цель (конверсия, лиды, продажи). Используй данные из предоставленного брифа.
> ```

---  

## 2. Problem Definition  

1. **Research** – Interview 3‑5 target users, collect pain points.  
2. **Synthesize** – Write a 2‑sentence “Problem Statement”.  

> **Copy‑Ready Prompt – Problem Statement**  
> ```
> Опиши проблему целевой аудитории в 2‑3 предложениях, используя язык, характерный для русскоязычных пользователей. Включи конкретный контекст и эмоциональный отклик.
> ```

### Gate 1 – Problem Validation  

- **Pass**: ≥ 80 % of interviewed users confirm the problem.  
- **Fail / Stop**: < 60 % agreement → return to research.  

---  

## 3. Competitive Evidence (Optional)  

> **When to trigger** – If the brief mentions “highly competitive market” **or** the problem is generic.  

1. Identify 3‑5 top competitors.  
2. Extract headline, value proposition, and conversion hook.  
3. Create a **Competitive Evidence Matrix** (see template below).  

### Competitive Evidence Matrix  

| Competitor | Headline | Core Offer | Conversion Hook | Notable Gap |
|------------|----------|------------|----------------|-------------|
| … | … | … | … | … |

> **Copy‑Ready Prompt – Competitive Gap**  
> ```
> На основе таблицы конкурентного анализа сформулируй 2‑3 уникальных преимущества нашего продукта, которые решают выявленные пробелы у конкурентов.
> ```

---  

## 4. Landing Conversion Architecture  

| Block | Purpose | Primary KPI | Example Content |
|-------|---------|-------------|-----------------|
| Hero | Capture attention, state value | Click‑through | Headline, sub‑headline, CTA |
| Problem | Reinforce pain | Time on page | Short paragraph + icon |
| Solution | Show benefit | Scroll depth | 3‑column feature list |
| Social Proof | Build trust | Conversion | Testimonials, logos |
| CTA Block | Drive action | Click‑through | Button, form |
| FAQ | Reduce friction | Bounce rate | 4‑6 Q&A |

> **Copy‑Ready Prompt – Architecture Summary**  
> ```
> Составь короткое описание каждого блока посадочной страницы (не более 40 слов), указав цель блока и ключевой KPI.
> ```

---  

## 5. Copy / Content Gap Analysis  

1. **Map** existing copy (if any) to the architecture blocks.  
2. **Identify** missing pieces, tone mismatches, or regulatory gaps (e.g., GDPR, Russian advertising law).  

### Gap Checklist  

- [ ] Headline aligns with problem statement  
- [ ] CTA verb is action‑oriented (e.g., «Получить», «Начать»)  
- [ ] Legal disclaimer present where required  
- [ ] Localization: correct case, gender, and cultural references  

> **Copy‑Ready Prompt – Gap‑Fix Draft**  
> ```
> Для каждого выявленного пробела подготовь черновой вариант текста, соблюдая тон бренда и правила русского языка.
> ```

---  

## 6. Design Directions (3 concepts)  

| Concept | Visual Style | Key Color | Hero Layout | Unique Element |
|---------|--------------|-----------|------------|----------------|
| **A** | Minimalist | #0047AB (deep blue) | Full‑width image + headline overlay | Interactive scroll‑trigger |
| **B** | Warm & Friendly | #D94F0B (orange) | Split‑screen (image | text) | Hand‑drawn icons |
| **C** | Data‑Driven | #2E7D32 (green) | Card‑grid hero | Real‑time stats widget |

*Deliverables per concept:*  
- Wireframe (Figma link)  
- Mood board (image collage)  
- Copy skeleton (headlines, sub‑headlines)  

> **Copy‑Ready Prompt – Hero Headline per Concept**  
> ```
> Предложи 3 варианта заголовка для героя в стиле {Style}, учитывая проблему «{Problem Statement}» и целевую выгоду «{Core Benefit}». Каждый вариант ≤ 12 слов.
> ```

---  

## 7. Hero + Proof Slice  

**Hero Slice** – The first‑fold section that combines headline, sub‑headline, primary CTA, and a visual.  

**Proof Slice** – Directly below hero; includes:  
- 2‑3 short testimonials (name, role, photo)  
- Trust logos (partners, media)  
- Mini‑case metric (e.g., «Увеличил конверсию на 18 % за 30 дней»)  

> **Copy‑Ready Prompt – Proof Text**  
> ```
> Напиши 2‑3 коротких кейс‑стади (≤ 30 слов) с конкретными цифрами, подтверждающие эффективность продукта. Используй формат «{Клиент} достиг {результат} за {период}».
> ```

---  

## 8. Approval Gate  

| Reviewer | Scope | Deadline |
|----------|-------|----------|
| Product Owner | Business alignment, KPI | +2 дня после design concepts |
| Brand Lead | Tone, visual consistency | +1 день |
| Legal | Compliance, disclaimer | +1 день |
| UX Lead | Flow, accessibility basics | +1 день |

**Pass Criteria** – All reviewers sign off (✓) in the shared tracker.  

**Fail / Stop** – Any “✗” triggers a **Revision Loop** (return to the relevant step).  

---  

## 9. Build & Development  

1. **Component Library** – Use the repository’s UI‑kit (React + Tailwind).  
2. **CMS Integration** – Populate copy via JSON schema (`landingCopy.json`).  
3. **A/B Test Hooks** – Insert `data-test-id` attributes for each CTA block.  

> **Copy‑Ready Prompt – JSON Payload**  
> ```json
> {
>   "hero": {
>     "headline": "PLACEHOLDER",
>     "subheadline": "PLACEHOLDER",
>     "ctaText": "PLACEHOLDER",
>     "imageUrl": "PLACEHOLDER"
>   },
>   "proof": [
>     {
>       "quote": "PLACEHOLDER",
>       "author": "PLACEHOLDER",
>       "logoUrl": "PLACEHOLDER"
>     }
>   ]
> }
> ```

*Replace `PLACEHOLDER` with approved copy before push.*  

---  

## 10. Accessibility & UI Audit  

| Checklist Item | Standard | Tool | Pass Threshold |
|----------------|----------|------|-----------------|
| Text contrast | WCAG AA | axe‑core | Ratio ≥ 4.5:1 |
| Keyboard navigation | WCAG AA | Lighthouse | No focus traps |
| Alt text | WCAG AA | manual review | Descriptive, ≤ 125 chars |
| Language attribute | HTML5 | manual | `lang="ru"` on `<html>` |
| Form labels | WCAG AA | axe‑core | All inputs labeled |

**Audit Owner:** Accessibility Engineer  

- **Pass** → Deploy to staging.  
- **Fail** → Return to **Build** step with issue list.  

---  

## 11. Gates & Stop Conditions Summary  

| Gate | Entry Criteria | Exit Criteria | Stop Condition |
|------|----------------|---------------|----------------|
| **Gate 1 – Problem Validation** | Completed user interviews | ≥ 80 % agreement | < 60 % → re‑research |
| **Gate 2 – Competitive Evidence** (optional) | Market flagged as competitive | Matrix approved | Incomplete data → additional research |
| **Gate 3 – Architecture Review** | Completed copy gap analysis | All blocks mapped, KPI defined | Missing KPI → revisit architecture |
| **Gate 4 – Design Review** | 3 design concepts delivered | ≥ 2 concepts approved | All concepts rejected → redesign brief |
| **Gate 5 – Final Approval** | All reviewers signed off | All checkmarks ✓ | Any ✗ → revision loop |
| **Gate 6 – Accessibility Audit** | Staging build ready | All audit items passed | Any fail → back to Build |

---  

## Appendices  

### A. Template – Landing Copy JSON  

```json
{
  "hero": {
    "headline": "",
    "subheadline": "",
    "ctaText": "",
    "imageUrl": ""
  },
  "problem": {
    "title": "",
    "text": ""
  },
  "solution": {
    "features": [
      {"title": "", "description": ""},
      {"title": "", "description": ""},
      {"title": "", "description": ""}
    ]
  },
  "proof": [
    {
      "quote": "",
      "author": "",
      "role": "",
      "photoUrl": ""
    }
  ],
  "ctaBottom": {
    "text": "",
    "buttonLabel": ""
  },
  "faq": [
    {"question": "", "answer": ""},
    {"question": "", "answer": ""}
  ]
}
```

### B. Quick Reference – Copy‑Ready Prompt Library  

| Prompt ID | Use Case | Prompt (RU) |
|-----------|----------|-------------|
| **P‑BRIEF** | Extract brief | `Сформулируй короткое описание продукта...` |
| **P‑PROB** | Problem statement | `Опиши проблему целевой аудитории...` |
| **P‑COMP** | Competitive gap | `На основе таблицы конкурентного анализа...` |
| **P‑ARCH** | Architecture summary | `Составь короткое описание каждого блока...` |
| **P‑GAP** | Gap‑fix draft | `Для каждого выявленного пробела подготовь черновой вариант текста...` |
| **P‑HEAD** | Hero headline per concept | `Предложи 3 варианта заголовка для героя в стиле {Style}...` |
| **P‑PROOF** | Proof text | `Напиши 2‑3 коротких кейс‑стади...` |
| **P‑JSON** | JSON payload | *(see section 9)* |

---  

*End of `workflows/landing-workflow.md`*
