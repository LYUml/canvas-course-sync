# Canvas Course Sync

A Codex skill to sync Canvas materials and existing Zoom/Panopto transcripts. AI organizes files into logically numbered folders, renames them by content, and tracks updates without overwriting personal notes.

## Install

```bash
git clone https://github.com/LYUml/canvas-course-sync.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/canvas-course-sync"
```

## Use

Sign in to Canvas, then ask Codex:

```text
Use $canvas-course-sync to sync COURSE_CODE, TERM, from CANVAS_URL
into LOCAL_FOLDER. Organize and rename files based on their contents.
```

Folder categories and numbering adapt to each course. Run again for incremental updates. Requires browser/connector access and local file tools.
