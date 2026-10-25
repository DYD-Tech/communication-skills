# Revising an existing document collection

Read this only when the user explicitly requests a broader rewrite, terminology cleanup, or document overhaul. Ordinary maintenance uses the entrypoint's local-edit rule.

## 1. Establish the scope and meaning

Use the requested audience, files, and goals. If scope is already explicit, proceed without asking for it again. Resolve only ambiguities that would materially change the work. Full wording cleanup does not by itself authorize changing behavior, requirements, public names, or historical records.

Inspect the selected material and its relevant references. Identify the facts, conditions, decisions, and exceptions that must survive. Where several files use an opaque term, establish whether it names a real object or merely obscures a claim. Use definitions, implementation, and authoritative project decisions when needed; do not infer intended behavior from polished wording.

**Output:** a short scoped plan using existing task notes. Record terminology decisions only where shared usage or ambiguity makes them necessary. Distinguish editorial changes from unresolved factual questions.

## 2. Rewrite in coherent batches

Group work by topic or dependency rather than an arbitrary file count. Each batch should be reviewable and leave a usable, internally consistent result. Complete all authorized batches; batching is not a reason to stop after a sample or ask permission for each file.

Preserve identifiers and established names unless renaming is part of the authorized work. When a rename is requested, map old and new names and update affected references together; retain an alias or explanation where needed for search and recognition. Do not create competing definitions during the transition.

Keep wording cleanup separate from behavior or requirement changes in the diff when possible. Do not alter executable code, directives, examples that must match exact output, or historical quotations merely to improve prose. Edit the source of generated documentation if that is in scope; otherwise leave generated output alone.

**Output:** revised passages or files, with unresolved factual issues kept distinct from completed editorial work. Preserve original text where an uncertain interpretation would change meaning; identify the precise uncertainty rather than inventing a confident rewrite.

## 3. Verify meaning and references, then finish

Compare each batch with its source: check claims, numbers, conditions, exceptions, commitments, and terminology. Check links and anchors affected by changes. If comments or documentation are consumed by tools, run the relevant existing checks. Do not add unrelated tests just for prose.

Use a small sample to calibrate tone if helpful, then apply the agreed or clearly requested style to the rest. A checkpoint requires user input only when a real decision remains unresolved, not merely because the next batch exists.

**Output:** the completed revision, a concise summary of substantive terminology or structural changes, and any unresolved issues. Do not claim the whole collection was reviewed when only a subset was covered. No recurring cleanup schedule, per-file quality labels, or new approval process is implied.
