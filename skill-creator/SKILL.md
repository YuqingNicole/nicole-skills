---
name: skill-creator
description: |
  Create, improve, audit, or restructure skills for the Nicole workspace (OpenClaw).
  
  USE WHEN:
  - "create a skill" / "make a skill for X" / "写一个 skill"
  - "improve this skill" / "tighten up" / "优化 skill"
  - "audit the skill" / "review skill quality" / "检查 skill"
  - "add references to skill" / "restructure skill directory"
  - User pastes a SKILL.md and asks for feedback or edits

  DON'T USE WHEN:
  - User just wants to run a skill (load the target skill instead)
  - User asks about skill availability (check skills/INDEX.md)
---

# Skill Creator

Create, improve, and audit skills for the Nicole workspace. A skill is a modular instruction package that turns the AI from general-purpose into a specialist — for a specific platform, workflow, or domain.

---

## Core Philosophy

**A skill is an onboarding guide for a task the AI would otherwise figure out from scratch every time.** It should save tokens, reduce errors, and encode non-obvious knowledge (Nicole's style, platform quirks, proven patterns).

The golden test: *"If the AI had to do this task cold, would it make avoidable mistakes?"* If yes, that's what the skill should prevent.

---

## Skill Anatomy

```
skill-name/
├── SKILL.md          ← required: frontmatter + core instructions
├── references/       ← loaded on demand (platform docs, schemas, style guides)
├── scripts/          ← executable code (deterministic, reusable)
└── assets/           ← output files (templates, fonts, images)
```

### SKILL.md Structure

```yaml
---
name: skill-name
description: |
  One-line summary of what it does.
  
  USE WHEN: (specific triggers — this is the routing signal)
  DON'T USE WHEN: (prevents false positives)
  EDGE CASES: (borderline situations)
---
```

Body: imperative instructions, routing tables, anti-patterns. Max ~500 lines. For anything larger, split into `references/`.

---

## Three Degrees of Freedom

Match specificity to how fragile the task is:

| Fragility | Format | Example |
|-----------|--------|---------|
| Low (many valid approaches) | Plain text guidance | "Write in Nicole's voice: direct, opinionated, no bullet AI-ness" |
| Medium (preferred pattern, some variation) | Pseudocode + parameters | Operation routing table with conditions |
| High (exact sequence required, errors costly) | Full script with few parameters | A Python formatter that must produce valid JSON |

Don't over-constrain low-fragility tasks. Don't under-constrain high-fragility ones.

---

## Progressive Disclosure

Skills load in three stages. Design accordingly:

1. **description field** (~100 words) — Always in context. This is the routing trigger. Make it comprehensive.
2. **SKILL.md body** (<500 lines) — Loaded when skill triggers. Core workflow only.
3. **references/** — Loaded only when needed. Put everything else here.

**Rule:** If you find yourself writing "for details see below," that content belongs in `references/`.

---

## Nicole-Specific Design Rules

These apply to all skills in this workspace:

- **Voice**: Direct, has opinions, no AI filler ("great question!", "I'd be happy to"). See `references/writing-style.md`.
- **Platform awareness**: Telegram = no markdown tables, use bullets. Discord = suppress link embeds with `<>`. WhatsApp = no headers.
- **Memory hygiene**: Skills that produce important decisions or project milestones should note when to write to `memory/YYYY-MM-DD.md`.
- **No unsolicited external actions**: Always confirm before sending messages, posting, emailing. Reading and drafting are free.
- **Chinese/English**: Nicole writes both. Skills should handle either without asking for language preference — detect from context.

---

## Creation Process

### Step 1: Understand with examples
Before writing anything, clarify 2-3 concrete use cases. Ask: "What would Nicole say to trigger this?" and "What would failure look like?"

### Step 2: Plan reusable contents
For each example, ask: what would be rewritten from scratch every time? That's what goes in scripts/references/assets.

### Step 3: Write SKILL.md
Start with frontmatter. Write `description` last — it's the hardest and most important part.

### Step 4: Populate references/
Move anything longer than ~50 lines of reference material out of SKILL.md.

### Step 5: Validate
Run this checklist before shipping:

```
✓ description covers all real trigger phrases (incl. Chinese)
✓ DON'T USE WHEN prevents obvious false positives
✓ Body ≤500 lines
✓ No content duplicated between SKILL.md and references/
✓ No README.md, CHANGELOG.md, or auxiliary files
✓ Nicole's voice/style encoded
✓ External actions require explicit confirmation
```

### Step 6: Package (if distributing)
Create a `.skill` archive:

```bash
# From parent directory of skill-name/
zip -r skill-name.skill skill-name/
```

Verify the archive contains:
- `skill-name/SKILL.md`
- `skill-name/references/` (if any)
- `skill-name/scripts/` (if any)
- `skill-name/assets/` (if any)
- Nothing else

### Step 7: Update INDEX.md
Add to `skills/INDEX.md`: name | description | path.

---

## Audit Checklist

When reviewing an existing skill:

- [ ] `description` field covers all real trigger phrases (incl. Chinese)
- [ ] `DON'T USE WHEN` prevents obvious false positives
- [ ] Body is under 500 lines — if not, move content to `references/`
- [ ] No content duplicated between SKILL.md and references files
- [ ] No README.md, CHANGELOG.md, or other auxiliary files
- [ ] Nicole's voice/style encoded (not generic AI behavior)
- [ ] Platform-specific rules noted (Telegram, Discord, WhatsApp)
- [ ] External actions require confirmation (no auto-posting)
- [ ] After edits: INDEX.md updated

---

## Anti-Patterns

**❌ Over-documenting obvious things**
"Use the read tool to read files" — the AI already knows this.

**❌ Restating system prompt capabilities**
Don't explain web_search, memory_search, etc. in every skill.

**❌ Auxiliary files**
No README.md, INSTALLATION.md, TESTING.md. The skill is for the AI, not the user.

**❌ Flat SKILL.md with everything inline**
If the skill supports 5 platforms, each with 200 lines of platform notes — those go in `references/platform-name.md`.

**❌ Missing DON'T USE WHEN**
Every skill with a broad description will get false-positives. Pre-empt them.

**❌ Generic description**
"Helps with content" triggers on everything. Be specific: "Rewrites a draft for Substack, 小红书, X, and 公众号, applying Nicole's voice and platform-specific formatting rules."

---

## Reference Files

See `references/` for:
- `writing-style.md` — Nicole's voice, anti-AI-ness rules, platform formatting
- `skill-examples.md` — Annotated good/bad SKILL.md examples
