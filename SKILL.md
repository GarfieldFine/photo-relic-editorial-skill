---
name: photo-relic-editorial
description: "Create distinctive Photo Relic editorial artworks from user-provided photographs: generate a FULLY AI-REDRAWN vertical artwork that reinterprets the entire photo into modern printmaking language with quiet Eastern restraint and source-derived light. The ENTIRE image is AI-generated — no half-and-half split, no preserved photographic region. Use when the user asks to turn a photo into minimal art, photographic relic posters, abstract editorial photography, gallery-like photo posters, Douyin-ready art series covers, graphic photo abstraction, afterimage compositions, or similar visual treatments."
---

# Photo Relic Editorial

## Overview

Use this skill to transform a user-provided photograph into a **fully AI-generated** vertical editorial artwork. The ENTIRE finished image is drawn by AI — there is NO half-and-half split, NO preserved photographic region, NO "real photo on top + relic below" layout. The whole image is reinterpreted from the source photo into the Photo Relic aesthetic: modern printmaking, quiet Eastern restraint, compressed memory marks on warm paper.

The source photograph is used as a **reference for style, color, structure, light, and mood** — not pasted or preserved as a literal half of the output. The AI re-draws the entire scene from scratch in the Photo Relic visual language.

The aesthetic should feel like a modern paper print: quiet, restrained, source-derived, recognizable, and artful enough to become a repeatable visual series.

This is a creative image-generation skill. When producing the final image, use an **image generation CLI** with the user's photo as the reference image (`input_images` parameter). The AI should generate the ENTIRE artwork — top to bottom — in the Photo Relic style, not preserve any part of the original photo as-is.

## Workflow

1. Inspect the supplied photograph before writing the generation prompt.
2. Identify 3-5 source cues from the real image:
   - the main subject identity and the full relationship that makes it recognizable
   - the photo's emotional core, reduced to a short concept such as "held dusk", "falling sky", "quiet order", "wet neon", or "alone in the plaza"
   - dominant colors plus one possible signature accent: vermilion, small gold, dusk orange, or a source-specific warm light
   - strongest light or shadow direction, including large cold/warm areas
   - key structural cues: roof layers, towers, arches, windows, paths, stairs, horizon, ground, water, people scale, or silhouettes
3. Choose a compact Photo Relic recipe before prompting:
   - layout rhythm
   - relic grammar
   - mark weight
   - title mode
   - motion seed when useful for social-video follow-up
4. Read `references/afterimage-editorial-prompt.md` before composing the final image prompt.
5. Ask for the missing photo only if no usable source image is available.
6. Compose the final generation prompt from the template in `references/afterimage-editorial-prompt.md`, then call your **image generation CLI** to generate one finished vertical artwork. Use the user's photo as the reference image via `input_images`. Use a high-quality image-to-image model (e.g., Seedream 5.0 or equivalent) by default for best quality. Set width=1536, height=2048 for a vertical 3:4 layout. Generate one artwork unless the user asks for variants.
7. Use the Quality Gate before finalizing. If the result clearly fails one major gate, regenerate once with tighter constraints.

## Image Generation CLI Invocation

This skill uses **image-to-image generation** (not text-to-image). The source photograph is passed as a reference image, and the model re-draws the entire scene in the Photo Relic aesthetic.

### Key Parameters

| Parameter | Value | Notes |
|-----------|-------|-------|
| `input_text` | The composed Photo Relic prompt | See prompt template in references |
| `model` | Seedream 5.0 or equivalent | High-quality image-to-image model. Alternative: a faster turbo model for quick drafts |
| `width` | `1536` | Vertical 3:4 layout |
| `height` | `2048` | Vertical 3:4 layout |
| `input_images` | `["<path-to-user-photo>"]` | The user's original photo as reference |
| `strength` | `0.55`–`0.75` | **Critical for image-to-image.** Controls how much the model departs from the reference photo. Higher = more creative reinterpretation; lower = closer to original photo. Use 0.65 as default for the Photo Relic style — the model must depart enough to fully redraw in printmaking language, but retain subject identity. |
| `guidance_scale` | `7.5` (if supported) | Prompt adherence strength. Adjust if the result is too literal or too abstract. |
| `num_inference_steps` | `30`–`50` (if supported) | More steps = higher quality, slower generation. |

### Why `strength` Matters

The Photo Relic style requires the model to **completely reinterpret** the photo — not lightly edit it. If `strength` is too low (< 0.5), the output will look like a filtered photo, not a redrawn artwork. If too high (> 0.8), the model may lose the subject's identity. The 0.55–0.75 range is the sweet spot for this skill.

