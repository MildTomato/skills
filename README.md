# Agent Skills

A collection of skills for AI coding agents. Skills are packaged instructions
and scripts that extend agent capabilities.

Skills follow the [Agent Skills](https://agentskills.io/) format.

## Available Skills

### cli-guidelines

Design and build well-crafted command-line interfaces following modern best
practices. Based on the [Command Line Interface Guidelines](https://clig.dev/).
Focused, actionable rules prioritized by impact.

**Use when:**

- Creating CLI tools or adding commands/subcommands
- Implementing help text and error handling
- Parsing arguments and flags
- Designing interactive prompts
- Improving CLI UX and output formatting
- Reviewing or refactoring CLI code

**Categories covered:**

- **The Basics** (CRITICAL) - Argument parsing, exit codes, stdout/stderr
- **AI Agent Integration** (CRITICAL) - JSON output, structured errors, --yes flag
- **Help & Documentation** (CRITICAL) - Concise help, examples, suggestions
- **Output Formatting** (HIGH) - TTY detection, JSON/plain output, paging
- **Error Handling** (HIGH) - Human-friendly errors, signal-to-noise
- **Arguments & Flags** (HIGH) - Prefer flags, standard names, secrets
- **Interactivity** (HIGH) - TTY checks, --no-input, password handling
- **Signals & Control** (HIGH) - Ctrl-C handling, crash-only design
- **Robustness** (MEDIUM-HIGH) - Progress, validation, timeouts, idempotency
- **Subcommands** (MEDIUM-HIGH) - Consistency, verbs, no catch-alls
- **Configuration** (MEDIUM) - Precedence, XDG spec
- **Future-proofing** (MEDIUM) - Additive changes, deprecation
- **Naming & Distribution** (LOW-MEDIUM) - Simple names, single binary

### docs-writer

Standards for writing, reviewing, and editing documentation. Covers voice and
tone, language and grammar, formatting, structure, and verification.

**Use when:**

- Writing or editing documentation
- Working with `.md` or `.mdx` files
- Reviewing docs for style and consistency

**Phases covered:**

- **Documentation standards** - Voice, tone, grammar, formatting, structure
- **Preparation** - Clarify, investigate, audit, plan
- **Execution** - Gaps, structure, tone, clarity, consistency
- **Verification** - Accuracy, self-review, link checks

## Installation

```bash
# Install a specific skill
npx skills add MildTomato/agent-skills --skill cli-guidelines
npx skills add MildTomato/agent-skills --skill docs-writer

# Install all skills
npx skills add MildTomato/agent-skills
```

## Usage

Skills are automatically available once installed. The agent uses them when
relevant tasks are detected.

**Examples:**

```
Create a CLI tool with proper help text and error handling
```

```
Review this documentation for style and consistency
```

## Skill Structure

Each skill contains:

- `SKILL.md` - Instructions for the agent (required)
- `metadata.json` - Version and metadata (required)
- `rules/` - Focused, actionable rule files (optional)
- `references/` - Background documentation (optional)
- `scripts/` - Helper scripts for automation (optional)

See [CLAUDE.md](CLAUDE.md) for detailed contribution guidelines.

## License

MIT
