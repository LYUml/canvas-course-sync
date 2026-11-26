# Organization and Naming

## Folder order

Inventory the actual course activities first. Numeric prefixes express navigation order, not fixed category IDs. Put course information first, followed by teaching materials, practice, and other activities in a useful learning order. For example:

```text
00_info/
01_lec/
02_tut/
03_adaptive_learning/
04_project/
05_lab/
97_recording/
99_final/
```

Adapt this example: a course may instead need assignments, readings, or midterms. Create only useful categories with content; keep questions and solutions together. Preserve established numbering on updates, adding unused prefixes without renumbering to close gaps. Record category purposes in the index.

## File names and moves

- Inspect page context and file contents to identify type, number, topic, term, and question/solution role. Use concise names such as `L01_Introduction.pdf`, `T02_Solutions.pdf`, or `Midterm_2026-27_Sem1_Questions.pdf`.
- Preserve extensions and source language. Do not invent unknown topics or confuse week numbers with lecture numbers. Remove path separators and control characters; distinguish collisions with evidenced versions, dates, or source IDs.
- Preserve personal notes, drafts, and project archive internals. When reorganizing existing materials, record old/new paths, verify destination hashes before cleanup, and update identifiable local references. Keep uncertain duplicates.
- Maintain `00_info/FILE_INDEX.md` or the existing index with grouped titles, working relative links, original names, and sources. Store full source/path mappings in the manifest and report unresolved references.
