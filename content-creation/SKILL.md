---
name: content-creation
description: |
  Rewrites a draft or raw idea into platform-specific versions for Substack, 小红书, X/Twitter, and 公众号.
  Applies Nicole's voice: direct, opinionated, no AI filler, no bullet-point brain dump.
  Also handles single-platform rewrites and content idea generation from Flomo notes or topics.

  USE WHEN:
  - "帮我改成小红书版" / "发布内容" / "多平台" / "distribute this post"
  - "写一篇 Substack" / "生成 thread" / "帮我写公众号文章"
  - User provides a draft and asks for platform adaptation
  - "从我的笔记里找写作选题" / "给我一个内容方向"

  DON'T USE WHEN:
  - User wants to publish (go to platform-specific tools — mcporter, browser)
  - User asks about engagement stats or analytics
  - Quick one-liner reply (just answer inline)

  EDGE CASES:
  - "帮我写一篇文章" with no platform specified → ask which platform(s), then proceed
  - Draft is rough notes, not prose → clean up into main draft first, then adapt
---

# Content Creation

Adapt drafts to Nicole's four publishing platforms, or generate content from scratch.

---

## Operation Routing

| Request | Operation |
|---------|-----------|
| Draft + multiple platforms | `multi-platform` |
| Draft + one platform | `single-platform` |
| Topic/notes → content | `generate` |
| Find writing ideas | `ideation` |

---

## Operation: `multi-platform`

Produce all four versions in one pass. Present for review before any publishing step.

**Output order:** 公众号 → 小红书 → X thread → Substack

For each version, apply the rules in `references/platforms.md`.

**Review gate:** After presenting all four versions, stop and wait. Nicole will:
- Approve all → proceed to publish flow (separate tool)
- Request edits to specific platform → revise only that version
- Skip a platform → drop it, proceed with rest

---

## Operation: `single-platform`

Rewrite directly for the requested platform. Apply relevant section from `references/platforms.md`.

---

## Operation: `generate`

When Nicole provides a topic, angle, or raw notes:

1. Identify the **core insight** — the one sentence that's actually interesting
2. Identify the **primary audience** — heavy AI users? Startup founders? General curious people?
3. Draft the 公众号 version as the source of truth (highest density)
4. Derive other platforms from it

Do NOT start writing without a clear core insight. If the raw material doesn't have one, surface that first.

---

## Operation: `ideation`

Search `~/workspace/context-infrastructure/flomo/notes.json` for themes worth developing.

Look for:
- Observations that appear multiple times in different contexts (compressed insight)
- Contradictions with mainstream takes (variant view)
- Personal experiences with generalizable lessons
- Frameworks Nicole uses that aren't widely named

Surface top 3-5 as one-line angles, not full outlines.

---

## Voice Rules (Non-Negotiable)

See `references/writing-style.md` for full rules. Key points:

- No "In this post, I'll cover..." / "Let's dive in" / "Final thoughts"
- No rhetorical questions as section headers
- Specific numbers > abstract claims
- First sentence should earn attention, not explain what's coming
- Nicole's Substack audience: curious, 30-and-under, heavy AI users — write to the smartest person in that room

---

## Platform Quick Reference

Full rules in `references/platforms.md`. Minimums:

| Platform | Length | Key constraint |
|----------|--------|----------------|
| 公众号 | 1000–2000 words | High density, philosophical register |
| 小红书 | 200–400 words | Title ≤15 chars, end with question, 5–8 tags |
| X thread | 1–3 tweets | First tweet standalone hook |
| Substack | 600–1500 words | Personal "I" voice, bilingual or English |
