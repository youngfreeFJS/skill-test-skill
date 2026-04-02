# skill-test-skill

An Agent Skill that tests and scores any other Agent Skill against the official [anthropics/skills](https://github.com/anthropics/skills) specification.  
  
🦞 clawhub here: https://clawhub.ai/youngfreefjs/skill-test-skill

## What It Does

Install this skill, then point it at any skill directory or `SKILL.md` file. It will:

1. Read every file in the skill (SKILL.md, scripts/, references/, assets/, etc.)
2. Check each file line-by-line against the official spec rules
3. Score the skill across **6 dimensions** (100 points total)
4. Output a detailed Markdown report with findings and prioritized improvement suggestions

Supports **Chinese and English** output — the report language follows the language of your request.

## Scoring Dimensions

| # | Dimension | Max Points |
|---|-----------|-----------|
| 1 | Directory Structure | 10 |
| 2 | Frontmatter Compliance (name, description, etc.) | 30 |
| 3 | Body Content Quality | 25 |
| 4 | Progressive Disclosure Design | 15 |
| 5 | Optional Directory Quality (scripts/, references/, assets/) | 10 |
| 6 | Description Trigger Optimization | 10 |

## Grade Scale

| Score | Grade |
|-------|-------|
| 90–100 | Excellent — production-ready |
| 75–89 | Good — minor improvements recommended |
| 60–74 | Acceptable — needs improvement |
| 40–59 | Poor — significant rework required |
| 0–39 | Critical — major rewrite needed |

## Usage Examples

After installing the skill, you can trigger it with:

**English:**
- `"Check my skill at /path/to/my-skill"`
- `"Score this skill: https://github.com/user/repo/tree/main/skills/my-skill"`
- `"Does my SKILL.md follow the spec?"`

**中文：**
- `"检查一下 /path/to/my-skill 是否符合规范"`
- `"给这个skill打分：/path/to/my-skill"`
- `"这个skill符合anthropics的要求吗？"`

## Rules & Specification

The validation rules in this skill are based on:

- **[Agent Skills Specification](https://agentskills.io/specification)** — the official spec defining SKILL.md format, frontmatter fields, directory structure, and progressive disclosure requirements
- **[anthropics/skills — skill-creator](https://github.com/anthropics/skills/blob/main/skills/skill-creator/SKILL.md)** — Anthropic's official skill-creation guide, which defines best practices for writing style, description optimization, trigger tuning, and the "why over MUST" principle
- **[anthropics/skills repository](https://github.com/anthropics/skills)** — real-world skill examples used as reference for what good looks like

Key principles derived from skill-creator:
- All "when to use" information belongs in the `description` field, not the body
- Prefer explaining *why* over issuing bare `ALWAYS`/`NEVER` commands
- Keep `SKILL.md` under 500 lines; move large content to `references/`
- The `description` field is the primary triggering mechanism — make it specific and slightly "pushy" to prevent undertriggering

## File Structure

```
skill-test-skill/
├── SKILL.md                        ← Core skill instructions (416 lines)
├── README.md                       ← This file
└── references/
    ├── spec-summary.md             ← Complete spec rules reference (loaded on demand)
    └── scoring-rubric.md           ← Detailed scoring criteria per check (loaded on demand)
```
