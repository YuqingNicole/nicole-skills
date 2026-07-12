---
name: x-renaissance-cover
description: Generate polished 5:2 cover images for X/Twitter long-form posts, especially idea essays that need an art-history, Renaissance, editorial, or museum-poster look. Use when the user asks for an X long article cover, a 5:2 social cover, or wants to turn a conceptual title into an image generation prompt with readable title typography and Renaissance-style visual drama.
---

# X Renaissance Cover

## Workflow

Use the built-in image generation flow unless the user explicitly asks for another tool or model path.

1. Extract the exact title, required aspect ratio, style, and any hard constraints.
2. Convert the idea into a symbolic Renaissance scene instead of literal clip art.
3. Reserve a clean title area before describing the characters or objects.
4. Prompt for a 5:2 horizontal banner with editorial cover polish.
5. Include the exact title in the prompt only when the user wants text inside the image. Preserve spelling, casing, and mixed-language fragments.
6. After generation, inspect whether the title is readable, the aspect ratio is correct, and the art direction matches the requested style. Iterate once with a targeted correction if needed.

## Composition Pattern

Default layout:

- Canvas: wide horizontal 5:2 banner.
- Visual weight: subject or narrative scene on the left or center-left.
- Text zone: right side or upper third, with dark or quiet negative space.
- Mood: intellectual, poetic, dramatic, not gimmicky.
- Detail density: high around the subject, low behind title text.

For abstract technology topics, use symbolic pairings:

- Human agency: hand on reins, compass, manuscript, astrolabe, architectural measure, deliberate posture.
- AI or machine intelligence: brass automaton, marble angel, geometric halo, illuminated circuitry, celestial mechanism.
- Trust without control: blindfold, loose parchment contract, unattended oracle, over-bright halo, unexamined prophecy.
- Control without hostility: reins, steering, calibration, apprenticeship, instrument-making, workshop discipline.

Avoid making AI monstrous unless the user asks for fear or threat. The stronger default is powerful but governable.

## Prompt Template

Adapt this template directly:

```text
Use case: ads-marketing
Asset type: X long-form article cover, wide horizontal banner, exact aspect ratio 5:2.
Primary request: Create a Renaissance art style cover for the title: "<TITLE>".

Composition: A dramatic Renaissance oil painting scene, wide 5:2 canvas. Center-left: <HUMAN_AGENCY_SYMBOL>. Nearby: <AI_SYMBOL>, powerful but not monstrous. Reserve <TEXT_ZONE> as clean negative space for the title.

Text: Include the exact title clearly and legibly as written: "<TITLE>". Use elegant high-contrast serif typography, like a museum exhibition poster. Keep all text fully inside the image, no extra words.

Style: Renaissance oil painting, chiaroscuro, warm candlelit golds, deep lapis blue accents, classical drapery, fresco texture, fine brushwork, balanced sacred-composition geometry, intellectual and poetic mood.

Layout requirements: 5:2 banner, title readable at social feed thumbnail size, no clutter behind text, sophisticated editorial cover, polished final asset.

Avoid: modern sci-fi neon overload, cartoon style, stock-photo look, distorted hands, extra text, watermark, logo, garbled lettering.
```

## Example

For:

```text
标题：需要驾驭 ai 而不是一味的trust me bro
风格：文艺复兴艺术风格
比例：5:2
```

Use:

```text
Use case: ads-marketing
Asset type: X long-form article cover, wide horizontal banner, exact aspect ratio 5:2.
Primary request: Create a Renaissance art style cover for the title: "需要驾驭 ai 而不是一味的trust me bro".

Composition: A dramatic Renaissance oil painting scene, wide 5:2 canvas. Center-left: a thoughtful human figure in Renaissance clothing calmly holding reins made of luminous threads, guiding a symbolic AI automaton or angelic machine figure. The AI should feel powerful but not monstrous: polished brass, marble, subtle circuit-like halo, manuscript geometry, celestial light. Right side or upper third should have clean negative space for the title.

Text: Include the exact title clearly and legibly in Chinese plus English lowercase as written: "需要驾驭 ai 而不是一味的trust me bro". Use elegant serif typography with high contrast, like a museum exhibition poster. Keep all text fully inside the image, no extra words.

Style: Renaissance oil painting, chiaroscuro, warm candlelit golds, deep lapis blue accents, classical drapery, fresco texture, fine brushwork, balanced sacred-composition geometry, intellectual and poetic mood.

Layout requirements: 5:2 banner, title readable at social feed thumbnail size, no clutter behind text, sophisticated editorial cover, polished final asset.

Avoid: modern sci-fi neon overload, cartoon style, stock-photo look, distorted hands, extra text, watermark, logo, garbled lettering.
```

## Quality Check

Before finishing, check:

- The image reads as a cover, not just an illustration.
- The title is inside the frame and readable at small size.
- The text contains no extra slogan, watermark, or invented subtitle.
- The main scene expresses the essay's argument through symbolism.
- Renaissance cues dominate more than modern sci-fi cues.
- The 5:2 crop has breathing room and does not cut off the main subject awkwardly.

If title rendering is flawed, regenerate with simpler text placement, fewer background details behind the letters, and a larger type block. If the scene is too literal, replace objects with Renaissance-era symbolic instruments and compositional geometry.
