## 2026-10-31 · iOS 6 聊天内置白框测试站同步

- 从 SullyOS 现有分支 `remove-checkphone-vrworld-lifesim` 读取最新源代码；本次白框适配提交 `143d7125d361cf2fbe9bfc18ff897e70e8b7b58e`，不创建开发分支，不触碰正式站。
- 新增「iOS 6 · 复古水晶」内置整套聊天装扮：银灰/冰蓝玻璃气泡、纹理背景、顶栏和输入栏、语音、转账、群聊红包及领取回执。
- 验收必须核对独立站 `preview-source.json` 的 `sourceCommit` 与 GitHub Actions 构建结果；本 README 提交仅触发独立预览站构建，不等于部署成功。

## 2026-10-31 · 手绘风梦核：全景清晰、放大轻景深

- 测试站仅发布 SullyOS 原有开发分支 `remove-checkphone-vrworld-lifesim` 的最新快照，审计提交 `75100ce8ce79618ec8fcbcee1e62e741dd7b1a26`。不新建分支，不动正式站。
- 用户真实书房截图指出全屋糊成马赛克；修复为仅在正交相机可见高度小于 4.25m 时逐渐出现景深，视野大于等于 4.25m 时景深强度为零，放大近景才有轻度虚化。
- 限制景深最大混合比例为 21%，降低模糊采样范围；保留「手绘风梦核」既有细描线、纸感和梦核配色，不改变角色/家具/存档。
- 真实 Chromium WebGL 快照覆盖同场景全景与近景的景深开关；测试验证 `zoomStats.wideStrength=0`、`wideDifference=0`，并发现并修复关闭景深时复用旧画面的更新问题。
- 实际上线与否以该预览站的 `preview-source.json` 中 `sourceCommit`、GitHub Actions 公网校验结果为准。

## 2026-10-31 · 家园「手绘风梦核」景深重影修复 · 测试站同步触发

- 本次只触发独立预览站既有发布工作流；实际源码检出 SullyOS 原开发分支 `remove-checkphone-vrworld-lifesim` 的 `598e8f25646ddaea774bf95628ecc52ce86dfdb4`，绝不更改正式站。
- 旧八方向 24px 景深采样产生窗框、家具及地板的重复影子，现替换为近距离、深度边缘保护的双向连续高斯虚化。
- 真实 WebGL 景深开关与窄线防重影截图已生成；自动验收报告 `depthGhostStats.detachedPixels=0`，人物与光影、回归检查通过。安卓真机仍需确认。
- 实际上线须以 GitHub Pages 工作流中公开 `preview-source.json` 的 sourceCommit 复核。

## 2026-10-31 · 家园漫画滤镜重影专项修复 · Joyce Comic 参考

- 已在 SullyOS 唯一开发分支 `remove-checkphone-vrworld-lifesim` 修复，源码 SHA `f9461d3fd1ba6b3d63b14c55ed5083a88da58fb0`，不建立任何开发分支，不影响正式站。
- 对照上传的 Joyce Comic.ini，确认真正启用的是 `Comic@Comic.fx`；取消此前最高 18 像素方向偏移采样混合和新版光晕叠加，改为仅利用邻域检测边缘、原始像素本位落笔的漫画线条。保留原材质的光影层次和轻微静态颗粒，无模拟景深、无运动重影。
- Chromium 真实 WebGL 验收已通过：原版和漫画版两张清晰轮廓基准截图、四组发色肤色角色截图；防重影断言 `spuriousBright=0`，原版切换恢复逐像素一致。
- 测试站独立工作流会检出开发分支当前 HEAD，是否上线必须以公开 `preview-source.json` 的 `sourceCommit` 核验。

## 2026-10-31 · 家园手绘插画画风二次视觉修正与独立测试站部署

- 测试站从 `artibala866-cmd/SullyOS` 的唯一开发分支 `remove-checkphone-vrworld-lifesim` 检出 SHA `c2b0e44b51436f1db7fa566adc1ef536ce913dcf`；不会修改正式站。
- 本次在原有插画材质上强化脸部暖色颜料、头发丝缎亮面、纹理内部手绘笔触以及暖光/冷影分离，加入更明显的主体焦点式外围虚化与克制颗粒。
- 完成真实 Chromium/WebGL 人物材质多肤色/发色及原版切换截图检查；最终以独立测试站 `preview-source.json` 的 sourceCommit 和发布工作流为准。

