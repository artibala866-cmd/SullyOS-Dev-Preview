# SullyOS-Dev-Preview

此仓库只负责发布独立开发测试站：https://artibala866-cmd.github.io/SullyOS-Dev-Preview/

- 应用源码：`artibala866-cmd/SullyOS` 的现有 `remove-checkphone-vrworld-lifesim` 分支。
- 测试站发布：使用 `.github/workflows/branch-preview.yml`，不修改 SullyOS 正式 Pages。
- 实际已上线源码提交：以网站的 [preview-source.json](https://artibala866-cmd.github.io/SullyOS-Dev-Preview/preview-source.json) 为准；不要以源码提交成功代替部署成功。

## 阶段 3 测试站同步

已在 SullyOS 的既有 `remove-checkphone-vrworld-lifesim` 分支完成日程跨页恢复、确认事件驱动的 NPC 手机机会检查、已有 NPC 微信优先续聊。阶段 3 自动化回归 88 项通过；真实离线后台执行仍属于阶段 4 验收。

**是否已真正上线，以测试站的 [preview-source.json](https://artibala866-cmd.github.io/SullyOS-Dev-Preview/preview-source.json) 为准。** 此文档变更只触发当前独立预览构建，不修改应用正式部署。

## 阶段 2/3 安全复查与修复（2026-10-30）

复查并修复：切换角色期间迟到的私人聊天保存、关闭自动回复后旧回调复活、过时 NPC 微信被新事件误触发、无有效手机动作占用冷却、多个角色手机机会同时到达时的排队丢失或堵塞。现有 AMSG / 日程 / 手机 API 预算与用户开关不变。

- 阶段 2 回归：143 项通过，相关 TypeScript 检查通过。
- 阶段 3 回归：93 项通过，相关 TypeScript 检查通过。
- 测试入口只用 https://artibala866-cmd.github.io/SullyOS-Dev-Preview/ ，实际源提交号以线上 `preview-source.json` 为准。
- 真实 Android 杀进程执行、云端/多设备并发预算仍待专项实测，不把自动化测试等同实机验收。

## 主动消息 2.0：无需手动建任务的全局入口验收（2026-10-30）

已将现有 `ensureAutonomyWakes` 云端日循环机会对账接入全局 OS：角色明确开启 2.0 后，应用初始化、开关状态变更、恢复前台及日程更新都会触发对账，即使不再打开该角色的聊天页也无需先创建人工任务。复用既有 Worker 定时任务与云端幂等校验，不新增收费的定时 LLM 引擎。

注意：成功登记任务并不代表每次都要开口；Worker、推送订阅、API 凭据和用户限额必须有效，模型可自主选择沉默。网页与原有独立云端 Worker 并非同一个部署；NPC 微信/朋友圈的离线全自主活动尚未实现，仍需应用前台进行相应操作，不得宣称已全部完成。请以站点 `preview-source.json` 核对实际源提交。
