# SullyOS-Dev-Preview

## 神经链接联合回归 · 最新开发分支发布校验（2026-10-31）

- 这次仅触发独立测试站现有 Actions，构建 `remove-checkphone-vrworld-lifesim` 最新源码，不修改正式站。
- 酒馆 V1/V2/V3 + PNG/JSON、BabyLink 共用入口已按本轮审计修复；新版解析与库挂载的联合回归已通过。
- 最终发布结果必须由公共站 `preview-source.json` 与 workflow 部署校验共同确认。

## 酒馆角色卡导入 · 深度复查修复（2026-10-31）

- 不修改正式分支，测试站从 SullyOS 的 `remove-checkphone-vrworld-lifesim` 当前 HEAD 构建。
- 已修正角色 description 在真实 ContextBuilder 中被当作备注、混合 scenario 整段丢失、扩展世界书控制项丢失、zTXt/iTXt PNG 解析及酒馆/ BabyLink 图片判别优先级。
- 角色头像使用 Blob 资产，失败时清理新建的孤立头像令牌。
- 实际部署成功与源码版本只以公开 `preview-source.json` 校验为准。

## 神经链接 · 酒馆角色卡兼容测试站同步（2026-10-31）

- 本次仅触发独立开发预览仓库已有的发布工作流，源码保持 `artibala866-cmd/SullyOS` 的 `remove-checkphone-vrworld-lifesim` 分支。
- 新增酒馆 V1/V2/V3 JSON、V2/V3 PNG、世界书启停与挂载、预览确认、数据库原子保存。
- 第一轮导入回归、TypeScript 检查与完整构建已成功；最新补充的 ContextBuilder 请求断言由源码 CI 继续验证。
- 实际上线源码提交必须以部署后的 `preview-source.json` 为准；不得以这份 README 的更新代替上线验证。

## 学习室阶段 2 · 真实反馈与执行计划（2026-10-31）

