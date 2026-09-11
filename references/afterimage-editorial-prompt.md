# Photo Relic Prompt Guide

Use this guide when creating the final prompt for the image generation CLI.

## Core Intent

Create a vertical editorial artwork from the user's photograph. The finished image should feel like a distinctive Photo Relic series: a **fully AI-generated** modern print made from the photo's memory. The ENTIRE image is AI-drawn — there is NO half-and-half split, NO preserved photographic region, NO "real photo on top + art below." The whole image is reinterpreted from the source photo into the Photo Relic aesthetic.

The photograph is reference. The relic is what remains after time presses the evidence into paper — and the entire artwork is that relic.

## Required Structure

Describe the result as a single finished artwork with:

- **The ENTIRE image is AI-generated in the Photo Relic style. No half-and-half split. No preserved photographic region.**
- one clear primary relic shape as the central motif of the entire image
- a warm ivory/off-white paper plate or a very restrained source-light field as the background for the entire image
- modern printmaking marks: flat ink blocks, softened edges, sparse lines, negative-space cuts, and measured breaks
- one small title or no title
- enough subject contrast for the artwork to remain readable on a mobile thumbnail

Default to a vertical 4:5, 3:4, or 9:16-friendly composition unless the user asks otherwise.

## Prompt Compiler

Before writing the final generation prompt, compile the user's photo into a compact recipe:

- layout rhythm: photo-over-paper, deep-paper, axis-diptych, horizon-cover, or social-cover
- relic grammar: ink-seal architecture, stacked-order, skyline-memory, light-relic, or edge-remnant
- mark weight: quiet ink, graphic ink, thin trace, or single accent
- title mode: small English title, small Chinese title, textless, or micro bilingual
- motion seed: outline descent, ink assembly, light fade, or still only

Use the recipe to change the actual visual grammar. Do not merely change title words or motif position.

## Photo as Reference — NOT Preserved

State these constraints clearly in the prompt:

- The ENTIRE image is AI-generated in the Photo Relic style. Do NOT preserve the original photo as a literal region.
- Do NOT create a half-and-half split layout (no "real photo on top + AI art on bottom").
- Use the photograph only as reference for subject identity, colors, light, edges, scale, and mood.
- Redraw the entire scene from scratch in the modern printmaking language described in this guide.
- The finished artwork should be a single cohesive image, not a collage of photo + art.

## Relic Logic

Derive the Photo Relic from visible source cues:

- identity: preserve the full relationship that lets the viewer feel the subject's presence, such as roof stack plus base/path, tower plus skyline, doorway plus wall mass, body lean plus ground, shoreline plus horizon, or window grid plus wall plane
- concept: compress the photo into a short emotional idea such as "quiet order", "held dusk", "falling sky", "wet neon", "empty plaza", or "warm stone"
- color: sample muted colors from the image and allow at most one small warm signature accent when the source supports it
- light: carry the source light through mark hierarchy or a very restrained field; do not let atmosphere erase the shape
- edge: simplify a horizon, wall, roof, street, branch, crane, railing, body angle, stair, or shadow edge into a mark that helps build the primary form
- scale: use small people marks, base lines, paths, or ground to keep the subject's scale relationship

Use only a few gestures. Never let the lower panel become only color fields, swatches, generic geometry, a cropped icon, or a full scenic painting.

## Subject Treatments

For architecture and landmarks:

- preserve the complete relationship: roof/mass, body, base, approach/path, and scale marks when visible
- reduce roof layers into stacked arcs or bands
- reduce facades into blocks, voids, narrow cuts, and sparse window signals
- reduce stairs, plazas, or roads into one or two grounding marks
- use one small warm accent from the source, such as vermilion, gold, lantern light, or sunset orange

For city skylines:

- preserve the skyline as a group, not only the tallest landmark
- keep one dominant mark for the key tower or building
- reduce secondary buildings into varied bars or soft masses
- use a horizon/base mark so the city does not float
- use tiny light dots only as sparse signals
- keep the result from becoming a literal skyline illustration

For landscapes, water, roads, or plazas:

- reduce horizon, water, road, or plaza lines into calm residue marks
- keep one subject anchor: tree, mountain, building, vehicle, person, or light source
- use blank paper as silence, not emptiness

For people:

- preserve posture, spacing, and scene relationship
- reduce figures to small irregular vertical marks
- do not draw faces, limbs, clothing detail, or portraits unless explicitly requested

## Signature System

Prefer:

- warm ivory/off-white paper
- deep blue, ink black, muted teal, gray-green, stone gray, dusk charcoal
- one small warm accent: vermilion, gold, orange light, or source-specific red
- flat ink blocks, negative-space cuts, short bars, stacked arcs, base lines, tiny dots, and softened edges
- generous blank space around the relic
- one title that feels like a gallery label or quiet poem
- a lower motif usually 35-55% of the panel width, adjusted for subject clarity

Avoid:

