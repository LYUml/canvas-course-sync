# Sync Manifest

Reuse the existing format, or create UTF-8 `sync-manifest.json` in `00_info/` (course root if absent). Separate courses and terms. Validate a temporary JSON file before replacing the manifest.

Record:

- Course code, term, and Canvas course ID.
- Checked sources: platform, stable URL, check time, scope, and completeness. Unfinished pagination is incomplete; never refresh unchecked sources.
- Items: platform/course/file or recording ID, original title, stable source URL, remote update time, check time, status, and specific failure reason.
- Artifacts: relative path within the course root, SHA-256, byte size, and retrieval time. Preserve previous successful versions on failure.
- Recordings: recording time/timezone, caption origin, visible duration, first/last caption times, and completeness.

Use timezone-qualified ISO 8601 times; unknown source times remain null. Keep recording, modification, retrieval, and check times distinct.

Statuses: `downloaded`, `updated`, `unchanged`, `partial`, `processing`, `no_transcript`, `authentication_required`, `permission_denied`, `failed`.

Confirm local files exist before marking unchanged. Remote size/time alone does not prove equality; download and hash when uncertain. Identical content may share a file while retaining separate source mappings. Recheck partial, processing, and missing-caption items on later runs. Report actual coverage and unresolved items, not merely a populated manifest.
