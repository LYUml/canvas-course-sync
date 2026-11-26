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
~/Courses/2026-27-Sem1/example101 into numbered categories that fit this course and follow a logical learning order.
Rename files based on their contents and update the index.
Preserve my notes and project drafts, and report all moves and renames.
```

You can limit the scope to attachments, a particular week, or recording transcripts. The AI first identifies the course's actual activities, then chooses a useful folder order. Numeric prefixes are for navigation, not fixed category IDs: `03` might be adaptive learning in one course and assignments in another.

For example, a course with adaptive learning, a project, and labs could use:

```text
example101/
├── 00_info/               # Syllabus, FILE_INDEX.md, sync-manifest.json
├── 01_lec/                # Lectures
├── 02_tut/                # Tutorials and matching solutions
├── 03_adaptive_learning/  # Adaptive learning materials
├── 04_project/            # Project briefs, datasets, and templates
├── 05_lab/                # Lab instructions and supporting files
├── 97_recording/          # Transcripts/: original captions and readable text
└── 99_final/              # Final exam papers and solutions
```

This is a reference, not a required layout. A different course might need assignments, readings, or midterms and have no adaptive learning or labs. The AI creates only useful categories, keeps related questions and solutions together, and records the chosen structure in the index. Existing folder names and numbers stay stable during routine updates; new material does not trigger a complete renumbering. Explicit reorganization requests can change the layout while preserving source mappings and updating local references.

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
