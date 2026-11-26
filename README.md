# Canvas Course Sync

An AI skill that downloads Canvas course materials, organizes them into numbered folders, renames files based on their contents, and maintains a readable file index. Later runs fetch missing or updated materials while avoiding unnecessary duplicates.

This repository provides instructions for Codex with browser or connector access and local file tools. It is not a standalone downloader or background service.

## Features

- Discover attachments in Modules, Announcements, Assignments, Files, and linked course pages.
- Use AI to identify lectures, tutorials, solutions, assignments, projects, and exams from page context and file contents, then categorize and rename them.
- Compare SHA-256 hashes, deduplicate identical content, and preserve previous versions and personal notes.
- Sync existing Zoom and Panopto captions and transcripts, retaining original subtitles and producing readable TXT files with origin and completeness information.
- Maintain a sync manifest and file index with sources, original names, destination paths, and failure reasons so interrupted work can resume.

Recordings without published captions are not reported as transcribed. Local speech recognition requires separate confirmation of tools, audio access, and possible costs. Recurring runs are configured only when requested.

## Installation

With Git available, clone the repository into your Codex skills directory:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/LYUml/canvas-course-sync.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/canvas-course-sync"
```

If the destination already exists, check for local changes before modifying it. To update a Git installation, run `git pull --ff-only` inside that directory.

Start a new Codex session and invoke `$canvas-course-sync`. Before syncing, have an authenticated Canvas session and a writable local course directory ready. Browser access and download support depend on the current Codex environment; the AI will report missing capabilities when necessary.

## Usage

For the first sync, provide the Canvas URL, course code, term, and destination:

```text
Use $canvas-course-sync to sync EXAMPLE101, 2026-27 Sem1,
from https://canvas.example.edu into ~/Courses/2026-27-Sem1/example101.
Organize files into numbered folders, rename them based on their contents,
and generate a file index.
```

For incremental updates:

```text
Use $canvas-course-sync to update ~/Courses/2026-27-Sem1/example101.
Check for new attachments and recording transcripts, and report anything unavailable.
```

To organize existing materials:

```text
Use $canvas-course-sync to organize existing instructor materials in
~/Courses/2026-27-Sem1/example101 into 01, 02, 03, 04 categories.
Rename files based on their contents and update the index.
Preserve my notes and project drafts, and report all moves and renames.
```

You can limit the scope to attachments, a particular week, or recording transcripts. The AI follows existing conventions; new courses use the categories below as needed:

```text
example101/
├── 00_info/           # Syllabus, FILE_INDEX.md, sync-manifest.json
├── 01_lec/            # L01_Introduction.pdf
├── 02_tut/            # T01_Questions.pdf, T01_Solutions.pdf
├── 03_ass/            # A01_Brief.pdf, A01_Template.xlsx
├── 04_project/        # Project briefs, datasets, and templates
├── 05_recording/      # Transcripts/: original captions and readable text
├── 06_reading/        # Readings
├── 98_midterm/        # Midterm papers and solutions
└── 99_final/          # Final exam papers and solutions
```

Classification uses actual contents, not just filenames. For example, after its first page confirms it is a midterm paper, `Test.pdf` can become `98_midterm/Midterm_2026-27_Sem1_Questions.pdf`. Unknown lecture numbers, topics, and terms are not invented. Internal project archive structures are preserved.

## Sync results

Each run reports its checked scope, additions, updates, unchanged files, unavailable items, and actual destination paths. Partial transcripts, expired sessions, denied access, and processing recordings are tracked separately. Unchecked entry points are not counted as complete. Local copies are preserved when remote materials disappear.

Course files and sync records belong in the selected course directory, not this skill repository. Credentials and signed temporary download URLs must not be included in public records.

## Repository structure

- [SKILL.md](SKILL.md): AI execution entry point.
- [Organization and naming](references/organization.md): numbered categories, content-based names, and indexes.
- [Manifest conventions](references/manifest.md): incremental states, source mappings, and recovery.
- [Recording transcripts](references/transcripts.md): Zoom/Panopto retrieval and validation.
- [Local conventions](references/local-conventions.md): original author's historical examples, used only when local evidence matches.
- [agents/openai.yaml](agents/openai.yaml): skill display metadata.
