# Installation and default activation

[简体中文](installation.md) | English

Documentation checked on 2026-10-24. These instructions cover Codex, Claude Code, Cursor, GitHub Copilot, and OpenCode. Paths were checked against the linked official documentation, but installation has not been tested separately in all five clients.

## Let your agent install it

Use the [README installation prompt](../README.en.md). The repository is `https://github.com/DYD-Tech/communication-skills`; install the folder `skills/clear-communication`. Authorized SSH users may use `git@github.com:DYD-Tech/communication-skills.git`. Repository files must be published before remote installation can work.

Give an explicit installation request, scope, and default-use preference. A bare link may be treated as a request to read the repository.

The installing agent should:

1. Identify the host, installation scope, and source revision. Use available context; ask only if needed. A model name does not identify its host application.
2. Inspect and copy the complete skill folder, including `SKILL.md`, `references/`, and `agents/`. No project scripts are required for initial installation.
3. Add the requested persistent instruction without replacing unrelated rules. Compare an existing skill before overwriting local changes. Do not copy the repository's root `AGENTS.md`, which contains project development instructions.
4. Verify files and rule references. Report the actual paths, source tag or commit when available, and any remaining session or UI steps. Download success is not activation verification.

Report network or permission limitations precisely. Files in a temporary sandbox are not a permanent installation on the user's computer. Cloud agents may not have access to local personal skills.

## Manual installation

Download and extract the repository ZIP, or clone it with Git. Copy the complete `skills/clear-communication/` folder to one of the locations below. Choose user scope for your projects or project scope for a shared repository; avoid accidental duplicate installations.

The destination must directly contain `SKILL.md`, without another nested `clear-communication` folder. `~` means your home directory, typically `%USERPROFILE%` on Windows; PowerShell exposes it through `$HOME`. Project paths are relative to the consuming project's root.

| Agent | User directory | Project directory | Official documentation |
| --- | --- | --- | --- |
| Codex | `~/.agents/skills/clear-communication/` | `.agents/skills/clear-communication/` | [Build skills](https://learn.chatgpt.com/docs/build-skills) |
| Claude Code | `~/.claude/skills/clear-communication/` | `.claude/skills/clear-communication/` | [Skills](https://code.claude.com/docs/en/skills) |
| Cursor | `~/.cursor/skills/clear-communication/` | `.cursor/skills/clear-communication/` | [Skills](https://cursor.com/docs/skills) |
| GitHub Copilot | `~/.copilot/skills/clear-communication/` | `.github/skills/clear-communication/` | [Add skills](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills) |
| OpenCode | `~/.config/opencode/skills/clear-communication/` | `.opencode/skills/clear-communication/` | [Skills](https://docs.opencode.ai/docs/skills/) |

These are selected supported paths, not an exhaustive list. An installed helper may choose a different compatible location; the Codex installer in this project's development environment uses `$CODEX_HOME/skills`. Record the actual destination and verify discovery instead of installing a second copy just to match the table.

## Apply it by default

Discovery makes a skill available for selection; it does not guarantee use in every task. The included `agents/openai.yaml` allows Codex implicit invocation but does not configure persistent instructions for the user.

Add this short instruction in the appropriate location below. Replace the placeholder with the real installed entry path. Use an absolute path for a personal installation, or explicitly identify a path relative to the project root.

```text
Apply clear-communication to every task. Entry: <installed SKILL.md path>.
Load it when starting work; reuse the current version already in context.
Reload after changes or context loss. Use a lightweight check for short answers
and the skill's editing steps for complex content. Do not narrate the checks.
```

### Codex

Merge personal instructions into `~/.codex/AGENTS.md`, or project instructions into the root `AGENTS.md`. Preserve other rules and account for existing overrides. Start a new session to check discovery; inspect supported paths and disabled settings if it is missing. Explicit `$clear-communication` invocation can test loading, separately from default use. [Customization](https://learn.chatgpt.com/docs/customization/overview)

### Claude Code

Merge personal instructions into `~/.claude/CLAUDE.md`, or project instructions into root `CLAUDE.md`, referencing the installed entry. Try `/clear-communication` in a new session to test explicit loading; check default use separately. [Memory and instructions](https://code.claude.com/docs/en/memory)

### Cursor

For personal use, add the instruction to User Rules. If the agent cannot edit that UI, it should provide the text for you to paste. For project use, create `.cursor/rules/clear-communication.mdc` as below. [Rules](https://cursor.com/docs/rules)

```markdown
---
description: Apply clear-communication to each task
alwaysApply: true
---
Apply the skill at .cursor/skills/clear-communication/SKILL.md, relative to the
project root, on every task. Reuse current instructions already in context.
Check short answers lightly; organize and revise complex content without narrating checks.
```

This example assumes project installation. Use the actual personal path for user-level installation. Always applying the entry rule does not guarantee perfect adherence. Check synchronization or repository access separately for cloud and remote environments.

### GitHub Copilot

A project installation is a straightforward starting point. Merge the default-use instruction into `.github/copilot-instructions.md`, referencing `.github/skills/clear-communication/SKILL.md` from the project root. Personal instruction entry points differ across clients; do not assume one global rules file works everywhere. [VS Code custom instructions](https://code.visualstudio.com/docs/agent-customization/custom-instructions)

Cloud execution requires accessible repository skills and rules; local personal files are not a substitute. Check the actual IDE version and surface. [Supported surfaces](https://docs.github.com/en/copilot/concepts/customizations/agent-skills)

### OpenCode

Merge personal rules into `~/.config/opencode/AGENTS.md`, or project rules into root `AGENTS.md`. Reference the corresponding skill path and check that the active agent permits skill loading. Do not change unrelated skill permissions. [Rules](https://docs.opencode.ai/docs/rules/)

## Verify, update, and remove

Verify three things separately:

1. **Files:** The entry and examples exist, and the persistent rule references a readable path.
2. **Loading:** Check the skill list or loading record in a new session; try explicit invocation if supported. The model saying “installed” is not sufficient evidence.
3. **Default use:** In another new session, ask a normal question without naming the skill, such as “Explain why a client timeout does not mean the server did nothing, in two sentences for a nontechnical reader.” Check loading records when available and inspect the answer. A good answer alone does not prove automatic loading or future adherence.

When updating, compare local changes, update the same installation, and record the new source revision. Do not append duplicate rules. Use a tag or commit for reproducibility; a branch URL is not a fixed revision.

To uninstall, remove only the installed `clear-communication/` directory and its persistent entry instruction. Keep other skills and host configuration intact.

## Before publication

After uploading, verify public access, the default branch, and the skill directory. The current layout supports link-based installation without an installation script or marketplace manifest. This guide is installation documentation, not a runtime dependency.
