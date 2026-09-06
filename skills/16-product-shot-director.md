# Display Name
Product Shot Director

## Name
product-shot-director

## Description
Transforms an approved storyboard into a set of 6–10 precise, model‑neutral product shots. Each shot specification includes purpose, duration, subject, environment, composition, camera/lens settings, movement, subject motion, lighting, first and last frame details, transition notes, continuity anchors, positive and negative prompt constraints, feasibility assessment, and fallback options. The output is ready for downstream rendering pipelines or human artists.

**Auto‑trigger**: When a storyboard receives final approval, generate a complete shot list for product visualization.

## Instructions

### Objective
Create a comprehensive, production‑ready shot list that captures every visual intent of the approved storyboard while remaining neutral to any specific 3D model or rendering engine. The list must be detailed enough for a cinematographer, VFX supervisor, or AI‑image generator to execute without additional clarification.

### Use when
- A storyboard has been signed off by product, marketing, and legal teams.  
- The project requires a clear, model‑agnostic visual plan before asset creation.  
- Multiple downstream teams (rendering, animation, photography) need a single source of truth for shot composition.

### Do not use when
- The storyboard is still under review or contains unresolved creative comments.  
- Specific hardware, lenses, or software constraints have already been mandated.  
- The product is a purely abstract concept that does not map to physical shots.

### Required inputs
1. **Approved storyboard JSON** – an ordered array of scenes, each with:  
   - `scene_id`  
   - `purpose` (e.g., highlight feature, convey lifestyle)  
   - `duration_seconds`  
   - `subject_description` (product name, key attributes)  
   - `environment_description` (studio, outdoor, props)  
   - `key_composition_notes` (rule of thirds, focal point)  
2. **Brand style guide** – tone, color palette, and any prohibited visual elements.  
3. **Technical constraints** – maximum shot length, resolution, and allowed camera rigs.  
4. **Fallback preferences** – simplified lighting or static camera options if feasibility is low.

### Workflow
1. **Parse storyboard** – read each scene in order, validate required fields, and assign a sequential shot number.  
2. **Derive shot count** – split scenes into 6–10 shots based on duration thresholds (≤ 3 s → single shot, > 3 s → split).  
3. **Define shot template** – for each shot populate:  
   - **Purpose & Duration** – concise statement and exact time.  
   - **Subject & Environment** – model‑neutral descriptors (e.g., “sleek metallic gadget on matte black surface”).  
   - **Composition** – camera angle, framing, rule of thirds, depth cues.  
   - **Camera & Lens** – focal length range, aperture, sensor size, movement type (pan, dolly, static).  
   - **Subject Motion** – rotation, translation, or deformation details.  
   - **Lighting** – key, fill, rim, temperature, soft‑box placement, HDRI usage.  
   - **First/Last Frame** – visual anchor description for continuity.  
   - **Transition** – cut, dissolve, match‑move note.  
   - **Continuity Anchors** – objects or lighting cues that persist across shots.  
   - **Prompt Constraints** – positive keywords (e.g., “high‑gloss finish”) and negative keywords (e.g., “no reflections”).  
   - **Feasibility Score** – 1‑5 rating based on technical constraints.  
   - **Fallback Plan** – alternative lighting or static camera if score ≤ 2.  
4. **Validate against brand guide** – flag any prohibited colors or motifs.  
5. **Generate output JSON** – an ordered list of shot objects matching the schema defined in the “Output contract”.  
6. **Review handoff** – attach a concise handoff note for the rendering team, summarizing critical continuity and fallback decisions.

### Output contract
```json
[
  {
    "shot_number": 1,
    "purpose": "Highlight product silhouette",
    "duration_seconds": 2.5,
    "subject": "generic sleek device, matte black finish",
    "environment": "studio with seamless white backdrop",
    "composition": "45° angle, centered, shallow depth of field",
    "camera": {
      "type": "digital cinema",
      "sensor": "full‑frame",
      "lens_focal_mm": "35‑50",
      "aperture": "f/2.8",
      "movement": "static"
    },
    "subject_motion": "slow clockwise rotation 15°",
    "lighting": {
      "key": "softbox left 45°, 5500K",
      "fill": "bounce panel right, 30% intensity",
      "rim": "backlight behind product, subtle"
    },
    "first_frame": "product front‑left edge in focus",
    "last_frame": "product rear‑right edge in focus",
    "transition": "hard cut to shot 2",
    "continuity_anchors": ["light temperature 5500K", "white backdrop"],
    "prompt_positive": ["high gloss", "clean edges"],
    "prompt_negative": ["glare", "shadow artifacts"],
    "feasibility_score": 5,
    "fallback": null
  },
  ...
]
```
The JSON array must contain one object per shot, ordered by `shot_number`. All fields are mandatory except `fallback` when not needed.

### Quality gate
- **Completeness**: Every storyboard scene is represented; total shot count between 6 and 10.  
- **Clarity**: Each field is a single sentence or structured value; no ambiguous language.  
- **Brand compliance**: Zero violations of the brand style guide (automated check).  
- **Feasibility**: Minimum feasibility score of 3; any shot below 3 must have a documented fallback.  
- **Continuity**: At least one continuity anchor shared between consecutive shots.

### Safety constraints
- Do not include any copyrighted brand assets, proprietary model names, or location identifiers.  
- Exclude any prompt terms that could generate disallowed content (e.g., “nudity”, “violence”).  
- Ensure lighting descriptions never suggest hazardous setups (e.g., “open flame”).  
- All generated text must be free of personally identifiable information (PII).
