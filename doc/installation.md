# 安装与默认启用

简体中文 | [English](installation.en.md)

核对日期：2026-10-24。覆盖 Codex、Claude Code、Cursor、GitHub Copilot 和 OpenCode。路径与功能依据下方官方文档核对，未在这五种客户端分别进行安装实测。

## 推荐方式：给 agent 链接和明确要求

使用 [README 中的安装提示](../README.md)。公开仓库地址足以定位源码；同时给出 `skills/clear-communication` 可避免装错目录。只发链接可能被理解为阅读请求，因此应明确说“安装，并设为每次任务默认应用”。

安装者应按以下步骤处理：

1. 确认目标 agent、个人或项目范围，以及仓库版本。使用当前宿主的信息；只有无法判断时再询问，不能凭模型名称猜宿主。
2. 获取并检查 `skills/clear-communication/`。把完整目录安装到宿主支持的位置，保留 `SKILL.md`、`references/` 和 `agents/`；首次安装不需要执行项目脚本。
3. 按用户请求添加默认应用规则。只合并与此技能有关的内容，保留现有规则；目标已有同名技能时先比较，不能直接覆盖本地改动。不复制本仓库根目录的 `AGENTS.md`，其中包含本项目的开发约定。
4. 检查安装路径、文件完整性和规则引用。报告来源 tag 或 commit（可取得时）、修改的文件，以及是否还需新会话或界面操作。不能用下载完成替代启用验证。

网络或文件权限不足时，报告具体未完成项。不要把安装在临时沙箱中的文件描述为用户电脑上的永久安装；云端 agent 也不一定能访问本机的个人技能目录。

## 手动安装：复制完整文件夹

下载仓库 ZIP 并解压，或用 Git 克隆仓库。从中找到 `skills/clear-communication/`，复制到下表选定的位置。个人范围适合自己的多个项目；项目范围适合随代码共享给团队。选一个范围即可，避免无意中保留多个同名副本。

路径以 `clear-communication` 结尾，复制后应当直接包含 `SKILL.md`，不要多套一层同名文件夹。`~` 表示用户主目录，Windows 通常对应 `%USERPROFILE%`，PowerShell 中可通过 `$HOME` 查看；项目路径相对于使用技能的项目根目录。