## 家园完整画风改造：手绘线稿 / 梦核颗粒 / 焦点景深 · 2026-10-31

- 仅触发独立测试站既有工作流，从 SullyOS 唯一开发分支 `remove-checkphone-vrworld-lifesim` 检出当前源码 `c2b0e44b51436f1db7fa566adc1ef536ce913dcf`；原始仓库主分支和正式网址不修改。
- 新的插画风格加强暖墨轮廓线、三段阴影造型与材质区分，加入轻胶片颗粒、焦点式渐进虚化及暖光冷影电影调色；其他材质、角色骨骼、家园家具和照片记录不动。
- 已生成原版 / 新版的真实 Chromium WebGL 截图，用黑发/浅发/暖发和不同肤色校验；旧样式保留为可切换选项。此记录仅触发部署，最终发布以公开预览站 `preview-source.json` 的 `sourceCommit` 核验为准。

# SullyOS-Dev-Preview

## 家园 Q 版三渲二黑色手绘线稿 · 2026-10-31

- 测试站源码来自 SullyOS 现有开发分支 `remove-checkphone-vrworld-lifesim`，提交 `b7a5665e5eb737f28b1cfe8e9cceb050fba5f85d`；未创建、切换开发分支。
- 仅在可选「插画三渲二」风格内加入角色表面轻薄暖黑手绘轮廓，发片根据 alpha cutout 纹理边缘补线。保持原有软萌亮面与昼夜/窗影，不用全场景滤镜或额外双重几何。
- 原版「风格化」「经典」的 Shader、物体结构、家具、动作、五官、服装、存档及照片滤镜全部保留；原版切换复原的 Chromium WebGL 图像逐像素一致。
- Chromium SwiftShader 真正渲染四组发色/肤色/服装、近景及四时段，验证浅色衣边出现深色笔线；980 帧双人动作、家具/座位交互、运动回归与其他相关构建全部通过。Android 真机性能仍待实测。
- 以公开 `preview-source.json` 返回的源码 SHA 与部署 workflow 通过为发布准据。

## Q版清透日系三渲二修复 · 2026-10-31

- 测试源码 SHA：`341c358e4e25b3b805ec177e8389ded0869581d5`，来自现有分支 `remove-checkphone-vrworld-lifesim`，没有创建或切换开发分支。
- 修正之前发灰、死黑、厚重阴影的「插画三渲二」：亮面和中间调保持通透，暗部采用轻暖/浅冷色，脸部和衣物不再大面积压黑，保留真实窗光和昼夜四时段。
- 发束高光为柔和有色丝缎宽亮面，跟随真实头部旋转；浅色区域只添加轻量插画明面，保护五官和衣服贴图。
- 原版「风格化」与「经典」不变，新样式独立切换；关闭时实际 WebGL 截图逐像素回到原版。照片滤镜、家具、骨骼、角色几何和存档未改动。
- 真实 Chromium WebGL 原版与新版多发色、多肤色、四时段以及近景截图通过；人物区域亮度及黑色像素占比验收通过；980 帧双人动作、家具场景、基本回归均通过。Android 真机性能仍未测。
- 部署只以独立测试站 workflow 公网 `preview-source.json` 验证为准。

## 3D 家园明显三渲二画风 · 2026-10-31

- 源码：`artibala866-cmd/SullyOS` 的现有开发分支 `remove-checkphone-vrworld-lifesim`，已核查版本 `559fbd8545284aa43d01e10d0f16303a845f1eaa`。不创建、不切换开发分支。
- 仅加强可选「插画三渲二」：三段方向光阴影色块，材质区分的冷暖暗部、深色插画轮廓和有色发束光泽。原版「风格化」和「经典」不改，原有清晨/白天/夕阳/夜晚灯光、窗影、拍照滤镜和人物存档保留。
- 真实 Chromium WebGL 四种发色/肤色/衣装的相同视角前后图及四时段对照检查通过；原版切回逐像素一致。完整 980 帧动作视觉验收、家园回归、构建、相关 CI 均通过。
- 本站以独立工作流部署；只有公开 `preview-source.json` 的实际源码 SHA 与本条一致才算上线。

