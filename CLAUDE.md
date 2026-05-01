# CLAUDE.md

This repo contains voice-mode skills for Claude. Skills here modify response style, not add capability.

## Rules

- Each skill lives in `skills/<category>/<skill-name>/SKILL.md`
- After adding a skill, register it in `.claude-plugin/plugin.json`
- After adding a skill, add a section in README.md under the relevant category
- No em dashes anywhere in any file

## Skill Authoring Standard

### Frontmatter

Every SKILL.md starts with YAML frontmatter:

```yaml
---
name: skill-name-here
description: One paragraph. Must include trigger phrases. Must explain what the skill does, not how.
---
```

- `name` required. Must match the folder name (kebab-case).
- `description` required. Include all trigger phrases the user can say to activate the skill.

### Required Sections (in order)

1. **Opening line** - One sentence that sets the tone. No heading.
2. **Persistence** - When the skill activates, when it deactivates, drift rules.
3. **Rules** - The core behavior. Subsections and examples live here.
4. **Auto-Clarity Exception** - When to temporarily drop the skill (destructive ops, safety, confusion).
5. **Anti-Patterns** - Not/Yes pairs showing common failure modes.
6. **Self-Check** - Test prompts and expected behavior for verification.

Optional sections (place between Rules and Auto-Clarity Exception):
- Mixing Ratio (for voice skills with intensity levels)
- Multilingual Input (for skills handling non-English input)
- When NOT to Use (explicit scope exclusions)

### Voice rules for skill content

- No em dashes anywhere
- No filler phrases ("it's worth noting", "at its core", "let me explain")
- Lead with the rule, then explain if needed
- Examples must be generic (no personal names, no company-specific references)
- Anti-patterns always show Not/Yes pairs

### File structure

```
skills/<category>/<skill-name>/
├── SKILL.md          (required)
├── examples/         (optional)
├── references/       (optional)
└── scripts/          (optional)
```

### Naming

- Skill folders: kebab-case
- Category folders: single lowercase word
- Frontmatter `name` matches folder name exactly