| Agent | 个人安装目录 | 项目安装目录 | 官方依据 |
| --- | --- | --- | --- |
| Codex | `~/.agents/skills/clear-communication/` | `.agents/skills/clear-communication/` | [Build skills](https://learn.chatgpt.com/docs/build-skills) |
| Claude Code | `~/.claude/skills/clear-communication/` | `.claude/skills/clear-communication/` | [Claude Code skills](https://code.claude.com/docs/en/skills) |
| Cursor | `~/.cursor/skills/clear-communication/` | `.cursor/skills/clear-communication/` | [Cursor skills](https://cursor.com/docs/skills) |
| GitHub Copilot | `~/.copilot/skills/clear-communication/` | `.github/skills/clear-communication/` | [Copilot 安装技能](https://docs.github.com/en/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/add-skills) |
| OpenCode | `~/.config/opencode/skills/clear-communication/` | `.opencode/skills/clear-communication/` | [OpenCode skills](https://docs.opencode.ai/docs/skills/) |

本表列出一组明确路径，不罗列所有兼容目录。已有版本的安装器可能选择其他兼容位置，例如本项目开发环境的 Codex skill-installer 默认使用 `$CODEX_HOME/skills`。使用内置安装器时记录其实际目标，并在客户端验证发现结果，不要为匹配表格再安装第二份。

## 默认应用：再添加一条常驻规则

自动发现只表示技能可被选择，不等于每次都会使用。本技能中的 `agents/openai.yaml` 允许 Codex 自动调用，但不会替用户设置跨项目常驻规则。规则的作用是要求加载，具体写法仍由技能文件维护，避免复制整份技能后难以同步更新。

把下列内容添加到相应规则位置，将占位符换成安装后的真实路径。个人安装推荐写实际绝对路径；项目安装写相对于项目根目录的路径，并明确这是项目根路径。

```text
每次任务都应用 clear-communication 技能。入口：<已安装技能的 SKILL.md 路径>。
开始工作时加载；上下文已有最新内容时复用，内容更新或丢失后重新读取。
短答直接写并轻量检查，复杂内容按技能整理与修正；不额外展示检查流程。
```

### Codex

个人规则合并到 `~/.codex/AGENTS.md`；项目规则合并到项目根目录 `AGENTS.md`。保留其他规则及可能存在的 override 配置。首次安装可新开会话检查技能是否出现；若未出现，再检查发现目录与禁用设置。也可明确请求使用 `$clear-communication` 验证加载。[官方定制说明](https://learn.chatgpt.com/docs/customization/overview)

### Claude Code

个人规则合并到 `~/.claude/CLAUDE.md`；项目规则合并到根目录 `CLAUDE.md`。规则引用所选范围内的技能路径。可在新会话中尝试 `/clear-communication`；成功明确调用只证明可加载，仍应单独检查默认应用。[Claude Code 记忆与规则](https://code.claude.com/docs/en/memory)

### Cursor

个人范围在 Cursor 的 User Rules 中添加上述规则；如果 agent 无法修改该界面，让它给出需要粘贴的文本。项目范围可新增 `.cursor/rules/clear-communication.mdc`，内容如下。`alwaysApply: true` 让这条入口规则持续适用；它不保证模型每次严格遵循技能。[Cursor rules](https://cursor.com/docs/rules)

```markdown
---
description: Apply clear-communication to each task
alwaysApply: true
---
每次任务都读取并应用项目根目录下的 .cursor/skills/clear-communication/SKILL.md。
上下文已有最新内容时复用。短答轻量检查，复杂内容才整理与修正，不展示检查流程。
```

上面是项目安装示例；若安装在个人目录，不要原样引用项目路径。Cursor 的云端与远程环境需另行确认技能同步或项目文件是否可访问，不能把本机安装视为云端安装。

### GitHub Copilot

推荐先完成项目安装，再把默认应用规则合并到 `.github/copilot-instructions.md`，引用项目根目录下的 `.github/skills/clear-communication/SKILL.md`。个人技能可以跨项目复用，但不同 Copilot 客户端的个人指令入口不完全相同，需按实际客户端配置；本指南不假定存在一个所有客户端通用的个人规则文件。[VS Code 自定义指令](https://code.visualstudio.com/docs/agent-customization/custom-instructions)

云端运行时应让技能和规则文件可在目标仓库中读取；本机个人目录不能替代仓库配置。IDE 版本与运行界面的支持范围以其文档为准。[Copilot 技能支持范围](https://docs.github.com/en/copilot/concepts/customizations/agent-skills)

### OpenCode

个人规则合并到 `~/.config/opencode/AGENTS.md`；项目规则合并到项目根目录 `AGENTS.md`。引用对应技能入口，并检查当前 agent 的 skill 权限是否允许加载。不要为安装此技能改变其他技能权限。[OpenCode rules](https://docs.opencode.ai/docs/rules/)

## 验证、更新与卸载

安装后检查三个不同层次：

1. **文件完整：** 安装目录直接含 `SKILL.md`，示例文件存在，规则中的路径可访问。
2. **可以加载：** 新会话中查看技能列表或加载记录；如果宿主支持明确调用，先调用一次。不能只依据模型说“我已经会了”。
3. **默认应用：** 再开一个未点名技能的任务，例如“给外行解释：客户端超时不等于服务端没执行，两句话即可”。若有可用记录，核对规则和技能是否加载，并检查答案。单次答得好不能证明以后都会遵循；无可用加载记录时明确写“行为观察通过，自动加载未独立确认”。

后续更新时比较已安装副本与新版本，保留用户改动，更新同一安装位置，并记录新来源版本；无需重复追加常驻规则。若要可复现，使用指定 tag 或 commit，不把分支地址当成固定版本。

卸载时移除自己安装的 `clear-communication/` 目录，并删掉对应入口规则，保留其他技能与规则。无需删除整个 `.agents`、`.claude` 或其他宿主配置目录。

## 发布前维护者要做什么

仓库地址为 `https://github.com/DYD-Tech/communication-skills`，本地远程地址为 `git@github.com:DYD-Tech/communication-skills.git`。README 使用 HTTPS 地址，方便公开访问；本地有 SSH 权限的安装者也可使用 SSH。文件上传后再检查公开可访问性、默认分支及 `skills/clear-communication/` 路径；目前不声称远程已有这些文件。不需要为了链接安装重排目录，也不需要先增加安装脚本或插件市场清单。

本文件是安装指导，不是技能运行依赖。安装提示要求 agent 读取它，是为明确目录、范围和验证方法；日常使用不需要再次加载。
