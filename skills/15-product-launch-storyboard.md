# Display Name
Product Launch Storyboard Generator

## Name
product-launch-storyboard

## Description
Generate a model‑neutral video narrative storyboard from an approved product launch brief, detailing audience/action, thesis, beats, scenes, timing, UI/product proof, asset list, captions, aspect ratios, continuity, first/last frames, and a production handoff package.

## Instructions

### Objective
Transform a vetted product launch brief into a comprehensive, production‑ready storyboard that can be handed off to visual designers, animators, and video editors without any reference to specific AI models or rendering tools. The output must be a clear, sequential document that defines every narrative beat, visual cue, timing estimate, and asset requirement, enabling a multidisciplinary team to produce a polished launch video.

### Use when
- A product marketing team has completed an approved launch brief and needs a concrete visual plan for a launch video.  
- The project requires a neutral, tool‑agnostic storyboard that can be consumed by any creative vendor or internal studio.  
- The launch timeline includes a defined deadline for storyboard approval before production begins.

### Do not use when
- The launch brief is still under review or contains unapproved messaging.  
- The video concept relies on proprietary AI‑generated visuals that must be embedded in the storyboard.  
- The intended deliverable is a static infographic or a non‑video asset; this skill is strictly for video narrative storyboards.

### Required inputs
1. **Launch Brief** – Full text of the approved brief, including target audience, key messaging, product features, and desired call‑to‑action.  
2. **Brand Guidelines** – Color palette, typography, logo usage, and tone of voice specifications.  
3. **Desired Video Length** – Total runtime in seconds (e.g., 90 s).  
4. **Target Platforms** – List of platforms (YouTube, Instagram Reels, LinkedIn, etc.) with associated aspect ratios.  
5. **Asset Inventory** – Existing assets (product screenshots, UI mockups, B‑roll footage) and any gaps that need creation.  
6. **Production Timeline** – Key milestones (storyboard review, asset creation, edit lock).

### Workflow
1. **Brief Ingestion** – Parse the launch brief to extract audience persona, core thesis, and primary value propositions.  
2. **Narrative Structuring** – Draft a three‑act structure: Hook (0‑15 s), Value Demonstration (15‑70 s), Call‑to‑Action (70‑90 s).  
3. **Beat Definition** – Break each act into 4‑6 beats, assigning a concise headline, visual description, and timing window (e.g., “Beat 2 – Feature Highlight: 22‑30 s”).  
4. **Scene Blueprint** – For each beat, create a scene entry containing:  
   - **Scene ID** (e.g., S02)  
   - **Shot Type** (wide, close‑up, split‑screen)  
   - **Visual Elements** (UI mockup, product prototype, on‑screen graphics)  
   - **Audio Cue** (voice‑over line, music cue, sound effect)  
   - **Caption Text** (closed‑caption wording)  
   - **Duration** (seconds)  
   - **Aspect Ratio** (based on target platform)  
5. **Asset Mapping** – Cross‑reference each visual element with the Asset Inventory, marking “Existing” or “To‑Create”. Provide a brief specification for new assets (resolution, format, style).  
6. **Continuity Check** – Verify visual and narrative flow, ensuring consistent branding, color usage, and logical progression from first to last frame.  
7. **Production Handoff Package** – Compile:  
   - **Storyboard PDF** (scene table + thumbnail sketches)  
   - **Narrative Script** (voice‑over text)  
   - **Asset Request List** (detailed specs for missing assets)  
   - **Timing Sheet** (cumulative timestamps for each scene)  
   - **Review Checklist** (approval gates for script, visual, and asset completeness).  

### Output contract
- **File Format**: Markdown document plus an optional attached CSV of the scene table.  
- **Structure**: Header sections as defined above, followed by a **Storyboard Table** (Markdown table) listing all scenes with columns: Scene ID, Beat, Duration, Visual, Audio, Caption, Asset Status, Aspect Ratio.  
- **Deliverables**: A concise narrative script, a complete asset map, and a clear handoff checklist. No rendering commands, vendor APIs, or model‑specific instructions are included.  

### Quality gate
1. **Narrative Coherence** – Each beat must logically follow the previous one and reinforce the core thesis.  
2. **Timing Accuracy** – Sum of scene durations must equal the Desired Video Length ± 2 seconds.  
3. **Brand Alignment** – All visual descriptors must reference the Brand Guidelines; any deviation triggers a review flag.  
4. **Asset Completeness** – No “To‑Create” entry may lack a specification; missing specs cause the output to be rejected.  
5. **Platform Compliance** – Aspect ratios must match the Target Platforms list; mismatches are flagged for correction.

### Safety constraints
- Do not embed copyrighted third‑party media; only reference assets that are owned or cleared by the client.  
- Avoid disclosing any confidential product details beyond what is present in the approved launch brief.  
- Ensure all caption text complies with accessibility standards (e.g., WCAG 2.1 AA).  
- Do not generate any executable code, shell commands, or external service calls.  
- Maintain a neutral tone; do not insert promotional language that is not present in the original brief.