### Command Template

Adapt this to your specific CLI/API tool — parameter names will vary:

```bash
your-image-cli generate \
  --model seedream-5-0 \
  --width 1536 --height 2048 \
  --strength 0.65 \
  --prompt "<composed Photo Relic prompt>" \
  --reference-image "<path-to-user-photo>" \
  --output-format json
```

If your tool uses a REST API instead of a CLI, the equivalent request body would look like:

```json
{
  "model": "seedream-5-0",
  "prompt": "<composed Photo Relic prompt>",
  "image": "<path-or-url-to-user-photo>",
  "width": 1536,
  "height": 2048,
  "strength": 0.65,
  "guidance_scale": 7.5,
  "num_inference_steps": 40
}
```

### Dimension Variants

| Aspect ratio | Width | Height | Use case |
|---|---|---|---|
| 3:4 (default) | 1536 | 2048 | Standard vertical artwork |
| 9:16 | 1152 | 2048 | Social video cover (Douyin/Reels/Stories) |
| 4:5 | 1638 | 2048 | Instagram-style vertical |

### After Generation

Extract the image URL from the JSON output and present it to the user. If the generation times out (some APIs are async), poll for completion using the returned task/batch ID until the status is "completed" or "succeeded".

## ⚠️ Critical: Fully AI-Generated, No Half-and-Half

**The ENTIRE output image must be AI-generated.** This is the most important rule of this skill.

- **NO** half-and-half split layout (no "real photo on top, AI relic below").
- **NO** preserving any part of the original photograph as a literal, unmodified photographic region.
- **NO** pasting, compositing, or stitching the original photo into the output.
- The source photo is a **reference for style and content only** — the AI re-draws the ENTIRE scene from scratch in the Photo Relic aesthetic.
- The finished artwork should be a single, cohesive, fully AI-drawn vertical image from top to bottom, in the modern printmaking language described below.

If the generated result looks like it has a real photograph on one half and AI art on the other, it has FAILED. Regenerate with stricter emphasis on "redraw the entire image from scratch."

## Signature Aesthetic

Make the result feel like this:

A fully AI-drawn vertical artwork that looks as if time pressed the photograph into a few ink marks on warm paper. The ENTIRE image — top to bottom — is in the Photo Relic style: modern printmaking, warm paper texture, sparse ink marks, generous negative space, and one quiet poetic title.

Use these signature traits consistently:

- The ENTIRE image is AI-generated in the Photo Relic aesthetic. No half photo, half art split.
- Use a warm ivory, off-white, or very quiet source-light panel as the background for the entire image.
- Build the artwork from deep blue, ink black, gray-green, stone gray, muted teal, and one small warm accent when the source supports it.
- Use one primary form plus a few support marks. Do not fill the panel.
- Make the subject recognizable at thumbnail size, but not literal enough to become a normal illustration.
- Let marks feel like modern printmaking: flat ink blocks, softened edges, small breaks, negative-space cuts, and measured irregularity.
- Keep titles small, poetic, and label-like. The image should not read as an advertisement.
- Favor a stable series identity over one-off novelty.

## Creative Rules

- The ENTIRE image is AI-generated. Do NOT preserve any part of the original photograph as a literal photographic region. Do NOT create a half-and-half split layout.
- Use the source photo as reference for colors, light logic, negative space, edges, subject placement, and spatial tension — but redraw everything from scratch in the Photo Relic visual language.
- Always create one clear primary relic shape. The viewer should sense the whole subject relationship through the simplified form.
- Keep the relic complete enough to preserve the photo's main identity. For architecture, include roof/mass, base, entrance or path, ground/horizon, and scale marks when they matter.
- Translate details into marks, not decorations: roof layers become stacked arcs; windows become sparse cuts or tiny dots; people become short vertical ticks; water becomes one or two horizontal residues; dusk becomes one small warm signal.
- Use atmosphere only as support. Light may hold the relic, but it must not replace the form.
- Prefer quiet precision over ornament. Use breathing room, one primary motif, a few supporting marks, and restrained title treatment.
- Keep the family resemblance to minimal editorial photo art, but avoid copying any specific external skill's text, layout formula, examples, or named style.
- Avoid loud gradients, commercial-poster hierarchy, heavy watercolor, fake vintage texture, stickers, collage clutter, UI overlays, platform watermarks, and decorative geometry unrelated to the photo.

## Composition Patterns

Choose one pattern based on the photograph. Do not output a panel made only of fields, lines, or swatches; the relic must have a central motif and enough surrounding structure to carry the whole photograph. **All patterns below produce a FULLY AI-generated image — no half-and-half split.**

