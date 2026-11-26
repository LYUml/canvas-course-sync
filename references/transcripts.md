# Zoom and Panopto Transcript Sync

## Discovery and authentication

1. Inspect Recording/Recordings pages in Modules and the Zoom or Panopto Video course navigation. Confirm course, term, and dates. Traverse all recording-list pages and embedded module recordings missing from those lists. Deduplicate by platform recording ID or canonical playback URL. Keep separate times for tutorials recorded on the same date.
2. Use connected tools or an authenticated browser. If an embedded Panopto player is blank, follow an actual player link or existing source record to its playback page. When prompted, select the Canvas identity provider and use the current Canvas login. Do not guess recording IDs, extract browser credentials, or bypass permissions.
3. In Zoom, inspect Cloud Recordings, date filters, pagination, and multiple files per session. Upcoming Meetings is not a recording list. Use only passcodes supplied by the user or published in the course.

## Retrieval and storage

- Prefer native transcript/caption downloads in VTT, SRT, or TXT. Download captions and transcripts by default, not full videos. If a complete transcript is visible without a download button, export the rendered transcript panel. Preserve language, timestamps, and existing speaker labels without translation or silent terminology corrections.
- In Panopto, select Captions and read its associated panel, excluding OCR outlines, chats, discussions, and search results. In Zoom, open Audio Transcript and confirm all entries have loaded. For virtualized lists, load successive sections and deduplicate by timestamp. Label incomplete captures as `partial`.
- Use download or export methods supported by the current browser tools. If only panel text is available, a supported alternative is to paste the captured text into a UTF-8 file using a text editor and then organize it with filesystem tools. Preserve underscores in save paths using supported value-setting or paste actions. Verify saved contents on disk, not just closure of the save dialog. Follow tool restrictions; do not create page-script downloads or call hidden endpoints.
- Store transcripts in the course recording directory's `Transcripts/`. Adopt a numbered recording directory only when confirmed by local evidence. Follow `{Lxx|Txx|Pxx}_YYYY-MM-DD_HHMMSS_Topic.txt` where course evidence supports the number and topic. Otherwise use `Recording_YYYY-MM-DD_HHMMSS_<short-ID>.txt`; do not invent lecture numbers.
- Record course, original title, stable playback page, recording date/timezone, export date, platform, and automatic/human caption origin in the text header. Mark automatic captions as uncorrected. If the platform timezone is unknown, preserve the displayed time and label the timezone unknown rather than inferring it from the machine.
- Keep downloaded original captions and produce a separate readable TXT. Panopto panels may place timestamps after the corresponding text; associate each timestamp with the preceding full segment rather than the following text. Do not replace transcripts with summaries.

## Incremental checks and validation

- Inspect the manifest, source links, and local files first. Skip complete unchanged recordings. Recheck recordings previously marked in progress, processing, or without captions. Compare updated captions by SHA-256, retain old versions, and preserve user notes.
- Verify nonempty, decodable files, segment counts, first/last timestamps, and chronological order. Captions may end before trailing silence; do not fabricate text to match video duration. Record visible duration and last caption time, investigating substantial gaps for incomplete loading.
- Use `downloaded`, `updated`, `unchanged`, `partial`, `processing`, `no_transcript`, `authentication_required`, `permission_denied`, or `failed` as appropriate. Distinguish unpublished captions, ongoing recording, expired login, and permission issues. Do not claim speech recognition when no transcript exists. If local transcription is requested, first confirm available models/tools, costs, and permission to obtain audio; label the generated source separately.
- Update `Transcripts/INDEX.txt` and the manifest with additions, changes, skips, and unresolved reasons. If only part of a platform was checked, report exact coverage instead of claiming the entire course is complete.
