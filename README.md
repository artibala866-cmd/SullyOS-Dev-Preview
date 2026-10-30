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


## 主动联系可靠性复查：推送和云端任务对账（2026-10-30）

这轮只完善已有 AMSG2 自主联系链路，不新增引擎、不触碰正式部署：

- 角色明确开启主动消息 2.0 后，由 OS 全局自动与现有 Worker 对账，无需手动创建第一条联系任务；真人感开关是私聊节奏，不代替 Worker 配置。
- 关闭网页或 OS 卸载不再误判成用户关闭 2.0，从而撤销刚在云端建立的自主联系任务；重新打开时以远端任务为准对账。
- 用户直接点击启用 2.0 时申请浏览器通知权限；已开启的老用户也有一键授权/重新登记推送的入口。推送检查区分浏览器订阅与 Worker 服务端登记。
- 任务面板只在远端实际核对成功后显示云端已确认；远端旧任务回收绝不可把从未开启或已关闭 2.0 的角色自动开通。
- 工作流 11 个测试文件、188 项通过，相关 TypeScript 检查通过。完整云端送达仍需用户所配置的 Worker、API 密钥及终端推送实测。
- 本次页面最终源提交以独立站的 `preview-source.json` 为准；此说明仅触发已有独立预览构建。

## 阶段 4 有限离线 NPC 回复（2026-10-30）

本测试站现在从唯一源码开发分支 `remove-checkphone-vrworld-lifesim` 读取阶段 4 开发成果。**不改正式分支、正式部署或用户已有数据**。

- 只有用户明确开启某角色的主动消息 2.0，并另外显式允许角色手机“借用现有聊天生成”（`chatPiggybackEnabled`，默认关闭）、角色手机自主活动及其 API 开关，系统才会选取**真实保存的、尚未回复的虚构 NPC 微信消息**，在原有每日 AMSG2 云端自主联系任务的**同一次**模型请求中可选顺带回复 NPC；不添加另一套付费轮询任务。
- Worker 严格剥离内部 NPC 指令，给用户的主动消息与 NPC 回复分开；NPC 结果只进入现有无通知收件箱，下次客户端上线重新核对权限、聊天历史、联系人、删聊/删角色、版本号后才写回原手机微信；重放不重复写。跨 NPC 会话有限去重避免重复付费。
- 对应 Worker bundle 版本提升到 `2026-10-30.1`；**只更新本独立网页预览，不会更改用户自己的 Cloudflare Worker**。实际离线 NPC 回复需用户自行部署兼容的 Worker，并保持已配置的 API、Cron、Push 有效。
- 回归与真实 Worker bundle 构建已通过：**6 组测试、141 项成功；相关 TypeScript 检查通过；`pnpm build:workers` 成功**。真实 Cloudflare Worker 与 Android 设备端到端送达未验收。
- 这只是阶段 4 的**有限云端 NPC 待回复能力**，不是完整的应用杀进程后 24 小时独立生活或离线朋友圈、新 NPC 自发创建。见源码 `docs/stage4-cloud-phone-continuity.md`。以测试站 `preview-source.json` 所示具体源码提交为准。
