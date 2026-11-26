# Canvas Course Sync

让 AI 从 Canvas 同步课程资料，按编号目录分类、根据内容改名，并维护可追溯的文件索引。后续再次同步时，只补缺和更新，减少重复下载与手动整理。

这是供 Codex 使用的 skill，需要由具备浏览器／连接器及本地文件能力的 AI 执行；仓库本身不是独立下载程序或后台服务。

## 功能

- 检查 Modules、Announcements、Assignments、Files 及相关课程页面中的附件。
- 由 AI 结合页面上下文和文件内容，识别讲义、习题、答案、作业、项目和考试资料，分类并重命名。
- 使用 SHA-256 比较内容、去重及识别更新，保留旧版本与用户笔记。
- 同步 Zoom／Panopto 已有字幕和转录，保留原始字幕并生成可读 TXT，标明自动字幕及完整性。
- 维护同步清单和文件索引，记录来源、原名、新路径及失败原因，支持中断后继续。

没有发布字幕的录播不会被标记为已转录。本地语音识别需要另行确认工具、音频权限及可能的费用。只有用户明确要求时才配置定期任务。

## 安装

需要 Git 和 Codex。将仓库克隆到 Codex 的 skills 目录：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/LYUml/canvas-course-sync.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/canvas-course-sync"
```

如果目标目录已存在，先检查其中是否有本地改动，不要覆盖。已通过 Git 安装的版本可在该目录执行 `git pull --ff-only` 更新。

安装后在 Codex 新建会话，使用 `$canvas-course-sync` 调用。执行同步前，准备好可访问课程的 Canvas 登录会话，以及允许写入的本地课程目录。浏览器访问和下载能力取决于当前 Codex 环境；没有适用工具时，AI 会说明缺少的条件。

## 使用

建议第一次提供 Canvas 地址、课程代码、学期和保存位置：

```text
使用 $canvas-course-sync，同步 https://canvas.example.edu 上
EXAMPLE101 的 2026-27 Sem1 资料，保存到 ~/Courses/2026-27-Sem1/example101。
请按编号目录整理，阅读内容后改成容易识别的文件名，并生成文件索引。
```

后续增量更新：

```text
使用 $canvas-course-sync，更新 ~/Courses/2026-27-Sem1/example101，
检查新增附件和录播转录，列出未能取得的内容。
```

整理已有的杂乱资料：

```text
使用 $canvas-course-sync，整理 ~/Courses/2026-27-Sem1/example101 中
已有的教师资料，按 01、02、03、04 分类，根据内容改名并更新索引。
保留我的笔记和项目草稿，汇报移动及改名结果。
```

可以限定“仅下载附件”“只更新某周”“只同步录播字幕”。AI 会沿用已有目录；新课程按实际内容创建以下分类：

```text
example101/
├── 00_info/           # 大纲、FILE_INDEX.md、sync-manifest.json
├── 01_lec/            # L01_Introduction.pdf
├── 02_tut/            # T01_Questions.pdf、T01_Solutions.pdf
├── 03_ass/            # A01_Brief.pdf、A01_Template.xlsx
├── 04_project/        # 项目说明、数据与模板
├── 05_recording/      # Transcripts/：原始字幕与可读转录
├── 06_reading/        # 阅读材料
├── 98_midterm/        # 期中试卷与答案
└── 99_final/          # 期末试卷与答案
```

AI 根据实际内容判断用途，不仅按原文件名分类。例如 `Test.pdf` 经首页确认是期中卷后，可归入 `98_midterm/` 并改为 `Midterm_2026-27_Sem1_Questions.pdf`。无法确定的讲次、主题和学期不会被编造；项目包内部结构会保留。

## 同步结果

每次执行会报告检查范围、新增、更新、未变化和未取得的资料，提供实际保存路径。部分字幕、登录失效、权限拒绝和平台处理中会分别记录；未检查的入口不会被算作完成。远端资料消失时保留本地副本，不自动删除。

课程资料与同步清单保存在用户指定的课程目录，不应提交到这个 skill 仓库。登录凭据和带签名的临时下载链接不写入公开记录。

## 仓库结构

- [SKILL.md](SKILL.md)：AI 执行入口。
- [目录与命名规则](references/organization.md)：编号分类、内容改名与索引维护。
- [同步清单约定](references/manifest.md)：增量状态、来源映射和恢复规则。
- [录播转录流程](references/transcripts.md)：Zoom／Panopto 字幕获取与验证。
- [个人课程约定](references/local-conventions.md)：原作者已有目录示例，仅在本地证据匹配时使用。
- [agents/openai.yaml](agents/openai.yaml)：skill 展示信息。
