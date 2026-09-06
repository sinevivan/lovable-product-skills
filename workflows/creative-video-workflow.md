# Creative Video Workflow  
**Path:** `workflows/creative-video-workflow.md`  

---

## Overview  

A Russian‑language image/video creative pipeline that moves from **offer/evidence** through **performance hypotheses**, **storyboard**, **shot direction**, **generation batches**, **selection/iteration**, and finally **channel adaptations**. The workflow is gated by continuity rules, explicit stop conditions, and reusable prompts to ensure consistency, quality, and rapid iteration.

---  

## Table of Contents  

1. [Stage 0 – Intake & Evidence](#stage-0)  
2. [Stage 1 – Performance Creative Hypotheses / Launch Narrative](#stage-1)  
3. [Stage 2 – Storyboard Development](#stage-2)  
4. [Stage 3 – Shot Direction & Asset Specification](#stage-3)  
5. [Stage 4 – Generation Batches](#stage-4)  
6. [Stage 5 – Selection & Iteration](#stage-5)  
7. [Stage 6 – Channel Adaptations](#stage-6)  
8. [Continuity Rules & Global Gates](#continuity-rules)  
9. [Stop Conditions](#stop-conditions)  
10. [Prompt Library](#prompt-library)  

---  

## Stage 0 – Intake & Evidence <a name="stage-0"></a>  

| Input | Required Format | Owner |
|-------|----------------|-------|
| **Offer / Product brief** | 1‑2 paragraph description, target KPI, unique selling points (USPs) | Product Owner |
| **Evidence assets** | Links to research, testimonials, stats, visual assets (PNG/JPG) | Marketing Analyst |
| **Audience persona** | Persona name, demographics, psychographics, pain points | UX Researcher |
| **Compliance checklist** | List of mandatory legal/brand constraints (e.g., “no direct price mention”) | Legal |

**Gate:** All fields must be populated and pass the **Compliance Validation** script (see Continuity Rules).  

---  

## Stage 1 – Performance Creative Hypotheses / Launch Narrative <a name="stage-1"></a>  

**Goal:** Generate 3‑5 high‑level creative hypotheses that explain *how* the offer will achieve the KPI for the target audience.  

### Steps  

1. Run **Hypothesis Prompt** (see Prompt Library).  
2. Review each hypothesis for:  
   - Alignment with USPs  
   - Emotional resonance (e.g., “гордость”, “безопасность”)  
   - Measurable KPI impact (e.g., “CTR ↑ 15 %”)  
3. Select **2** hypotheses to advance.  

**Gate:** Must have at least one *emotional* and one *rational* hypothesis.  

---  

## Stage 2 – Storyboard Development <a name="stage-2"></a>  

**Goal:** Translate each selected hypothesis into a 6‑panel storyboard (visual + copy).  

### Deliverables  

| Panel | Content | Format |
|-------|---------|--------|
| 1 | Hook (visual + 1‑sentence hook) | Sketch + Russian copy |
| 2‑5 | Narrative beats (problem → solution → benefit) | Sketch + copy |
| 6 | Call‑to‑Action (CTA) | Sketch + copy |

### Process  

1. Use **Storyboard Prompt** for each hypothesis.  
2. Sketches can be hand‑drawn, AI‑generated, or a combination.  
3. Store assets in `assets/storyboards/<hypothesis-id>/`.  

**Gate:** All panels must contain **continuous visual language** (color palette, typography) defined in the *Brand Guide* (see Continuity Rules).  

---  

## Stage 3 – Shot Direction & Asset Specification <a name="stage-3"></a>  

**Goal:** Produce a detailed shot list and asset spec sheet for downstream generation.  

### Shot List Template  

| Shot # | Description | Duration (s) | Camera movement | Audio cue | Visual style |
|--------|-------------|--------------|-----------------|----------|--------------|
| 1 | Opening hook – product in hand | 2 | Slow dolly in | Soft synth pad | Warm, high‑contrast |
| … | … | … | … | … | … |

### Asset Spec Sheet  

| Asset Type | Resolution | Aspect Ratio | Format | Prompt (if AI‑generated) |
|------------|------------|--------------|--------|---------------------------|
| Background image | 1920×1080 | 16:9 | PNG | *Background Prompt* |
| Character illustration | 1080×1080 | 1:1 | PNG | *Character Prompt* |
| Motion graphic overlay | 1920×1080 | 16:9 | MP4 (transparent) | *Overlay Prompt* |

**Gate:** All shot durations must sum to ≤ **30 seconds** (or the length defined in the KPI).  

---  

## Stage 4 – Generation Batches <a name="stage-4"></a>  

**Goal:** Produce multiple AI‑generated video/audio/image variants for each shot.  

### Batch Configuration  

| Batch ID | Model | Parameters | Number of Variants |
|----------|-------|------------|--------------------|
| B1 | Stable Diffusion XL | CFG = 7, Steps = 30 | 5 per visual asset |
| B2 | Runway Gen‑2 (video) | CFG = 8, FPS = 24 | 3 per shot |
| B3 | Whisper (audio) | Language = ru | 2 voice‑over styles |

### Execution  

1. Run the **Generation Prompt** (see Prompt Library) for each asset.  
2. Store outputs in `outputs/batch/<batch-id>/`.  

**Gate:** Automatic quality filter (blur detection, audio clipping) must pass ≥ 80 % of variants.  

---  

## Stage 5 – Selection & Iteration <a name="stage-5"></a>  

**Goal:** Choose the best assets, iterate where needed, and assemble the final cut.  

### Selection Process  

| Criterion | Weight |
|-----------|--------|
| Visual fidelity | 30 % |
| Narrative clarity | 25 % |
| Emotional impact (measured via pilot survey) | 20 % |
| Brand compliance | 15 % |
| Technical quality (no artifacts) | 10 % |

1. Conduct a **Rapid Review** with a cross‑functional panel (Creative Lead, Data Analyst, Legal).  
2. Score each variant using the matrix above.  
3. Select top‑scoring assets; flag any failing criteria for **re‑generation**.  

### Iteration Loop  

- **Re‑generation**: Adjust prompt parameters (e.g., increase CFG, change seed) and re‑run Batch step.  
- **Limit**: Maximum **2** iteration cycles per asset.  

**Gate:** Final assembled video must achieve a **pre‑test KPI** (e.g., predicted CTR ≥ 12 %) from the internal model.  

---  

## Stage 6 – Channel Adaptations <a name="stage-6"></a>  

**Goal:** Tailor the master video to each distribution channel (VK, TikTok, YouTube Shorts, Instagram Reels).  

### Adaptation Checklist  

| Channel | Duration | Aspect Ratio | Caption length | CTA format |
|---------|----------|--------------|----------------|------------|
| VK | ≤ 15 s | 1:1 | ≤ 150 chars | Button |
| TikTok | ≤ 60 s | 9:16 | ≤ 100 chars | Swipe‑up |
| YouTube Shorts | ≤ 60 s | 9:16 | ≤ 100 chars | End‑screen |
| Instagram Reels | ≤ 30 s | 9:16 | ≤ 125 chars | Link sticker |

### Steps  

1. Trim / re‑order shots to meet duration limits.  
2. Re‑encode using channel‑specific codecs (H.264, AAC).  
3. Localize captions using **Caption Prompt** (see Prompt Library).  
4. Export to `deliverables/<channel>/`.  

**Gate:** Each channel file must pass the **Channel Validator** (duration, aspect ratio, file size).  

---  

## Continuity Rules & Global Gates <a name="continuity-rules"></a>  

| Rule | Description | Enforcement Tool |
|------|-------------|-------------------|
| **Brand Palette** | All visual assets must use the approved hex codes from `brand/guide.json`. | Automated color‑check script |
| **Typography** | Headline font = **Montserrat Bold**, body = **Roboto Regular**. | PDF‑font‑audit |
| **Tone of Voice** | Russian copy must follow the “Warm‑Professional” style guide (no slang, no excessive exclamation). | Linguistic validator (RU‑NLP) |
| **Legal Compliance** | No mention of price, no comparative claims unless approved. | Legal compliance API |
| **Versioning** | Every asset file name includes `v{major}.{minor}`; increment minor on each iteration. | CI version hook |
| **Metadata** | All exported videos carry `title`, `description`, `tags`, and `language=ru` in the file metadata. | ffmpeg metadata injector |

**Global Gate:** The workflow cannot progress to the next stage until **all** applicable continuity checks return *PASS*.  

---  

## Stop Conditions <a name="stop-conditions"></a>  

1. **Compliance Fail** – Any legal or brand violation → abort and return to Stage 0.  
2. **KPI Threshold Not Met** – Predicted KPI < target after Stage 5 → abort and request new hypotheses.  
3. **Iteration Limit Exceeded** – More than 2 re‑generation cycles for a single asset → abort and flag for creative redesign.  
4. **Resource Exhaustion** – Compute budget exceeded (e.g., > $500 per video) → abort and renegotiate scope.  

---  

## Prompt Library <a name="prompt-library"></a>  

### 1. Hypothesis Prompt  

```
Ты – креатив‑стратег. На основе следующего оффера и доказательств создай 3‑5 креативных гипотез, каждая в виде:
1) Краткое название (≤ 8 слов)
2) Эмоциональная/рациональная точка роста
3) Ожидаемый KPI‑эффект (в %)
Ограничения: использовать только данные из оффера, избегать прямых ценовых упоминаний, язык – русский, стиль – «тёплый‑профессиональный».
```

### 2. Storyboard Prompt  

```
Для гипотезы «{hypothesis_title}» создай 6‑панельный раскадровочный план.
Каждая панель:
- Краткое визуальное описание (≤ 30 слов)
- Текстовый копирайт (один короткий слоган, ≤ 12 слов)
- Указание цвета/стиля (из бренд‑гайда)
Вывод в формате таблицы Markdown.
```

### 3. Shot Direction Prompt  

```
Исходя из раскадровки, опиши каждый кадр:
- Действие камеры (долли, панорамирование, статичный)
- Длительность в секундах
- Аудио‑подсказка (звуковой эффект, музыка)
- Технические параметры (разрешение, FPS)
```

### 4. Generation Prompt (Visual)  

```
Создай изображение в стиле «{style_description}», используя палитру {palette_codes}.
Тема: {scene_description}.  
Требования: 1920×1080, PNG, без водяных знаков, максимальная чёткость.
```

### 5. Generation Prompt (Video)  

```
Сгенерируй короткое видео (≤ {duration}s) в разрешении 1920×1080, 24 fps.
Сценарий: {shot_description}.  
Тон: «{tone}», цветовая схема: {palette_codes}.  
Убедись, что нет артефактов и звук синхронен.
```

### 6. Caption Prompt (Channel Adaptation)  

```
Перепиши основной копирайт для {channel} (max {char_limit} символов).  
Тон: «тёплый‑профессиональный», включи CTA «{cta_text}».  
Не превышай лимит, не используйте эмодзи, сохраняй ключевые USP.
```

---  

**End of Document**