- **Paper Relic**: Use a clean ivory/off-white background for the entire image. Place a small-to-medium source-derived relic in the center, with generous blank space and one title.
- **Light-Pressed Relic**: Use a very restrained cold/warm light field sampled from the photo for the entire image, then press a clear ink-like subject shape into it.
- **Architectural Seal**: Reduce a building or skyline into blocks, arcs, voids, base lines, and a small warm accent. Keep identity strong and ornament low.
- **Horizon Memory**: For cities, water, roads, or open landscapes, anchor the relic with one calm horizon/base mark so the form does not float.
- **Human Scale Echo**: If people matter, reduce them to small irregular vertical marks that show scale and atmosphere. Do not draw faces, limbs, or clothing detail.
- **Motion Cover Seed**: When the user wants Douyin or social-video potential, compose the still image so it can animate: subject outline descends, relic marks assemble, title appears last.

## Recipe Selection

Pick one option from each axis before writing the image prompt. Vary the recipe when recent outputs look too similar, but keep the series identity stable.

Layout rhythm:

- **full-paper**: the entire image is AI-drawn Photo Relic style on warm paper; default and preferred. No split, no half photo.
- **deep-paper**: large paper field with a small subject motif in the center; use when the relic needs air.
- **axis-diptych**: symmetric central axis composition; use for symmetrical architecture.
- **horizon-cover**: lower relic anchored by a horizon/base; use for cities, water, plazas, roads, and skylines.
- **social-cover**: readable composition for a 9:16 video cover; keep the relic and title clear on mobile.

Relic grammar:

- **ink-seal architecture**: deep block shapes, negative-space cuts, and one accent.
- **stacked-order**: arcs, bands, steps, or floors reduced into calm layers.
- **skyline-memory**: landmark plus supporting bars, horizon, sparse light marks.
- **light-relic**: subject silhouette pressed into a subdued light field.
- **edge-remnant**: a few decisive edges cluster into one recognizable motif.

Mark weight:

- **quiet ink**: medium-dark marks with softened edges; default.
- **graphic ink**: bolder flat blocks when the subject needs stronger recognition.
- **thin trace**: fine lines for cranes, railings, paths, water, or delicate edges.
- **single accent**: one warm point or short bar only, used like a signature.

Title mode:

- **small English title**: safe default for an editorial series.
- **small Chinese title**: use when the user asks for Chinese feeling or social-video resonance.
- **textless**: use when the relic is strong enough.
- **micro bilingual**: use only when explicitly requested.

Motion seed:

- **outline descent**: subject outline forms and settles into the relic panel.
- **ink assembly**: relic marks appear one by one from largest form to smallest accent.
- **light fade**: light fades into the paper field before the relic appears.
- **still only**: default unless the user asks about Douyin/video.

## Output Prompting

When composing the `input_text` for the image generation CLI, include:

- **CRITICAL: The ENTIRE image must be AI-generated in the Photo Relic style. Do NOT preserve the original photo as a literal region. Do NOT create a half-and-half split layout. Redraw the entire scene from scratch.**
- a vertical editorial artwork layout suitable for a repeatable art series, fully AI-drawn
- one recognizable primary Photo Relic derived from the source photo's subject, light, color, and mood
- a warm paper or restrained source-light background that supports the relic without competing with it
- modern printmaking language: flat ink blocks, soft edges, negative-space cuts, sparse lines, and one small source-derived accent when useful
- restrained typography, usually one very small title only
- the entire image should feel like a single cohesive artwork, not a collage of photo + art

Do not mention internal analysis in the final prompt. Translate the visual decision into concise production language.

## Quality Gate

Before finalizing, check the generated result:

- **CRITICAL: The ENTIRE image is AI-generated. There is NO half-and-half split. No part of the original photo appears as a literal photographic region. If the result looks like "photo on top, art on bottom," it has FAILED — regenerate.**
- The artwork is recognizable at thumbnail size.
- The artwork preserves the full subject relationship, not only a decorative fragment.
- The image feels like a memory print, not a normal illustration, infographic, or generic poster.
- The marks are few, deliberate, and source-derived.
- There is a stable series signature: warm paper, deep ink, one possible accent, generous blank space, quiet title.
- The result has enough artistic strangeness to feel memorable, but enough clarity to be shared quickly on mobile.
- Typography is absent or very small; it does not become the main visual.
- The palette clearly comes from the source photo.
- There are no UI overlays, watermarks, social media artifacts, fake film borders, stickers, or unrelated decorations.

If one major item fails, regenerate once with a shorter, stricter prompt focused on that failure.