## 家园人物「插画三渲二」独立可选画风 · 2026-10-31

- 只从 SullyOS 开发现有分支 `remove-checkphone-vrworld-lifesim` 检出已验收源码 `7ecb680b56b690193ba450ebad4c0f6ba30916c5`，绝不创建开发分支、修改正式站或覆盖他人提交。
- 新增第三种「插画三渲二」；原版「风格化」与「经典」原样保留，不覆盖已有房间主光、窗影、四时段灯光、照片滤镜和所有家具人物数据。
- 新版让有色发束光泽跟随头骨转动、皮肤与面部有克制的边侧体积、布料折叠更清晰。原「质感增强」后处理默认关闭，只有用户明确开时才附加。
- 原版/新版/恢复真实 WebGL 三联截图 4 种发色肤色、四时段和原生相机近景全部通过，切回原版逐像素一致。980 帧公主抱视觉验收、家园完整回归、动作回归通过。
- 实际发布以独立预览站公网 `preview-source.json` 的 `sourceCommit` 和工作流成功记录验证，不以此说明代替部署结果。

## 糯米机 3D 家园 · 原版光影保留 + 可关闭的质感增强（2026-10-31）

- 本仓库仅触发独立测试站现有工作流；真实源码始终取自 SullyOS 的 `remove-checkphone-vrworld-lifesim`，没有创建任何开发分支或覆盖其他窗口提交。
- 本次引用 ReShade qUINT Lightroom / AMD CAS 的小幅局部对比思想，但没有复制或注入 Windows ReShade。保留原版人物 Shader、材质分类、家具、室内灯光、阴影、原始柔光及照片滤镜。
- 新增的「质感增强」按钮可以即时关闭回到原版；保持原有「柔光调色」独立开关。样式只增加一层轻量局部细节对比，中间暗部得到克制增强；手机省电档自动减弱。
- 源码提交 `5781cb52a849ebee1e5de7a4962a647e3477ab0c`、`2261ef45e9a38606af39dc6ec9e5e51a041affab`；截图验收提交 `2154bbd87f9e253f2c49c7cc13e446a99ddf9206`。980 帧 WebGL + 36 张材质变体 + 8 张画质开关前后截图已验证，角色区域像素差异记录在构建工件中。
- 测试站发布成功只以公开 `preview-source.json` 源 SHA 和本仓库 deploy workflow 验证结果为准。

## 家园人物原版光影恢复 · 2026-10-31

- 仅触发隔离测试站既有发布工作流，重新检出 SullyOS 的 `remove-checkphone-vrworld-lifesim`；不动正式站和源码分支。
- 回退错误的角色材质阴影变浅、皮肤分类及发丝高光改写，恢复到原版的 `illustration.ts` / `FbxBody.ts` 字节内容，源码恢复提交 `26c943a1226d8d741359f17fe5ea70b379466ba7`。
- 实际上线版本只以本仓库发布流水线验证的公网 `preview-source.json` 为准。

## BabyLink 小手机角色卡 · 锁脸和生图配置适配（2026-10-31）

- 仅触发独立测试站的现有 `branch-preview.yml`，从 SullyOS 唯一开发分支 `remove-checkphone-vrworld-lifesim` 检出最新源码；不创建分支，不修改正式站或全局 API 密钥。
- 验证过用户提供的真实 BabyLink PNG，确认角色参考图与聊天头像分别存在。已将锁脸开关、角色身份参考图、五官与外貌提示词、服装约束和支持渠道的种子锁定接入糯米机现有角色生图配置；没有将用户原始人设/照片提交仓库。
- 源码提交 `818bc99e6279b47b2de83d9c93119ee47f3caf95` 的相关 CI：101/101 测试通过、TypeScript 目标检查通过、正式构建通过。
- 本 README 只是发布触发器；真正上线的 SHA 需要由发布工作流核对公开 `preview-source.json`，不可用此处记录代替部署验收。

## 酒馆 PNG 实卡结构复测：19 条世界书（2026-10-31）

