---
name: canvas-course-sync
description: Incrementally sync Canvas course materials and existing Zoom/Panopto transcripts, organize files into numbered folders, and rename them by content. Use for course downloads, updates, or organization of local course materials.
---

# Canvas Course Sync

## Workflow

1. Confirm the course, term, and local destination from user instructions and existing records. Inspect local files and conventions before writing. Resolve ambiguity that could target the wrong course.
2. Use a suitable connected tool or authenticated browser. Start with Modules, then relevant Announcements, Assignments, Files, and linked pages. Check pagination; previews, links, and login pages are not downloaded originals.
3. Match sources against local records. Download missing or potentially changed files through supported official links, compare SHA-256, and retain one copy of identical content with all source mappings. Preserve previous versions and personal work; never overwrite uncertain collisions.
4. Read [organization rules](references/organization.md). Classify and rename by actual content, choosing useful numbered categories for this course rather than copying a fixed template. Reorganize existing materials when requested; keep paths stable during routine updates.
5. Unless limited to attachments, check recordings using [transcript guidance](references/transcripts.md). Sync existing captions, not full videos or unrequested speech recognition.
6. Verify saved files are nonempty and readable, update the index and [manifest](references/manifest.md), and report additions, updates, unchanged items, failures, and unchecked scope. Resume interrupted work from actual files and records.

## Boundaries

- Use available tool capabilities and follow their restrictions. Ask the user to sign in when needed; never extract credentials or bypass access controls.
- Read course content and write within the selected local scope. Do not submit assignments, modify courses, or delete remote materials. Preserve local files missing from remote listings.
- Keep credentials, signed download URLs, and student personal information out of public records. Use stable source pages and IDs.
- Retry transient failures only a bounded number of times; preserve progress on login, permission, or persistent failures. Partial retrieval is not completion.
- Schedule recurring runs only when requested. For the original author's PolyU directories, consult [local conventions](references/local-conventions.md) only when relevant.
