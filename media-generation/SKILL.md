---
name: media-generation
description: |
  Generate video scripts, TTS audio drafts, and multi-speaker dialogue content.
  Adapted for Nicole's content stack: 小红书 short video, Substack audio versions,
  podcast-style dialogues, and voiceover scripts for product demos.

  USE WHEN:
  - "帮我写个视频脚本" / "做个小红书视频文案" / "video script"
  - "把这篇文章改成音频稿" / "Substack audio version"
  - "做个播客对话" / "podcast dialogue" / "multi-speaker TTS"
  - "帮我写个产品 demo 旁白" / "voiceover script"
  - "加个音效标注" / "add TTS markup"

  DON'T USE WHEN:
  - User wants written content for reading (use content-creation skill)
  - User wants to publish directly to video platforms (use browser/platform tools)
  - User asks about video editing or post-production

  EDGE CASES:
  - "做个小红书内容" — if text post → content-creation; if video script → this skill
  - "写个播客文案" — if solo narration → this skill; if full episode plan → content-creation
---

# Media Generation

Scripts and audio drafts for video, TTS, and podcast content. Output is text — ready for recording or feeding into a TTS/video tool.

---

## Operation Routing

| Request | Operation |
|---------|-----------|
| 小红书 / 抖音 short video | `short-video-script` |
| Substack audio version | `audio-adaptation` |
| Podcast / multi-speaker dialogue | `dialogue-script` |
| Product demo voiceover | `voiceover` |
| Single-speaker narration | `narration` |

---

## Operation: `short-video-script`

Format for 小红书 / 抖音 (60–90 seconds):

```
【Hook — 前3秒，必须抓住人】
[画面描述] + [口播台词，≤15字]

【主体 — 3段，每段10-20秒】
段落1：[画面] / [台词]
段落2：[画面] / [台词]  
段落3：[画面] / [台词]

【结尾 — 行动引导】
[台词] + [互动问题或关注引导]

字幕文案（同步）：[完整口播文字]
```

Rules:
- 口播 ≤150字（60秒视频）/ ≤220字（90秒）
- 开头不能是"大家好" / "今天给大家分享"
- 每句话独立成立，视频关掉声音看字幕也能懂
- 结尾必须有一个具体问题，不是"觉得有帮助的点个赞"

---

## Operation: `audio-adaptation`

Convert a written Substack post to audio-friendly narration:

1. Remove visual-only elements (bullet points, headers as section breaks)
2. Convert to natural spoken cadence — add pause signals `[medium pause]`
3. Rewrite list items as flowing sentences
4. Add verbal signposting: "First...", "What's interesting is...", "Here's the thing:"
5. Target: ~130 words/minute. Output word count = target duration × 130

Pause markup:
- `[short pause]` — between thoughts (~250ms)
- `[medium pause]` — between sections (~500ms)  
- `[long pause]` — for emphasis before key insight (~1000ms)

---

## Operation: `dialogue-script`

Multi-speaker format (for podcast, interview simulation, or product demo dialogue):

```
Format:
SpeakerA: [line]
SpeakerB: [line]

TTS gender array: ["female", "male"]  (order = first appearance)
Style prompt: "Casual conversation between two people exploring an idea"
```

Emotion markup available:
- `[sigh]` `[laughing]` `[uhm]` — non-speech sounds
- `[sarcasm]` `[whispering]` `[shouting]` — tone modifiers
- `[extremely fast]` — pacing modifier

Keep dialogue lines short (≤2 sentences each). Natural interruption rhythm — not lecture format.

---

## Operation: `voiceover`

Product demo or explainer voiceover:

- Tone: confident, clear, no filler words
- Structure: Problem → Solution → Proof → CTA
- Pacing: 120–140 words/minute (slightly slower than podcast)
- Avoid: passive voice, jargon without explanation, "revolutionary" / "game-changing"

---

## Operation: `narration`

Single-speaker long-form narration (essay, newsletter read-aloud):

- Match the written piece's register (philosophical → measured pace; energetic → faster)
- Insert `[medium pause]` at paragraph breaks
- Replace em-dashes with natural spoken phrasing
- Numbers: spell out for spoken clarity ("three hundred" not "300")

---

## Nicole's Content Formats Reference

| Platform | Ideal length | Style |
|----------|-------------|-------|
| 小红书 video | 60–90 sec | Conversational, fast hook, question ending |
| 抖音 | 15–60 sec | Even faster hook, punchy |
| Substack audio | 5–12 min | Essay register, measured pace |
| Podcast dialogue | 15–30 min | Natural back-and-forth, tangents OK |
| Product demo | 1–3 min | Clear, benefit-focused, no fluff |
