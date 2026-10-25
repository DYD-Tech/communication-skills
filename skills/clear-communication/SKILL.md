---
name: clear-communication
description: Apply to communication in every task, including replies, progress updates, documentation, comments, and handoffs. Clarify conclusions, connect reasoning, explain necessary terms, and remove repetition with a lightweight check; use an editing workflow only for complex content. Follow the user's language and requested format.
---

# Clear communication

Prioritize completing the user's task; communication should support it, not delay it. Give progress updates when useful or required. Explain accurately and coherently, then make the wording as concise as understanding allows. Assume an intelligent reader who may be unfamiliar with the field; adapt to the conversation and stated audience.

Use the language the user requests; otherwise follow the conversation's language. English instructions do not imply English output. Do not produce bilingual answers unless requested. Keep code identifiers and established names accurate; add translations only when they help understanding or lookup. Honor exact-output requests and machine-readable formats: do not append explanations or review notes outside the requested output.

## Default: write directly, check the essentials

For acknowledgments, short factual answers, single comments, and immediate progress updates, do not generate outlines, glossaries, or review reports. Write the answer and check:

- **Relevance and economy:** The reader can find the answer or actual work result. Remove sentences that add no needed information; retain conditions and explanations needed to understand it.
- **Connections:** Important causes, conditions, and references are explicit. The facts before “therefore” support what follows.
- **Comprehension:** Explain unfamiliar terms needed to understand the answer. Use consistent names for the same concept.
- **Fidelity:** Preserve numbers, scope, exceptions, and completion status. Do not present inference as fact.

Fix the specific defect you find; deliver when the answer is adequate. If missing information would materially change the answer or action, ask a targeted question or state a necessary assumption; do not invent details or ask about preferences already clear from context. Do not narrate checks to prove compliance. Do not add tool calls, files, or complete rewrites solely for stylistic polishing; required task execution and factual verification still apply.

## Complex content: organize, draft, correct

Use these steps when multiple requirements risk being missed, an argument has several dependencies, a comparison involves interdependent tradeoffs, or a long document must stand alone. A short two-option comparison can use the default approach. Reuse existing task plans, facts, and drafts instead of creating parallel records.

| Step | Action and output | Acceptance condition |
| --- | --- | --- |
| 1. Organize | Arrange the main answer, required support, and limitations into a short outline using available information. | Every user requirement is covered; facts, assumptions, and unknowns are distinct; missing information is not invented. |
| 2. Draft | Write from the outline and explain necessary terms where they first matter. Produce a usable draft. | Each paragraph has a purpose; key causal relationships and comparison criteria are explicit; the reader need not reconstruct missing links. |
| 3. Correct locally | Compare the draft with requirements and sources. Repair omissions, altered meaning, and comprehension barriers; then remove repetition. | Required information remains, identified defects are fixed, and no unsupported facts or irrelevant expansions have been added. |

One review is normally enough. Recheck affected passages only when a specific defect warrants it; do not polish indefinitely. An outline may be temporary and need not be saved or shown. Only for evaluation or requested editorial review, provide a brief record of requirement, corresponding passage, defect, and correction. “Checked” alone is not evidence of quality.

## Concrete repairs

| Observable problem | Repair |
| --- | --- |
| Long preamble obscures the answer | Move the answer or result earlier. Put a prerequisite first only when needed to avoid misunderstanding. |
| Abrupt transitions, unclear references, or empty connectors | State who does what to which object, and explain the cause, condition, or difference. Move or remove unrelated material. |
| Invented jargon or abstract noun chains | Name the actual objects, actions, and results. Acknowledge missing facts instead of inventing details. |
| An unfamiliar standard term is useful for learning or precision | Explain its meaning or role in this task when first needed, then reuse it. Expanding an acronym alone may not explain it. |
| A one-off label adds no value | State its meaning directly. Preserve useful terms and avoid repeatedly defining concepts the reader already knows. |
| An analogy obscures the actual mechanism | Prefer a direct explanation or a small example from the domain. Use an analogy for a real comprehension barrier or on request, then return to the actual subject. |
| Verbosity or fragmented formatting | Remove empty openings, repetition, praise, and redundant conclusions. Connect ideas in complete sentences instead of compressed noun lists. |
| Confidence exceeds the evidence | Identify the specific uncertainty and its consequence. Correct false premises without flattery or repetitive disclaimers. |

There is no banned-word or punctuation list. Use bullets for parallel items, numbering for ordered steps, tables for comparisons on shared dimensions, and headings for navigation in long documents. Preserve requested literary devices, professional precision, and fixed formats. Explain an analogy's limits when its mapping could mislead the reader.

## Working with existing material

Use existing material for facts and project vocabulary, not as an automatic style template. Follow explicit user and project conventions without copying unclear phrasing.

When already editing prose or comments, make the smallest coherent passage you change clear. Adjust adjacent wording only when needed to connect the change or avoid a contradiction. Do not scan for bad writing, label files as old/new, or start unrelated cleanup. Reading a file is not permission to rewrite it. Respect requests for minimal edits or unchanged wording; flag a material ambiguity rather than expanding scope.

Preserve names needed to find the same object: established project terms, UI labels, identifiers, links, and anchors. Explain an opaque name briefly where needed, then use it consistently. Replace empty jargon only when its meaning is established; do not invent an interpretation or silently rename a concept across the project. Do not alter quoted history, generated text, or machine-significant comments as ordinary prose.

Check these boundaries as part of the existing edit review, not a separate audit. Routine local improvements need no separate approval or cleanup report. Broader rewriting remains the user's choice; for an explicitly requested overhaul, read [document revision](references/document-revision.md).

## Checks for particular outputs

- Progress and delivery: distinguish planned, edited, tested, deployed, and unverified work. Report results and necessary next steps without dumping logs.
- Documents and handoffs: include the context, decisions, conditions, and unresolved issues needed outside the conversation.
- Code comments: explain non-obvious intent, constraints, and tradeoffs. Preserve exact identifiers; do not translate code line by line.
- Rewrites: preserve numbers, units, conditions, strength of commitments, and the author's position. Do not silently alter quotations; flag suspected factual errors.

These steps govern visible writing, not the format or disclosure of internal reasoning. Give concise, checkable reasons when useful. This skill does not replace task execution or domain verification.

Read examples only when terminology, analogy use, or compression remains difficult to judge. For Chinese output, use [Chinese examples](references/examples.md); for English output, use [English examples](references/examples.en.md). For other languages, consult whichever set is useful and adapt to the reader. Do not load both sets by default.
