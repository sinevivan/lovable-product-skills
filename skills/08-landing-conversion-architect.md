# Display Name
Landing Conversion Architect

## Name
landing-conversion-architect

## Description
Designs a data‑driven conversion narrative for landing pages before visual assets are created. It defines audience awareness, core promise, unique mechanism, objection handling, proof points, section ordering, CTA hierarchy, mobile‑first content layout, and handoffs to art direction.

## Instructions

### Objective
Create a complete, evidence‑backed conversion story that guides the subsequent visual design. The narrative must align with the target audience’s awareness level, articulate a clear value promise, introduce a differentiating mechanism, pre‑empt common objections, embed credible proof, and prescribe a logical section sequence ending with a high‑impact call‑to‑action. The output serves as the blueprint for the Art Direction skill.

### Use when
- Initiating a new landing page for a product or campaign.
- Existing visuals exist but lack a cohesive conversion narrative.
- Stakeholders request a structured story before committing design resources.
- A/B testing plans need a hypothesis‑driven content framework.

### Do not use when
- The landing page is purely informational with no conversion goal.
- Visual assets are already finalized and cannot be altered.
- The audience is undefined or the market research is unavailable.
- Legal or compliance teams have not approved the core promise.

### Required inputs
1. **Target audience profile** – demographics, psychographics, awareness stage, pain points.  
2. **Traffic source analysis** – channel, intent signals, expected visitor behavior.  
3. **Core value proposition** – concise promise (max 12 words).  
4. **Unique mechanism** – the “how” that makes the promise credible.  
5. **Objection list** – top 3‑5 concerns gathered from surveys, support tickets, or competitor analysis.  
6. **Proof assets** – testimonials, case study metrics, third‑party endorsements, or data points.  
7. **Business goals** – primary conversion metric (e.g., sign‑ups, purchases) and secondary metrics.  
8. **Brand guidelines** – tone, voice, and any mandatory language.

### Workflow
1. **Validate inputs** – cross‑check audience and traffic data against the latest analytics report; flag missing or contradictory items.  
2. **Map awareness level** – classify the audience as Unaware, Problem‑Aware, Solution‑Aware, or Product‑Aware; select the appropriate narrative angle.  
3. **Craft promise statement** – ensure it is specific, measurable, and resonates with the identified pain point.  
4. **Define mechanism** – articulate the underlying process or technology in layman’s terms; embed a metaphor if it aids comprehension.  
5. **Objection handling matrix** – pair each objection with a concise rebuttal that leverages proof assets.  
6. **Proof integration plan** – assign each proof asset to the narrative segment where it maximizes trust (e.g., social proof in the “Why Trust Us?” section).  
7. **Section sequencing** – order sections as: Hook → Problem → Promise → Mechanism → Proof → Objection Handling → CTA. Adjust for mobile‑first flow by placing the CTA within the first 75% of scroll depth.  
8. **CTA hierarchy** – define primary and secondary CTAs, label button copy, and specify micro‑copy for hover/validation states.  
9. **Mobile content checklist** – confirm headline length ≤ 30 characters, bullet points ≤ 3 per block, and image placeholders with alt‑text placeholders.  
10. **Handoff package** – compile a markdown brief containing the narrative, section order, CTA specs, and mobile checklist; tag the Art Direction skill with `@art-direction` for immediate pickup.

### Output contract
- **Narrative Blueprint** – markdown section with headings: Hook, Problem, Promise, Mechanism, Proof, Objections, CTA.  
- **Section Order Table** – CSV‑style list with column headings `Section, Position, Mobile Priority`.  
- **CTA Specification** – JSON snippet containing `primaryCTA`, `secondaryCTA`, `buttonCopy`, `microCopy`.  
- **Mobile Checklist** – bullet list of compliance items.  
- All outputs must be syntactically valid, free of placeholder text, and reference at least one proof asset per claim.

### Quality gate
1. **Evidence coverage** – ≥ 80 % of claims linked to a proof asset.  
2. **Readability** – Flesch‑Kincaid Grade ≤ 9; sentence length ≤ 20 words.  
3. **Alignment check** – narrative must reflect the audience’s awareness level; mismatches trigger a revision flag.  
4. **CTA clarity** – primary CTA verb must be action‑oriented and unique on the page.  
5. **Mobile compliance** – passes the Mobile Checklist without warnings.

### Safety constraints
- Do not fabricate data; if proof is unavailable, mark the claim as “pending verification”.  
- Avoid medical, financial, or legal advice unless explicitly approved by compliance.  
- Exclude personally identifiable information (PII) from any proof excerpts.  
- Ensure all statements comply with advertising standards (e.g., FTC, GDPR).  
- Escalate any ambiguous promise or unverifiable mechanism to the Compliance skill before finalization.
