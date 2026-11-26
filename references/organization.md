# Organization and Naming

## Numbered categories

Use this structure for new courses, creating only categories that have content. Preserve existing numbering and abbreviations. When the user requests reorganization, move files according to their contents and update source records and identifiable local references.

```text
<course>/
├── 00_info/           # Syllabus, schedule, manifest, and file index
├── 01_lec/            # Lectures; Revision/ for revision materials
├── 02_tut/            # Tutorials, exercises, and matching solutions
├── 03_ass/            # Assignment briefs, templates, and attachments
├── 04_project/        # Project briefs, datasets, templates, and references
├── 05_recording/      # Recording sources; Transcripts/ for captions and text
├── 06_reading/        # Readings and supplementary references
├── 98_midterm/        # Midterm papers and solutions
└── 99_final/          # Final exam papers and solutions
```

Do not create empty categories for unpublished materials. Preserve original project archives and internal code paths. If extraction is needed, use a separate subdirectory rather than renaming individual internal files.

## Content-based names

Read the page context, then inspect the file's first page, title, or relevant text to identify its type, number, topic, term, and question/solution role. Use concise, sortable names and preserve extensions. Record the original name, source, and new path in the manifest.

| Material | Example names |
| --- | --- |
| Lecture | `L01_Introduction.pdf` |
| Weekly lecture | `W03_Heat_Transfer.pdf` |
| Tutorial and solutions | `T02_Questions.pdf`, `T02_Solutions.pdf` |
| Assignment | `A01_Brief.pdf`, `A01_Template.xlsx` |
| Project | `Project_Brief.pdf`, `Project_Dataset.zip` |
| Midterm and solutions | `Midterm_2026-27_Sem1_Questions.pdf`, `Midterm_2026-27_Sem1_Solutions.pdf` |

Lecture numbers and week numbers are distinct; do not infer one from the other. When a topic is unknown, retain the known number and useful parts of the original title. Source titles may keep their original language; translation is not required. Remove path separators and control characters from filenames. Resolve different content with the same name using an evidenced date, version, or short source ID, without overwriting.

## Existing files and indexes

- Routine synchronization organizes newly downloaded or updated instructor materials. Reorganize existing materials when requested. Preserve personal notes, drafts, their content, and user-chosen names.
- Record old and new paths and the reason before moving. Verify destination contents and hashes before cleaning up old locations. Preserve uncertain duplicates; never delete based only on matching names.
- Keep complete source/path mappings in the manifest. Maintain a readable `00_info/FILE_INDEX.md`, or update the existing index. Group entries by category with titles, relative file links, original names, and sources. Link only to files that actually exist.
- Verify moved files and index links. Update identifiable references in local course documents. Report external references that cannot be reliably updated without claiming all references were repaired.
