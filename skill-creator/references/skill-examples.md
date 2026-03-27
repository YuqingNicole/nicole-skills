# Skill Examples — Annotated

## Example 1: Good description field

```yaml
description: |
  Rewrites a draft for four platforms: Substack, 小红书, X, and 公众号.
  Applies Nicole's voice (direct, opinionated, no AI filler) and platform-specific rules.
  
  USE WHEN:
  - "发布内容" / "帮我改成小红书版" / "distribute this post"
  - User provides a draft and mentions multiple platforms
  - "多平台" / "content distribution"
  
  DON'T USE WHEN:
  - User wants only one platform (just rewrite inline)
  - User asks about platform specs without content ready
```

**Why it works:** specific verbs (rewrites), named platforms, named voice, clear triggers in both languages.

---

## Example 2: Bad description field

```yaml
description: "Helps with content creation and publishing across platforms."
```

**Why it fails:** triggers on everything. "Helps me write a tweet" would hit this. No DON'T USE WHEN.

---

## Example 3: Good use of references/

SKILL.md body:
```markdown
## Platform Rules

Each platform has specific formatting requirements. See:
- `references/xiaohongshu.md` — title format, tag strategy, comment hooks
- `references/substack.md` — voice, structure, bilingual conventions
- `references/wechat.md` — long-form layout, highlight rules
```

**Why it works:** SKILL.md stays lean. Platform-specific detail only loads when needed.

---

## Example 4: Bad (everything inline)

```markdown
## 小红书 Rules
[200 lines of 小红书 specific formatting]

## Substack Rules  
[200 lines of Substack specific formatting]

## WeChat Rules
[200 lines of WeChat specific formatting]
```

**Why it fails:** 600 lines load every time, even if user only needs Substack.

---

## Example 5: Good fragility matching

High fragility (exact sequence):
```markdown
## Reddit Post Workflow
1. Check account karma: must be ≥50 before product posts
2. Verify subreddit rules: search r/[sub]/wiki/rules
3. Use template from `references/product-post-templates.md`
4. Post during peak hours: 9–11am EST / 7–9pm EST
5. DO NOT post same URL to >3 subs in 24h (shadow ban risk)
```

Low fragility (guidance only):
```markdown
## Voice
Write as Nicole: direct, specific, with a point of view. No hedge words, no AI filler.
```

**Why it works:** The Reddit workflow has real failure modes (account ban). Voice guidance has many valid approaches.

---

## Example 6: Good EDGE CASES usage

```yaml
EDGE CASES:
- "分析市场" for a product to buy → DON'T use this skill, answer directly
- "分析市场" for business entry decision → USE this skill  
- "做竞品分析" about competitors to a product you're buying → answer directly
- "做竞品分析" for startup strategy → USE this skill
```

**Why it works:** The skill name "research" triggers broadly. Edge cases pre-empt the ambiguous middle.