- loud neon gradients
- generic Bauhaus poster cliches
- full watercolor copies of the photo
- heavy texture, grunge, torn paper, tape, stickers, scrapbook collage, or fake film sprockets
- big slogans, coordinates, date stamps, long captions, or explanatory typography
- UI screenshots, phone app overlays, platform watermarks, or social media artifacts
- unrelated decorative shapes
- making the relic too pale to read on a phone
- making the relic so literal that it becomes ordinary illustration

## Douyin-Oriented Still Design

When the user wants social or Douyin potential, design the still with these extra constraints:

- make the relic readable in the first glance on a phone
- preserve a repeatable series identity across different photos
- keep the title short enough to remember
- leave enough negative space for future video motion without clutter
- compose the relic so it can animate from photo to paper: outline descends, blocks assemble, light fades, title appears last

Do not turn the artwork into a marketing poster. The image should still feel like art first.

## Prompt Template

Adapt this template to the specific image:

Create a vertical Photo Relic editorial artwork using the supplied photograph as a style and content reference. Use this recipe: [layout rhythm] / [relic grammar] / [mark weight] / [title mode] / [motion seed]. The ENTIRE image must be AI-generated in the Photo Relic aesthetic — do NOT preserve the original photo as a literal region, do NOT create a half-and-half split layout, redraw the entire scene from scratch. Use the photograph only as reference for subject identity, light, color, edges, scale, and emotional concept. Build one recognizable primary relic using modern printmaking language: deep ink-like blocks, softened edges, negative-space cuts, sparse trace lines, measured breaks, and at most one small warm source-derived accent. The entire image should feel like warm ivory/off-white paper with the relic pressed into it, with generous blank space, quiet editorial spacing, and one very small poetic title or no title. The finished artwork should feel like memory pressed into paper, not a literal illustration, generic poster, infographic, watercolor copy, UI screenshot, or decorative symbol.

Then add 2-4 photo-specific sentences naming the actual visual cues, for example:

- Compress the tiered roof rhythm into stacked dark arcs with a small gold cap and a quiet red body mark.
- Preserve the stone base and central stair as pale grounding cuts so the temple remains whole.
- Reduce the plaza and small visitors into tiny vertical scale ticks, not people drawings.
- Let the cold blue left sky and warm right sky survive only as subdued paper warmth and source-derived ink colors.
- Compress the skyline into one dominant tower, a few supporting bars, a low gate shape, a crane trace, and tiny dusk lights.
- Use only one small vermilion or gold accent, placed like a signature.

## Image Generation Invocation Template

After composing the final prompt from the template above, call your image generation API/CLI to generate the artwork. This skill uses **image-to-image generation** — the user's photo is passed as a reference image, and the model re-draws the entire scene in the Photo Relic aesthetic.

Adapt the command template below to your specific CLI/API tool — parameter names will vary by tool:

```bash
your-image-cli generate \
  --model seedream-5-0 \
  --width 1536 --height 2048 \
  --strength 0.65 \
  --prompt "<composed Photo Relic prompt from template above>" \
  --reference-image "<path-to-user-photo>" \
  --output-format json
```

REST API equivalent:

```json
{
  "model": "seedream-5-0",
  "prompt": "<composed Photo Relic prompt from template above>",
  "image": "<path-or-url-to-user-photo>",
  "width": 1536,
  "height": 2048,
  "strength": 0.65,
  "guidance_scale": 7.5,
  "num_inference_steps": 40
}
```

Key notes:
- **`strength` is critical for image-to-image.** Controls how much the model departs from the reference photo. Use 0.55–0.75 for Photo Relic style. Too low = filtered photo (not redrawn); too high = lost subject identity. Default: 0.65.
- Default model is a high-quality image-to-image model (e.g., Seedream 5.0) for best quality. A faster turbo model can be used for quick drafts.
- Default dimensions: width=1536, height=2048 (vertical 3:4). For 9:16 social cover use width=1152, height=2048. For 4:5 use width=1638, height=2048.
- The reference image can be a local file path or a URL.
- If generation is async and times out, poll for completion using the returned task/batch ID until status is "completed" or "succeeded".
- The generated image URL is in the JSON output — extract and present it to the user.

## Quality Gate

Inspect the generated image before finalizing:

- **CRITICAL: The ENTIRE image is AI-generated. There is NO half-and-half split. No part of the original photo appears as a literal photographic region. If the result looks like "photo on top, art on bottom," it has FAILED — regenerate.**
- Artwork identity: the relic reads at thumbnail size.
- Full relationship: the artwork preserves the subject plus base, path, horizon, ground, skyline, or scale cues when those matter.
- Artistic compression: the image is neither a vague haze nor a literal illustration.
- Series signature: warm paper, deep ink, sparse marks, one possible accent, generous blank space, quiet title.
- Mobile memorability: one motif can be remembered after a quick glance.
- Palette: colors are sampled from the source photo and remain restrained.
- Typography: text is tiny or absent and does not become a slogan.
- Clean output: no watermark, UI overlay, platform text, fake border, sticker, collage, or unrelated decoration.

If a major gate fails, regenerate once with a shorter corrective prompt naming the failure, such as "make the temple relic more like a printmaking seal and less like watercolor" or "increase subject recognition while preserving generous blank paper" or "redraw the entire image from scratch, do NOT preserve the original photo as a literal region."
