# Recording Transcripts

## Discover

- Check module players and all pages of Zoom Cloud Recordings or Panopto lists, including date filters and multiple files per session. Upcoming Meetings is not a recording list. Deduplicate by recording ID or canonical playback URL.
- Use authenticated sessions and actual playback links. For blank Panopto embeds, open the linked player and use the Canvas identity provider when offered. Use only user-supplied or course-published passcodes.

## Save

- Prefer native VTT/SRT/TXT downloads. Otherwise export the complete rendered Captions or Audio Transcript panel through supported tools. Exclude OCR, chat, and search results. Load virtualized sections and deduplicate timestamps; mark incomplete captures `partial`.
- Keep original captions plus readable UTF-8 TXT in the recording directory's `Transcripts/`. Preserve language, timestamps, and speaker labels; do not summarize or silently correct text. In Panopto, timestamps following text belong to the preceding segment.
- Use evidenced names such as `L01_YYYY-MM-DD_HHMMSS_Topic.txt`; otherwise use `Recording_YYYY-MM-DD_HHMMSS_<short-ID>.txt`. Never invent lecture numbers or infer unknown source timezones from the machine.
- Include course, original title, stable playback URL, recording time/timezone, export date, platform, and caption origin in the header. Mark automatic captions as uncorrected.

## Validate

Verify actual saved contents, decoding, segment count, and ordered first/last timestamps. Compare the last caption with visible duration and investigate substantial gaps; trailing silence needs no fabricated captions. Hash updates and preserve previous versions.

Update `Transcripts/INDEX.txt` and the manifest with exact coverage and unresolved reasons. Recheck processing recordings and missing captions later. Do not claim speech recognition when captions are absent; local transcription requires confirmed tools, costs, audio access, and separate source labeling.