- 本轮直接核对用户提供的原始 V2/V3 双元数据 PNG：包含 19 条世界书，其中 13 条启用、6 条停用。
- 修复所有条目带 `use_regex: true` 但关键词实为普通文字时误拒绝整张卡的问题；复杂正则依然不会执行，保留对应条目但安全停用。
- 补充了同结构的脱敏回归用例，确认世界书条数、状态、位置及脚本过滤；不将用户私有角色卡上传到公开仓库。
- 此仓库仅触发原有预览工作流，实际发布 SHA 请查公开 `preview-source.json`。

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

## 2026-10-31 · 无声回信（黑）白框整套美化 · 独立站验收触发

- 源码继续使用 SullyOS 既有 `remove-checkphone-vrworld-lifesim` 分支，本次测试站触发时源 HEAD：`1f52a5225f5f091dcd1c3c676c7c7e37ba07b7a4`；不创建新开发分支，不碰正式站。
- `无声回信 · 黑（by黛）` CSS 已适配私聊、群聊、黑白气泡、引用、心象、转账、红包及回执，新增白框内置整套入口；不覆盖用户已有美化。
- 原生组件回归工作流 `41209223408` 通过 28 项测试和 TypeScript 目标检查，真实 Chromium 使用 CJK 字体截图含 360px 手机画面及群聊原生消息、红包与回执。此条记录仅触发预览站，真正上线以 `preview-source.json` 的 `sourceCommit` 与独立部署运行成功为准。

### 无声回信 · 黑｜最终引用对比度修复后重发（2026-10-31）

- 当前源码：`artibala866-cmd/SullyOS` 现有 `remove-checkphone-vrworld-lifesim` HEAD `b0a92887e86c106aa1bea10f3c2cbb9aef59e22e`。没有新建开发分支，也未发布正式站。
- 修正黑底发出消息中的引用文字对比度。原生群聊/私聊/转账/心象/头像/输入栏回归 `41209554636` 全部通过：28 个 Vitest、目标 TypeScript 与真实 Chromium 中文截图的全部断言。
- 此提交仅触发独立站重新从开发分支检出构建；公网 `preview-source.json` 验证为准。


## 2026-10-31 · 无声回信（黑）原作整套白框重检修复后发布

- 本次始终在 `artibala866-cmd/SullyOS` 既有开发分支 `remove-checkphone-vrworld-lifesim` 修改，不建立新源码分支、不修改正式站。触发部署时源码 HEAD 为 `5179d050f8f9db133abed0ea515f64f45c7b1e45`。
- 读取用户提供的 46 KB 原作 CSS，修复先前将原作缩减为气泡 CSS 的错误，补上原作悬浮玻璃头部、联系人胶囊、发送区、气泡铭牌与连发末尾头像、引用、媒体、心象、转账及群聊卡片；历史已应用错误白框显示时自动兼容，不覆盖其他美化。
- 本次原生组件视觉工作流 `41211846964`：29 项单元测试与目标 TS 检查通过，真实 Chromium 360px 场景截图断言通过，已逐图核验头像空圈消失、顶部在线状态不会竖排，转账卡恢复到原版 250px。
- 此记录只触发独立测试站构建，**不以此作为发布成功证明**。部署需以公开 `preview-source.json` 实际源 SHA 及 Pages 工作流成功为准。

### 2026-10-31 · 无声回信（黑）原版贴图图标重叠专项修复

- 源 SullyOS 现有开发分支 `remove-checkphone-vrworld-lifesim` 的本轮发布源码 HEAD：`e4a021af99d0524a15cab1231afa23f92a01d4ef`。没有新建开发分支，没有修改正式站。
- 用户 Android 截图发现返回箭头、右上角闪电和底部加号/发送按钮上，“原生 SVG + 原版装扮贴纸”被同时渲染；只修改该预设 CSS，把作者贴图当作替换图标而非覆盖层，并对停止生成/语音模式保留对应的原生状态提示。
- 真实 Chromium 360px 展示私聊/发消息/停止生成/转账/心象/群聊，专门测量原生 SVG 被替换、停止图标被保留、顶栏真实电话按钮不互相挤压；源码 CI `41213138738` 31 项单测和目标 TypeScript 检查通过，浏览器图标与布局断言通过并保存截图。
- 仅用于独立预览站的部署触发；以部署流程实际公网 `preview-source.json` 验证源码 SHA 为最终发布结果。
