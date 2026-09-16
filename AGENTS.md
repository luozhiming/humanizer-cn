# Guide for agents

This file explains how to change Humanizer without breaking its package or prompt.

## What this repo contains

Humanizer is an agent skill written in Markdown. `SKILL.md` is the prompt that agents read. The repo has no build step.

Keep the skill portable. Do not write instructions that limit it to one or two agent tools.

## Key files

- `SKILL.md` is the source of truth and the repo's only skill file. It contains portable YAML metadata, an account of why AI text sounds the way it does, and numbered patterns grouped in five sections and ordered by strength and frequency. The prompt is written in Chinese and targets Chinese text.
- `README.md` explains installation, use, patterns, and version history.
- `scripts/validate-package.py` checks package files and shared values.

The repo ships with no store listing and no agent-specific files. Install by copying `SKILL.md` (or the folder) into the agent's skill directory.

## Rules for changes

Keep `SKILL.md` and `README.md` in sync.

- **Patterns:** Patterns are numbered from 1 without gaps, strongest and most frequent first. A new tell earns a pattern only when no existing pattern already implies it; prefer folding it into an existing pattern. If you add, remove, or renumber a pattern, update the README tables, the README section title, and every §reference. The validator derives the count from the headings.
- **Version:** Keep the same version in `SKILL.md` under `metadata.version` and the first README version entry. Do not add a top-level `version` field to the skill.
- **Compatibility:** Keep install and use instructions neutral across agents. Names such as QwenWork, Claude Code, OpenCode, and Codex are examples, not limits.
- **History:** Add a short README version note for any behavior change or non-obvious fix.
- **Checks:** Before shipping a change, run `python3 scripts/validate-package.py`.

## Writing style

Use Plain Language in code comments, prompts, documentation, descriptions, validation messages, and progress reports. The skill prompt and README are written in Chinese; apply the same principles there: lead with the main point, prefer common words and short sentences, and keep one term for the same item.

- Lead with the main point.
- Use common words and active voice.
- Keep sentences and paragraphs short.
- Use one term for the same item.
- Use `must` for requirements.
- Use headings, lists, and tables when they help the reader.
- Remove repeated or unnecessary words.
- Limit acronyms and explain technical terms.
- Avoid double negatives.
- Keep exact identifiers, commands, paths, schema fields, quotations, watched phrases, and behavior-bearing examples.
- Keep the full technical meaning.

## Editing the skill

- Keep the YAML metadata valid.
- Treat the prompt below the metadata as the product.
- Prefer a short, clear instruction over another exception or repeated explanation.
