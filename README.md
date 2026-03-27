# nicole-skills

Nicole 专属 AI skill 库。4 个 skill，面向 OpenClaw / Claude Code 环境。

## Skills

| Skill | 用途 | 核心增强 |
|-------|------|---------|
| `skill-creator` | 创建、改进、审计 skill | Nicole 风格规则、三层披露设计、审计 checklist |
| `content-creation` | 多平台内容改写 + 选题生成 | 4平台路由、反AI味写作规则、Flomo 笔记挖掘 |
| `data-viz` | 图表 + Excel 生成 | Nicole 配色方案、CJK 字体配置、反模式清单 |
| `research-engine` | 市场调研 + 战略分析 | T1/T2/T3 证据分级、反偏见 checklist、Pre-mortem |

## 安装

将 skill 目录复制到 `~/.openclaw/workspace/skills/` 并在 `skills/INDEX.md` 中注册。

## 设计原则

1. **渐进式披露** — description (~100词) → SKILL.md body (<500行) → references/ (按需)
2. **Nicole 优先** — 每个 skill 都编码了 Nicole 的风格偏好，不是泛用 AI 行为
3. **不重复系统能力** — skill 只添加 AI 不具备的知识：平台规则、风格约束、领域流程
4. **外部操作必须确认** — 发帖、发邮件、公开内容，永远等 Nicole 确认

## 结构

```
skill-name/
├── SKILL.md          ← 必须：frontmatter + 核心指令
├── references/       ← 按需加载：平台文档、风格指南、schema
├── scripts/          ← 可复用代码（Python/Bash）
└── assets/           ← 输出用文件（模板、字体、图片）
```
