# 增量同步清单

沿用课程已有格式；没有清单时，在 `00_info/`（不存在则使用课程根目录）创建 `sync-manifest.json`。清单按课程和学期隔离，UTF-8 编码，不存凭据。先写临时文件并校验 JSON，再替换正式清单，避免中断损坏历史记录。

## 建议结构

```json
{
  "schema_version": 1,
  "course": {"code": "EXAMPLE101", "term": "2026-27 Sem1", "canvas_course_id": "123"},
  "checked_sources": [],
  "items": []
}
```

`checked_sources` 每项记录 `platform`、稳定 `source_url`、`checked_at`、`scope` 和 `complete`。只有实际检查过的入口才能更新时间；分页未结束时 `complete` 为 false。时间使用含时区的 ISO 8601；未知远端时间保留 null，不用当前时间代替。

`items` 每项至少包含：

- `source_key`：平台、课程 ID、文件或录播 ID 的组合。无 ID 时使用稳定来源页面和明确的条目标识，不以本地文件名作唯一身份。
- `source_url`、`original_title`、`remote_updated_at`、`checked_at`。
- `artifacts`：每个文件的 `relative_path`、`sha256`、`bytes`、`fetched_at`；可同时记录原始 VTT 和可读 TXT。路径必须落在课程根目录内。
- `status`、`reason`：结果与具体原因。失败时保留上次成功的文件信息，不把旧文件标成此次成功下载。

录播另记 `recorded_at`、原始时区、`caption_origin`（automatic、human 或 unknown）、可见时长、首末字幕时间和完整性。录制时间、远端修改时间、下载时间、检查时间各自独立。

## 结果与重查

- `downloaded` / `updated`：文件已保存、验证，并与旧版本完成比较；更新时保留旧版本记录。
- `unchanged`：有充分证据确认版本一致，且本地文件存在；清单中的旧路径缺失时重新获取。
- `partial`：附件或转录只取得一部分，注明缺少范围，后续重查。
- `processing` / `no_transcript`：录播处理或当前无字幕，下次同步重查。
- `authentication_required` / `permission_denied` / `failed`：分别记录登录、权限和其他失败，不当作空课程或空列表。

远端更新时间和大小可用于筛选，但不能证明内容相同。元数据不可靠或出现更新迹象时下载后比较 SHA-256。不同来源的相同内容可共用一个本地文件，但保留各自来源映射；不要仅按哈希合并不同课程的记录。

最终报告指出检查范围、实际写入路径、各类结果和仍需用户处理的事项。清单完整不等于同步成功，以实际来源覆盖和文件验证为准。
