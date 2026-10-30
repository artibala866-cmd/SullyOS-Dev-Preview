# SullyOS-Dev-Preview

此仓库只负责发布独立开发测试站：https://artibala866-cmd.github.io/SullyOS-Dev-Preview/

- 应用源码：`artibala866-cmd/SullyOS` 的现有 `remove-checkphone-vrworld-lifesim` 分支。
- 测试站发布：使用 `.github/workflows/branch-preview.yml`，不修改 SullyOS 正式 Pages。
- 实际已上线源码提交：以网站的 [preview-source.json](https://artibala866-cmd.github.io/SullyOS-Dev-Preview/preview-source.json) 为准；不要以源码提交成功代替部署成功。

## 阶段 3 测试站同步

已在 SullyOS 的既有 `remove-checkphone-vrworld-lifesim` 分支完成日程跨页恢复、确认事件驱动的 NPC 手机机会检查、已有 NPC 微信优先续聊。阶段 3 自动化回归 88 项通过；真实离线后台执行仍属于阶段 4 验收。

**是否已真正上线，以测试站的 [preview-source.json](https://artibala866-cmd.github.io/SullyOS-Dev-Preview/preview-source.json) 为准。** 此文档变更只触发当前独立预览构建，不修改应用正式部署。