- 此次独立测试站发布触发来自 SullyOS **既有开发分支** `remove-checkphone-vrworld-lifesim`，已审核源提交 `de26bc88741ce81e31453f0f4f6c5b09c68a61c4`。
- 主页隐藏重复的「自习室」图标；学习室内仍能进入原 StudyApp，课程与 PDF/测验数据不迁移、不删除。
- 学习室的真实督促事件支持按 Char 记录「稍后、今天休息、今天不再提醒」；只用已设置的可用时间生成画稿/作业候选计划，用户逐项确认后才会保存。后续提示来自确认过的原计划，不自动标记完成。
- GitHub Actions [学习室检查](https://github.com/artibala866-cmd/SullyOS/actions/runs/41130272605)：28 个测试文件、162 项测试通过，目标 TypeScript 诊断通过，生产构建通过。
- 本 README 提交仅触发 **隔离开发测试站** 的原有部署工作流；不是应用源码提交、不触及 SullyOS `master` / 正式站 / 原私聊 / AMSG Worker。
- 本站真正上线的源码版本，最终仍以线上 `preview-source.json` 及 GitHub Pages 部署成功记录为准。

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


## 阶段 4 持续修补：云端 NPC 微信实际可达性（2026-10-30）

- 源码修补仍只在 `remove-checkphone-vrworld-lifesim`；预览站独立部署，不触动正式 Cloudflare Worker、`master`、其他开发者的工作或用户旧数据。
- 检查并修复云端 NPC 回复的开关：仅需角色明确开启主动消息 2.0 + 手机“私聊同轮生成”；不依赖独立收费的手机后台 AI 开关或手机前台自主活动总开关。
- 云端工具多轮生成保留有效的 NPC sidecar 到终结轮，提交结果时只发一次；缺少持久回程通道则不预留这次 NPC 活动，避免无效消耗。
- 本地候选严格筛选虚构 NPC，排除绑定其他真实 Char 的联系人，又不会让这些人的旧消息挡住合格 NPC。云端消息按稳定来源标识去重，允许真实发生的重复短句；写入时再检查原微信线程仍存在、内容和数量没变化，防止旧数据复活。
- 角色手机设置已新增离线可用性说明，**仅显示本地候选**、不宣称 Worker 已启动或真实送达。
- Worker 包装层版本 `2026-10-30.2`，必须由用户在自己的 Worker 更新才能执行。当前仅是开发测试，不对用户 Cloudflare 实例做更新。
- 阶段 4 核心测试工作流 `41025354695`：**8 个测试文件、157 项通过；变更模块 TypeScript 检查通过；Worker 真实打包成功**。无手机端真实送达确认。
- 此段说明触发隔离预览构建；`preview-source.json` 及 GitHub Actions 中的源码检出记录是发布版本的依据。

## Stage 4 联系人删除与多会话安全补丁（2026-10-30）

这一轮只继续维护原有 AMSG2/角色手机阶段 4 的有限离线 NPC 微信续聊，不切换分支、不部署用户 Cloudflare Worker，也不引入新的收费后台任务。

- 云端候选和返回结果增加 **联系人创建身份及联系人清除版本**；用户清空或重建通讯录后，旧云端消息不能错认新的同 ID NPC。旧协议数据缺少身份字段时保守拒绝写回。
- 同一联系人在旧备份里有多条微信线程时，回程根据精确 `threadId` 找到原会话；已改成群聊/服务号的会话拒绝写入 NPC 私聊结果。继续保护用户自己先回复或删除的内容。
- 历史记录里空白、时间戳非法或联系人身份对不上的待回复消息不再被当成 NPC 自主活动理由，避免挡住其他有根据的消息。
- 阶段 4 真实 Worker fire/outbox 集成测试、手机同轮许可、联系人删除/重建、线程身份、生活事件删除回归均已纳入专用 CI。
- Worker bundle 版本 **`2026-10-30.3`**，旧 Worker 不支持这些协议字段。独立站发布不升级用户的正式 Worker；实际离线触发与推送仍需用户部署兼容版及端到端测试。
- 交付源码仍仅在 `artibala866-cmd/SullyOS` 的 `remove-checkphone-vrworld-lifesim`，真实发布的精确源 SHA 以 GitHub Pages 工作流及 `preview-source.json` 为准。


## 阶段 4 验证：真实 Worker 触发与联系人同步修复（2026-10-30）

本次隔离预览仍从源码开发分支 `remove-checkphone-vrworld-lifesim` 只读构建，不更改正式部署、生产 Cloudflare Worker、`master` 或其他开发者内容。

- 追加了**真实 Worker onBeforeFire → onLLMOutput** 的自发消息/NPC 同轮回程测试。确认角色选择对 User 静默、仍可生成一次合格 NPC 回复，且工具多轮不丢/不重复；没有 outbox 不预留 NPC 回复。
- 纠正对结果队列的断言：`fire-skipped` 和 `cloud-phone-reply-v1` 是不同结果，不能把正常跳过回执误看成重复 NPC 互动。
- 加强联系人主权：NPC 回复绑定稳定联系人生成身份与联系人清除版本；直接重命名、批量保存/删除联系人后由 `saveNpcProfiles` 统一发出原有变更通知，刷新上传到 Worker 的可选 NPC 候选，避免旧联系人快照长期不更新；失败存储不发送假通知。
- 核心 GitHub Actions `41027539994`：**3 项真实 Worker 钩子测试通过、10 组 170 项相关模块回归通过、相关 TypeScript 检查通过、Worker 打包成功**。阶段 4 不增加独立 AI 轮询或改变默认开关。
- 尚未实测用户线上 Worker、Cloudflare Cron 或 Android 真实收信；**预览网页的发布不会自动升级用户正式 Worker**。仅保留真实、已授权的有限 NPC 待回复云端回程，非完整离线独立生活。
- 以本次 workflow 检出源码和发布时的 `preview-source.json` 版本标记为准（预览可能同时包含其他开发者在指定分支提交的无关修改）。

## 学习室悬浮 Char 聊天窗 · 测试站同步核查（2026-10-30）

- 本次仅触发本独立测试站现有 GitHub Pages 构建，发布源仍为 `artibala866-cmd/SullyOS` 的 `remove-checkphone-vrworld-lifesim` 最新 HEAD；不修改正式部署或开发分支。
- 核查目标：学习室的可拖动小手机式 Char 悬浮聊天窗、角色快速选择及进入所选 Char 原生私聊的按钮。
- 是否已经真正上线，必须以本次构建结束后的 `preview-source.json` 中的 `sourceCommit` 和发布工作流结果为准；此说明不构成部署成功声明。

## 学习室 Char 头像悬浮球与原生手机私聊发布（2026-10-30）

- 本次只触发独立测试站的现有 GitHub Pages 流程，从 SullyOS 唯一正式开发分支 `remove-checkphone-vrworld-lifesim` 检出最新 SHA 进行构建，不向 SullyOS 的 `master` 写入。
- 学习室旧文字聊天入口改为常驻可点的 Char 圆形悬浮球；点开是真正的手机外框，手机内嵌原生私聊并复用原私聊消息记录，不添加学习室信息到原私聊提示词。已有专注计时期间只显示原学习室限额交流。
- 发布状态只以本次 CI 的实际源码 SHA、GitHub Pages 发布成功和线上 `preview-source.json` 为准；此文档更新只是触发构建。

## 学习室悬浮手机纵向比例修复 · 2026-10-30

- 独立测试站构建源：SullyOS 现有 `remove-checkphone-vrworld-lifesim` 分支；触发时源 HEAD 为 `f4c6840c91ae9e2b9c6a99bc5137b02f837e2eae`。
- 原悬浮框宽 326px、独立高度 478px 容易压扁；已改为 9:19.5 竖屏手机比例、最大宽 232px、按 320/360/390 CSS px 和短屏自适应收窄。手机保留完整外框和右侧悬浮位置；窄屏顶部切换改图标避免撑宽。
- 此处只触发既有的独立预览 Pages 工作流，不更新正式部署或 Cloudflare Worker。是否更新以 Pages 构建成功及 `preview-source.json` 为准。

## 学习室迷你手机原生聊天内容等比缩放修复（2026-10-30）

- 从 SullyOS 唯一开发分支 `remove-checkphone-vrworld-lifesim` 当前 HEAD (`f97646b5d6af4d020d4bff86efac6745a50a9167`) 重新构建独立测试站；不触动 SullyOS master 或正式部署。
- 本次重点修复真机截图的严重裁切：先将原生 Chat 在 390 CSS px 的完整逻辑宽度排版，再由 ResizeObserver 测得手机屏幕尺寸，把整个原生聊天画布和输入栏按同一比例缩放；手机壳宽度最多 218px，9:19.5 纵向比例且位于页面右侧。
- `preview-source.json` 和 Pages 工作流成功状态为发布依据；真实 Android 键盘仍需用户现场验收。

## 学习室悬浮手机最终可读尺寸修复（2026-10-30 · 23:16 截图反馈）

- 本次发布源为 SullyOS `remove-checkphone-vrworld-lifesim` 分支，提交 `1ea7e39195081b484228b0a213b0408959f17cb8`，仅更新隔离测试站。
- 纠正上次只缩外框造成的实际字体过小：当前最大外宽 334 CSS px、与参考图接近的 9:16 纵向悬浮手机、内部私聊按 300px 排版并整体等比缩放；手机私聊文字和输入框提高至 17px 逻辑字号，短屏提高至 21px。
- 已在 Chromium CSS 样式检验中测试 320/349/360/390/430px 和宽屏，移动端位置与外框在屏幕内；页面真实数据和 Android 输入交互仍需独立验收。
- 发布是否完成以本次 Pages Workflow 及其 source revision marker 为准。不更改 SullyOS master、私聊提示词或数据库。

## 学习室悬浮手机最终尺寸/实际字号复核版本（2026-10-30）

- 采用用户最新截图复核后再次精修：来源 `f396b11f3e3fdb03d003e0188cd2704a1c16b77a`，保留 Char 悬浮球及独立手机私聊。
- 最终手机壳最大外宽 306 CSS px，纵向 9:16，右侧悬浮、底部预留导航；内部真实私聊按 300px 排版，正文/输入提升至 17px 逻辑字号，短屏 21px。
- 通过 Chromium 独立布局样式检查，320×568、349×768、360×740、390×844、430×932、1366×768 上均未越界，实际估算字符大小约 15–16px；这不是已登录 App 的 Android 真机端到端截图。
- 仅发布独立测试站，不修改 SullyOS master、普通私聊提示词、消息数据库及正式部署。

## 3D 家园第二阶段：拍照构图、相纸文字、双人授权（2026-10-30）

- 发布来源保持 `artibala866-cmd/SullyOS` 的原有 `remove-checkphone-vrworld-lifesim`，只更新独立测试站，不修改正式站、`master`、家具目录或原存档。
- 增量加入全身 9:16、奶油拍立得、爱心大头贴、四格贴纸，主文案/底部文字/字体可编辑，沿用原高清 PNG 导出与相机交互；原四款比例、默认横幅、已选动作均保留。
- 双人拍照的亲密、亲亲类动作均须明确关系授权，列表过滤与底层执行双重保护。
- 此文档提交触发独立站现有 Pages 工作流。**实际部署成功与否、准确的来源提交，以本次 GitHub Actions 和线上 `preview-source.json` 为准**，不以源码提交或普通构建通过代替真实场景验收。

## 2026-10-31 · 万圣节双人动作实机复查后更新独立测试站

- 用户要求在 https://artibala866-cmd.github.io/SullyOS-Dev-Preview/ 测试四组万圣节双人动作。
- 本次只触发独立测试站 `branch-preview.yml`，由工作流只读检出 `artibala866-cmd/SullyOS` 的现有 `remove-checkphone-vrworld-lifesim` 最新 HEAD；触发前源分支为 `3ae086871e367ac6d97c0bc7ccbe9599f696f563`。不创建新分支、不修改 SullyOS 正式站或 Cloudflare Worker。
- 保留预览仓库已有「宝宝狗」专属名称和图标，发布工作流仍执行原有质量检查。
- 唯一有效的上线验收标准是 GitHub Pages 发布步骤成功，且线上 `preview-source.json` 返回本次构建真正检出的完整源码 SHA；若构建期间有其他协作提交，以上线 marker 为准。
