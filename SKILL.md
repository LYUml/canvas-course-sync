---
name: canvas-course-sync
description: Incrementally download and organize Canvas course materials, rename files by content, deduplicate versions, and sync existing Zoom or Panopto captions and transcripts. Use when asked to sync a Canvas course, update local course materials, or organize downloaded lectures, tutorials, assignments, exams, project attachments, and recording transcripts.
---

# Canvas Course Sync

Bring the selected local course directory up to date with accessible materials in the requested scope. For updates, compare existing files before downloading missing or changed content. Schedule recurring runs only when explicitly requested.

## Identify the course and scope

- Prefer a suitable connected Canvas tool. Otherwise use an authenticated browser session and confirm the course code, term, and course homepage from the course list.
- Inspect the target directory, existing README, indexes, and files. Preserve established numbering, naming, and version archives. Resolve courses with the same name using the requested term and local evidence.
- Start with Modules, then inspect Announcements, Assignments, and visible Files as relevant. Open pages that may contain attachments. A module item may be a file, page, quiz, or submission link; classify its actual content. Screenshots, links, and login pages are not downloaded originals.

## AI organization and numbered directories

Organization and content-based renaming are part of synchronization. Read [Organization and naming](references/organization.md). Identify each item's purpose from the course page and file contents. For a new course, create numbered categories such as `00_info`, `01_lec`, `02_tut`, `03_ass`, and `04_project` as needed. Preserve existing conventions. When asked to reorganize existing files, inventory files and references before making traceable moves. Keep uncertain names or flag them for review rather than inventing lecture numbers or topics.

## Download, compare, and archive

1. Match local files using source IDs, module context, titles, original names, and existing records. If a version is uncertain or appears changed, download to a temporary location and compare SHA-256. Identical content needs only one local copy, even when names differ.
2. Use the native download link on the Canvas file page and record the actual saved path. When download events are supported, start waiting before clicking. If no event arrives, inspect the download directory and page to distinguish a completed download from a preview, expired login, or blocked download. Check alternative official attachment links when available; record unresolved failures precisely.
3. Choose a category and descriptive name while preserving the extension. Use lecture numbers for lectures, matching tutorial numbers for questions and solutions, term and role for exams, and purpose for project materials. Inspect the first page or source description instead of relying on a generic filename or module position.
4. Check for destination collisions before moving. Archive the old version according to existing conventions when the source clearly establishes an update. Otherwise preserve both with distinguishable names. Preserve personal notes, self-authored exercises, project drafts, and user-edited copies.
5. Verify that every new file exists at the destination, is nonempty, and can be read. For PDFs, use `pdfinfo` when available and inspect the first page when needed. Update original-name and destination mappings and the file index. Report saved paths and unresolved items.

## Recording transcripts

Unless the user limits the task to attachments, also check Zoom and Panopto. Read [Recording transcripts](references/transcripts.md) and inspect both recording lists and embedded module players. Run incrementally on each invocation; this skill is not a background service. Use available automation tools only when a recurring schedule is explicitly requested.

## Records and completion

Read [Manifest conventions](references/manifest.md). Reuse an existing manifest format or create one when absent. Record each completed operation and resume interrupted work using both the manifest and actual files. Claim completion only after checking the agreed entry points, pagination, and download scope. Distinguish new, updated, unchanged, unavailable, and unchecked items. Permission failures and partial transcripts are not completed items.

## Environment and access boundaries

- Confirm the course, term, and local root using user instructions, the current course directory, or existing source records. Ask when ambiguity could cause writes to the wrong location; continue independent read-only checks where useful.
- Use tools actually available in the environment. If no authenticated session exists, ask the user to sign in; do not request passwords or copy session tokens. Use APIs only through provided tools or an explicitly authorized access method. Follow the browser tool's own restrictions.
- Read course content and write only within the selected local scope. Do not submit assignments, modify courses, publish content, or delete remote files. Preserve local copies when remote materials disappear; absence from a listing is not proof of deletion.
- Preserve progress on expired login, denied access, or persistent failures. Retry transient failures only a bounded number of times; do not repeatedly click through the same failure. Wait for the user when login or additional authorization is necessary.
- Do not put credentials, cookies, access tokens, signed temporary download URLs, or student personal information in public records. Store stable course pages and platform IDs. Omit a URL if credentials cannot safely be removed and explain the omission.

## Optional local conventions

For the original author's existing PolyU directories, read [Local conventions](references/local-conventions.md). These are historical settings to verify, not default installation paths or permanent course mappings.
