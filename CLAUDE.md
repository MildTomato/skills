# Agent Skills Repository

This file provides guidance to AI coding agents working on this repository.

## Repository overview

A collection of agent skills following the
[Agent Skills](https://agentskills.io/) specification. Each skill is a
directory containing instructions, rules, and references that extend agent
capabilities.

## Repository structure

```
{skill-name}/
  SKILL.md              # Required: skill definition with frontmatter
  metadata.json         # Required: version, organization, abstract
  rules/                # Optional: focused, actionable rule files
  references/           # Optional: comprehensive background documentation
  AGENTS.md             # Generated: compiled rules (run npm run build)
  scripts/              # Optional: executable helper scripts
  assets/               # Optional: static resources
```

## Creating a new skill

Follow these steps when adding a skill to this repository.

### 1. Create directory and SKILL.md

Create a kebab-case directory with a `SKILL.md` file:

```markdown
---
name: skill-name
description: One-line description of what this skill does and when to use it.
license: MIT
metadata:
  author: author-name
  version: '1.0.0'
---

# Skill Title

Brief description.

## When to Apply

Reference these guidelines when:

- Trigger condition 1
- Trigger condition 2
```

### 2. Frontmatter requirements

Every `SKILL.md` must include:

- `name`: Lowercase, kebab-case, matches directory name
- `description`: Clear description including when to use it
- `license`: License identifier (use MIT unless specified otherwise)
- `metadata`: Must include `author` and `version`

### 3. Add metadata.json

Create a `metadata.json` in the skill directory:

```json
{
  "version": "1.0.0",
  "organization": "Organization Name",
  "date": "Month Year",
  "abstract": "Brief description of the skill.",
  "references": ["https://relevant-source.example.com"]
}
```

### 4. Add rules (if applicable)

If the skill has multiple actionable guidelines, create individual rule files
in a `rules/` directory.

**Rule file format:**

```markdown
---
title: Rule Title
impact: CRITICAL | HIGH | MEDIUM | LOW
impactDescription: Brief impact note
tags: tag1, tag2, tag3
---

## Rule Title

One-line explanation of the rule.

**Incorrect:**

(example of what NOT to do)

**Correct:**

(example of what TO do)
```

**Rule file guidelines:**

- One rule per file, named `{category}-{description}.md`
- Target 50-70 lines per rule
- Focus on terminal output and UX examples, not implementation code
- Only include source code when it's specifically needed (security patterns,
  TTY detection, signal handling)
- Show what good CLI/tool behavior looks like
- Use incorrect/correct pattern
- Keep frontmatter with title, impact, and tags

### 5. Add references (if applicable)

Place comprehensive background documentation in a `references/` directory.
These are loaded by agents only when deeper context is needed.

### 6. Build AGENTS.md

Run the build script to compile rules into a single document:

```bash
npm run build
```

This generates `AGENTS.md` from all rule files in the `rules/` directory.

### 7. Format

Run Prettier before committing:

```bash
npm run format
```

### 8. Validate

Verify the skill is detected correctly:

```bash
npx skills add . --list
```

## Skill types

### Rule-based skills (like cli-guidelines)

For skills with many individual guidelines:

```
skill-name/
  SKILL.md           # Quick reference with rule categories
  metadata.json      # Version and metadata
  rules/             # Individual rule files (50-70 lines each)
  references/        # Background documentation
  AGENTS.md          # Generated from rules
```

`SKILL.md` should include:

- "When to Apply" section
- "Rule Categories by Priority" table
- "Quick Reference" listing all rules
- "Structure" section explaining rules/ vs references/

### Self-contained skills (like docs-writer)

For skills that are a single set of instructions:

```
skill-name/
  SKILL.md           # Complete instructions in one file
  metadata.json      # Version and metadata
```

`SKILL.md` should be under 500 lines and contain all instructions directly.

## Naming conventions

- **Skill directories**: `kebab-case` (for example, `cli-guidelines`,
  `docs-writer`)
- **Rule files**: `{category}-{description}.md` (for example,
  `basics-exit-codes.md`, `output-json-flag.md`)
- **SKILL.md**: Always uppercase, always this exact filename
- **metadata.json**: Always lowercase, always this exact filename

## Quality checklist

Before committing a new or updated skill, verify:

- [ ] `SKILL.md` has valid frontmatter (name, description, license, metadata)
- [ ] `metadata.json` exists with version, organization, abstract
- [ ] Skill name matches directory name
- [ ] `npx skills add . --list` finds the skill
- [ ] `npm run build` succeeds (if skill has rules/)
- [ ] `npm run format` passes
- [ ] Rule files are 50-70 lines on average
- [ ] Rules focus on terminal output and UX, not verbose source code
- [ ] No hardcoded counts in SKILL.md (they become outdated)
- [ ] `README.md` updated to list the new skill with description and categories
