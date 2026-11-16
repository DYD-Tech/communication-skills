# Communication Skills

[简体中文](README.md) | English

Help agents communicate clearly: organize ideas logically, explain useful terminology, and be concise without losing meaning.

This project covers replies, explanations, documentation, code comments, and handoffs. It assumes an intelligent reader who may be unfamiliar with the field. Good explanations preserve useful concepts and help readers learn them.

Use the word order, phrasing, and names familiar to readers of the target language. Borrowed terms and abbreviations such as AI and token can be natural in Chinese technical writing.

## Quick installation with your agent

Once the repository is published, send this to a coding agent that can access the repository and write local files:

```text
Install from https://github.com/DYD-Tech/communication-skills for my account using doc/installation.en.md. Use skills/clear-communication and rules/English/clear-communication.md. Merge the rule text into persistent instructions and add the instruction to apply the skill on every task. Preserve existing rules and local edits.
Verify the installed files and rule references. Report the paths, source revision,
default-use configuration, and how to confirm activation.
If this environment cannot support user-level installation or persistent instructions,
explain the limitation and provide an available alternative.
```

For a single project, replace “for my user account” with “in this project.” A tag or commit URL selects a particular version. You do not need a marketplace listing to install from the repository.

An ordinary chat interface may lack installation access. See the [installation guide](doc/installation.en.md) for manual steps covering Codex, Claude Code, Cursor, GitHub Copilot, and OpenCode. Installation and default activation are separate checks.

## Project layout

```text
rules/{English,中文}/clear-communication.md  Persistent rules, select one language
skills/中文/clear-communication/  Chinese skill package
skills/clear-communication/     English skill package (same layout)
  SKILL.md                     Runtime instructions in the selected language
  agents/openai.yaml           Allows implicit invocation in Codex
  references/examples.md      Chinese examples, loaded when needed
  references/examples.en.md   English examples, loaded when needed
  references/document-revision.md  Only for an explicitly requested overhaul
AGENTS.md                      Default-use instruction for this project
doc/                           Installation and development documentation
```

Each language package is self-contained. The `doc/` folder is not a runtime dependency and should not be installed with it.

## How it works

This is a foundational communication skill intended for every task. The project's [AGENTS.md](AGENTS.md) directs agents to load the [skill](skills/clear-communication/SKILL.md), reusing current instructions when already in context. You can also explicitly ask an agent to read and apply that file.

Short answers get a lightweight check. Complex content uses three steps: organize, draft, and correct specific defects. The skill does not require extra documents, public checklists, or a prescribed internal reasoning process.

The skill respects the user's audience, language, format, and tone. Automatic discovery makes a skill available; it does not guarantee use on every task. Set up a persistent instruction in the target agent when you want default use. This repository does not modify your global configuration by itself.

## Principles

- Answer the actual question and connect conclusions, reasons, and conditions.
- Keep useful terminology and explain it when context is insufficient.
- Preserve facts, limitations, and uncertainty when shortening text.
- Explain directly; use analogies only when they help or are requested.
- Avoid empty praise, invented jargon, redundant summaries, and mechanical formatting.

## Working in an existing project

No preliminary document cleanup is required. Extract facts without copying unclear prose. During normal maintenance, clarify the small coherent passage already being edited; do not scan or rewrite unrelated material. Preserve recognizable project names, identifiers, and UI labels, explaining them when needed. Respect narrower edit constraints; a broader overhaul remains the user's choice.

This fits into ordinary writing and review, without old-document labels or a recurring cleanup task. The detailed [design rationale](doc/existing-material.md) is currently in Chinese; the runtime rules and optional overhaul guide are in English.

## Languages

Choose the [English skill](skills/clear-communication/SKILL.md) or the [Chinese skill](skills/中文/clear-communication/SKILL.md) and the matching persistent rules. Each package includes its workflow and references. Replies follow the requested or conversational language.

## Status

Version `0.4.0`, 2026-10-25. Initial research, a problem inventory, examples, and evaluation design are available. Independent cross-model effectiveness and overhead experiments have not been completed; the project makes no measured performance claims.

Development records, in Chinese: [problems](doc/problems.md), [research](doc/research.md), [design](doc/design.md), [evaluation](doc/evaluation.md), [maintenance](doc/maintenance.md), and [changelog](doc/changelog.md).
