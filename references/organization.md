# Organization and Naming

## Numbered categories

Treat numeric prefixes as navigation order, not fixed category IDs. First inventory the course's actual material types and learning activities, then choose a small set of meaningful categories. Preserve existing numbering and abbreviations unless the user requests reorganization.

For a new course, place course information first (usually `00_info`), followed by the core teaching materials and their associated practice. Order other activities such as adaptive learning, assignments, projects, and labs according to the course structure and how students use them. There is no universal rule that assignments must be `03` or recordings must be `05`. Keep supporting resources and exam preparation easy to find; high prefixes such as `97_recording`, `98_midterm`, and `99_final` are useful options, not reserved slots.

For example, a course with adaptive learning and labs might use:

```text
<course>/
├── 00_info/               # Syllabus, schedule, manifest, and file index
├── 01_lec/                # Lectures
├── 02_tut/                # Tutorials and matching solutions
├── 03_adaptive_learning/  # Adaptive learning materials
├── 04_project/            # Project briefs, datasets, and templates
├── 05_lab/                # Lab instructions and supporting files
├── 97_recording/          # Recording sources and Transcripts/
└── 99_final/              # Final exam materials
```

This is an illustration, not a template to copy. Another course might use `03_ass`, `04_lab`, and `05_reading`, omit projects entirely, or group readings under the related lecture topic. Keep a distinct category when it represents a recurring activity or a useful body of material; avoid a separate top-level folder for every small variation. Keep questions and solutions together under the same activity.

Create categories only when needed. On later syncs, add a new category using a suitable unused prefix without renumbering established folders merely to close gaps. If ordering cannot be improved without disrupting existing paths, preserve stability until reorganization is requested. Record category purposes and the resulting order in the course index so subsequent runs follow the same logic.

When reorganization is requested, inventory existing files and references, choose the layout from the actual course content, then make traceable moves and update source records and identifiable local references.

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
