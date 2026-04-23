# Solv Claude Skills

Shared Claude Code skills for the Solv Health revenue team.

## What is a skill?

A skill is a markdown file (`SKILL.md`) that gives Claude specialized instructions for a specific workflow. Once installed, Claude automatically uses the skill when you ask for something that matches it.

## How to install a skill

1. Copy the skill folder (e.g., `monarch-deal-analysis/`) into your project's `.claude/skills/` directory:
   ```
   your-project/
   └── .claude/
       └── skills/
           └── monarch-deal-analysis/
               └── SKILL.md
   ```
2. Restart Claude Code (or start a new conversation). The skill will appear in your available skills list.

## Available Skills

### `monarch-deal-analysis`
Pulls context from Slack (`#mon-prosp-*`), Granola, and Gong to generate leadership-ready Monarch deal summaries. Produces a per-deal executive summary (< 300 words) and a one-slide pipeline table.

**Trigger phrases:** "update my Monarch deals", "give me a pipeline summary", "pull together a leadership update"

---

### `skill-creator`
Helps you build new skills from scratch — interviews you on the workflow, writes a draft, runs test cases, and iterates based on your feedback.

**Trigger phrases:** "create a skill for X", "turn this into a skill", "help me make a skill"

---

## Adding your own skill

1. Create a folder under `.claude/skills/` with your skill name
2. Write a `SKILL.md` with frontmatter (`name`, `description`) and instructions
3. Open a PR to this repo so the team can use it too
