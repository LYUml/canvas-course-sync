# Zoom／Panopto 转录同步

## 发现与登录

1. 检查 Modules 内的 Recording／Recordings 页面及课程导航 Zoom、Panopto Video。核对课程、学期、日期；遍历录播列表所有页，同时检查模块内未出现在列表的录播。用平台录播 ID 或规范播放地址去重，同日两场 tutorial 保留各自时间。
2. 通过已连接工具或已登录浏览器操作。Panopto 的 Canvas 内嵌播放器可能空白：从已有模块播放器或本地来源记录找到实际 Panopto 播放页；若显示登录，选择 Canvas 提供方，使用当前 Canvas 登录。不能猜测录播 ID、读取浏览器凭据或绕过权限。
3. Zoom 检查 Cloud Recordings／云录制、日期筛选、分页及每场录制的多个文件；不要把 Upcoming Meetings 列表当作录播列表。播放页可能需要录播口令；只使用用户提供或课程页面公布的口令。

## 获取与保存

- 优先使用平台提供的 transcript／caption 原生下载，保存 VTT／SRT／TXT。只下载字幕和转录，默认不下载完整视频。没有下载按钮但可查看完整转录时，导出渲染的字幕面板文本。保留原语言、时间戳和现有说话人，不翻译或默默纠正术语。
- Panopto 点击“字幕／Captions”标签，从对应 tabpanel 获取内容；不能混入 OCR 提纲、聊天、讨论或搜索结果。Zoom 打开 Audio Transcript／音频转录面板，确认实际条目完整加载。列表虚拟化时逐段加载、按时间去重；仅能拿到片段时明确标注 partial。
- 使用当前浏览器工具支持的下载或导出方式。若只支持读取面板文本，可通过 CUA 在文本编辑器新建 UTF-8 纯文本、粘贴捕获的完整文本并保存，再用文件工具整理。macOS 保存路径用 setValue 或 paste 保留下划线；保存后从文件系统核对内容，不仅确认对话框关闭。遵守当前工具限制，不通过页面脚本创建下载或调用隐藏接口。
- 转录统一置于课程录播目录的 `Transcripts/`。仅在现有课程目录证实时采用相应编号。文件名沿用 `{Lxx|Txx|Pxx}_YYYY-MM-DD_HHMMSS_Topic.txt`，只有课程证据支持时填写讲次与主题；不明确时用 `Recording_YYYY-MM-DD_HHMMSS_<短ID>.txt`，不能猜讲次。
- 文件头记录课程、原始标题、来源播放页、录制日期和时区、导出日期、平台及 automatic／human captions。自动字幕注明未经人工校正。平台显示时区不明时保留原始时间并标明不明，不能按机器时区推断。
- 保留下载的原始字幕格式（若有），另生成可读 TXT。Panopto 面板常见“文本行后跟时间戳”；将时间戳关联前面的整段文本，不能错配到后文。不要把转录改写成摘要。

## 增量与验证

- 先检查原有 manifest、来源链接及文件。已有完整且未变化的录播跳过；之前 recording in progress／processing／no captions 的条目每次重查。更新字幕时比对 SHA-256，变更版本保留旧版，用户笔记不覆盖。
- 每份核对非空、可解码、段数、首末时间戳和单调顺序；末条字幕可以早于视频结尾的静音，不能为凑时长伪造字幕。记录平台时长与末字幕时间，差距显著时检查是否加载完整。
- 记录 status: downloaded、unchanged、partial、processing、no_transcript、authentication_required、permission_denied 或 failed。未发布字幕、录制中、登录失效和权限问题分别记录。平台无转录时不要声称已完成语音识别；若需本地音频识别，先确认可用的模型、工具、费用和音频获取权限，再执行，单独标注生成来源。
- 更新 `Transcripts/INDEX.txt` 与 manifest，列出本次新增、更新、跳过及未取得原因。平台只检查了一部分时报告确切范围，不声称整门课齐全。
