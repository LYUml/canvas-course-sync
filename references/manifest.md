# Incremental Sync Manifest

Reuse the course's existing format. Otherwise create `sync-manifest.json` in `00_info/`, or the course root if that directory does not exist. Keep records separate by course and term, use UTF-8, and store no credentials. Write and validate a temporary JSON file before replacing the manifest to preserve history on interruption.

## Suggested structure

```json
{
  "schema_version": 1,
  "course": {"code": "EXAMPLE101", "term": "2026-27 Sem1", "canvas_course_id": "123"},
  "checked_sources": [],
  "items": []
}
```

Each `checked_sources` entry records `platform`, a stable `source_url`, `checked_at`, `scope`, and `complete`. Update timestamps only for entry points actually checked. Set `complete` to false when pagination is unfinished. Use ISO 8601 with a timezone; leave unknown remote times null rather than substituting the current time.

Each `items` entry includes at least:

- `source_key`: platform, course ID, and file or recording ID. If no ID is available, use a stable source page and an unambiguous item identifier. A local filename alone is not identity.
- `source_url`, `original_title`, `remote_updated_at`, and `checked_at`.
- `artifacts`: `relative_path`, `sha256`, `bytes`, and `fetched_at` for each file, including both original VTT and readable TXT when present. Paths must stay within the course root.
- `status` and `reason`: outcome and specific explanation. Retain previous successful artifact records on failure; do not present an old file as a successful new download.

For recordings, also record `recorded_at`, the source timezone, `caption_origin` (automatic, human, or unknown), visible duration, first/last caption times, and completeness. Keep recording, remote update, download, and check times distinct.

## Outcomes and rechecks

- `downloaded` / `updated`: files saved, validated, and compared against previous versions. Preserve old version records for updates.
- `unchanged`: sufficient evidence of the same version and an existing local file. Fetch again if the recorded local path is missing.
- `partial`: only part of an attachment or transcript was obtained. Record missing coverage and recheck later.
- `processing` / `no_transcript`: recording still processing or captions currently absent; recheck on the next sync.
- `authentication_required` / `permission_denied` / `failed`: distinguish login, access, and other failures. Do not treat these as an empty course or list.

Remote modification times and sizes help select candidates but do not prove identical content. Download and compare SHA-256 when metadata is unreliable or changes are indicated. Identical content from multiple sources may share one local file, but retain each source mapping. Do not merge records across courses based only on a hash.

The final report states checked scope, actual destination paths, outcomes, and remaining user actions. A populated manifest does not prove success; source coverage and file validation do.
