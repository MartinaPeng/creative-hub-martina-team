# Creative Hub — AI Generator PRD 梳理

> 文档性质：PRD 整理底稿（生成场景分类 · 输入输出 · 待定项）  
> 更新日期：2026-07-14  
> 状态：草稿，供产品共创迭代  
> 相关文档：  
>
> - `../Creative-Hub-AI生成场景与竞品实现.md`（竞品对照）  
> - `../Creative-Hub-报表与Insight能力梳理.md`（Insight → 生成闭环）  
> - `../Creative-Hub-竞品列表.md`  
> - 后续 PRD 均放本目录：`creative-hub/PRD/`

---

## 0. 文档范围与原则


| 项       | 说明                                                                    |
| ------- | --------------------------------------------------------------------- |
| 范围      | Creative Hub 内 **Asset Generator** 及附属变体能力；不含投放创建 Campaign 全链路细节（可另文） |
| 命名      | 章节号按产品菜单级：`1.x` = 能力模块；括号 `(1)(2)…` = 生成模式                            |
| 公共约束    | 多数「净新生成」模式均需：**广告类型（Ad Type）必选**；提示词 / 参考素材 / Logo 为「按模式必填或选填」        |
| 与竞品文档关系 | 竞品分析看「市场怎么做」；本文看「我们 PRD 要定什么」                                         |


### 0.1 公共字段定义（全模块复用）


| 字段                         | 必填性通则           | 说明                                                             |
| -------------------------- | --------------- | -------------------------------------------------------------- |
| **Ad Type（广告类型）**          | 生成类多数必选         | 决定版位规格、合规约束、默认像素；如 SP / SB / SD / Display / Video 等（以平台支持矩阵为准） |
| **Prompt（提示词）**            | 按模式             | Text to * 必填；其他模式选填辅助                                          |
| **Reference Asset / Logo** | 选填              | 品牌一致性：可从 Asset 库选参考图、Logo；用于约束风格 / 占位                          |
| **Source Image**           | Image to * 必填   | 来自上传或 Asset 库已有图                                               |
| **Product（1–3）**           | Product to * 必填 | **当前已对接平台**下的商品；数量 1–3                                         |
| **Product URL**            | URL to * 必填     | 任意平台（不限当前投放账号）的商品页 URL；系统抓取标题 / 图 / 卖点                         |
| **Target Pixel(s)**        | 多像素变体必选         | 输出尺寸清单                                                         |
| **Target Language(s)**     | 多语言变体必选         | 目标文案 / 口语语言                                                    |




### 0.2 Asset Generator 能力树（总览）

```
1. Asset Generator
├── 1.1 Image Generator
│   ├── (1) Text to Image
│   ├── (2) Image to Image
│   ├── (3) Product to Image
│   └── (4) URL to Image
├── 1.2 Video Generator
│   ├── (1) Text to Video        【待定 / 可二期】
│   ├── (2) Image to Video
│   ├── (3) Product to Video
│   └── (4) URL to Video         【待定 / 可二期，对齐 Image】
├── 1.3 多像素变体（Multi-Pixel Variants）
├── 1.4 多语言变体（Multi-Language Variants）
├── 1.5 质量 / 合规优化（Optimize Existing）  【建议补齐，见下文】
├── 1.6 Compliance Check（投放前 / 投放中规则校验）  【待办】
└── 1.7 Video Predictive Score（视频效果潜力分）  【待办 · 仅 Video】
```
---



## 1. Asset Generator

**目标**：在 Creative Hub 内一站式生成可入库、可绑定 Ad Type 规格约束的 Image / Video Asset，并支持从母版扩像素与语言变体。

**主流程（净新生成通式）**：

1. 选择生成类型（Image / Video）与模式（Text / Image / Product / URL…）
2. 填写必填源 + 选填 Prompt / 参考图 / Logo
3. **选择 Ad Type**（及平台，若 Ad Type 依赖）
4. （可选）勾选同时输出多像素 / 多语言
5. 生成 → 预览 → 入库 / 进入编辑 →（下游）关联 Creative / Campaign

---



### 1.1 Image Generator


| 模式                   | 必填         | 选填                    | Ad Type | 备注                 |
| -------------------- | ---------- | --------------------- | ------- | ------------------ |
| (1) Text to Image    | Prompt     | 参考Image / Logo        | **必选**  | 纯提示词起稿             |
| (2) Image to Image   | 源图片        | Prompt；参考Image / Logo | **必选**  | 基于已有图改写 / 风格化      |
| (3) Product to Image | 平台产品 1–3 个 | Prompt；参考Image / Logo | **必选**  | 产品仅限**当前支持平台**     |
| (4) URL to Image     | 商品 URL     | Prompt；参考素材 / Logo    | **必选**  | URL **不限**是否当前账号平台 |




#### (1) Text to Image


| 项    | PRD 要点                                     |
| ---- | ------------------------------------------ |
| 用户意图 | 无现成商品图 / 参考图时，用文案描述生成广告静图                  |
| 必填   | **Prompt**；**Ad Type**                     |
| 选填   | 参考素材、Logo（建议：有品牌规范时鼓励选 Logo）               |
| 输出   | 1–N 张静图 Asset；带 Ad Type 关联的推荐像素（可与 1.3 联用） |
| 校验   | Prompt 为空不可生成；Ad Type 未选不可生成               |
| 开放问题 | 单次默认生成张数？是否强制绑定 Brand / Profile？           |




#### (2) Image to Image


| 项    | PRD 要点                            |
| ---- | --------------------------------- |
| 用户意图 | 基于已有主图 / 广告图做改写、换背景、风格迁移、轻微重构     |
| 必填   | **源图片**（上传或 Asset）；**Ad Type**    |
| 选填   | Prompt（指导改哪）；参考素材 / Logo          |
| 输出   | 基于源图的新静图 Asset（建议保留「源 Asset」血缘关系） |
| 校验   | 未选源图不可生成                          |
| 开放问题 | 源图是否必须已是库内 Asset？是否允许任意上传临时图？     |




#### (3) Product to Image


| 项    | PRD 要点                               |
| ---- | ------------------------------------ |
| 用户意图 | 从 Pacvue 已对接平台的商品目录拉产品信息生成广告图        |
| 必填   | **产品 1–3 个**（当前支持平台）；**Ad Type**     |
| 选填   | Prompt；参考素材 / Logo                   |
| 数据来源 | 商品主图、标题、关键属性、类目等（以各平台 API 能力为准）      |
| 输出   | 静图 Asset；可写入 Product 关联元数据           |
| 校验   | 0 个产品不可生成；>3 需拦截；产品须属当前支持平台          |
| 开放问题 | 多产品（2–3）时构图策略（拼图 / 主副品 / 系列海报）是否可配置？ |




#### (4) URL to Image


| 项        | PRD 要点                                                                                                                                         |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| 用户意图     | 粘贴任意电商 / 零售商品页 URL，抓取后出图（不依赖账号内商品库）                                                                                                            |
| 必填       | **Product URL**；**Ad Type**                                                                                                                    |
| 选填       | Prompt；参考素材 / Logo                                                                                                                             |
| 与 (3) 差异 | 不限制「当前支持平台账号」；抓取失败需明确错误态与重试                                                                                                                    |
| 输出       | 静图 Asset；建议存 URL、抓取快照摘要                                                                                                                        |
| 校验       | URL 格式非法 / 抓取失败不可进生成；Ad Type 必选                                                                                                                |
| 开放问题     | 支持站点白名单？反爬失败兜底（改 Product to Image / 手动传图）？竞品参照：[Creatify URL to Video](https://creatify.ai/features/url-to-video)（视频侧），静图侧逻辑可对齐「URL → 解析 → 生成」 |


---



### 1.2 Video Generator

> 编号与 Image 对齐。当前你确认的一期能力为 **(2)(3)**；**(1)(4)** 建议保留占位，避免菜单日后错位。


| 模式                   | 一期？    | 必填          | 选填                 | Ad Type |
| -------------------- | ------ | ----------- | ------------------ | ------- |
| (1) Text to Video    | 建议二期   | Prompt      | 参考素材 / Logo        | **必选**  |
| (2) Image to Video   | **一期** | 源图片         | Prompt；参考素材 / Logo | **必选**  |
| (3) Product to Video | **一期** | 产品 1–3      | Prompt；参考素材 / Logo | **必选**  |
| (4) URL to Video     | 建议二期   | Product URL | Prompt；参考素材 / Logo | **必选**  |




#### (2) Image to Video


| 项    | PRD 要点                                |
| ---- | ------------------------------------- |
| 用户意图 | 静图驱动动态：镜头运动、产品展示动效、简单口播背景等（具体能力按模型定）  |
| 必填   | **源图片**；**Ad Type**（视频类 Ad Type）      |
| 选填   | Prompt；参考素材 / Logo                    |
| 输出   | Video Asset；时长 / 比例受 Ad Type 规格约束     |
| 开放问题 | 时长默认与上限？是否含配音 / 字幕？是否强制 9:16 / 1:1 等？ |




#### (3) Product to Video


| 项           | PRD 要点                         |
| ----------- | ------------------------------ |
| 用户意图        | 用账号内 1–3 个商品信息直接出视频广告          |
| 必填          | **产品 1–3**；**Ad Type**         |
| 选填          | Prompt；参考素材 / Logo             |
| 与 Image (3) | 同源商品选择器，输出介质为视频                |
| 开放问题        | 多产品视频叙事（对比 / 系列 / 卖点轮播）模板是否预置？ |




#### (1) Text to Video · (4) URL to Video —— 占位


| 模式            | 建议                                                  |
| ------------- | --------------------------------------------------- |
| Text to Video | 与 Image (1) 对称；成本与质控要求通常更高，可二期                      |
| URL to Video  | 对齐全站竞品强项（Creatify）；可与 Image (4) 共用 URL 解析服务，仅渲染管线不同 |


---



### 1.3 多像素变体（Multi-Pixel Variants）


| 项       | PRD 要点                                   |
| ------- | ---------------------------------------- |
| 定位      | **适配类**，非从零生成：基于已有 Image（或生成结果）扩出多尺寸     |
| 入口      | ① 生成完成页勾选「同时导出多像素」；② Asset 详情「生成像素变体」    |
| 必填      | 源 Asset；**目标像素列表**（可随 Ad Type / 平台推荐默认集） |
| 选填      | 是否允许轻微重构图（智能裁切 vs 等比留白）                  |
| Ad Type | 建议必选或从源 Asset 继承，用于拉「合规像素清单」             |
| 输出      | 一组同概念不同像素的 Asset（建议同 Asset Group / 版本家族） |
| 与 1.1   | 可在一次 Text/Image/Product/URL 生成任务末尾串联     |
| 开放问题    | 视频是否也支持多比例变体？像素清单权威来源（平台文档 / 内部配置表）？     |


---



### 1.4 多语言变体（Multi-Language Variants）


| 项       | PRD 要点                             |
| ------- | ---------------------------------- |
| 定位      | **适配类**：保留视觉主体，替换 / 重绘画面内文案与字幕语言   |
| 入口      | ① 生成时勾选；② 已有 Asset「生成语言变体」         |
| 必填      | 源 Asset；**目标语言**（可多选）              |
| 选填      | Prompt（语气 / 禁用词）；是否同步译 Brand Claim |
| Ad Type | 继承源；若某语言有平台文案限制，按 Ad Type + 语言校验   |
| 输出      | 多语言版本 Asset 家族；元数据含 `language`     |
| 与 1.3   | 常与多像素组合：语言 × 像素矩阵（需提示量级，防爆炸）       |
| 开放问题    | 纯图无字时行为？仅字幕轨 vs 画面内嵌字重绘？           |


---



### 1.5 质量 / 合规优化（Optimize Existing）——建议补齐

> 你原稿 1.5 为空。结合 Creative Hub Insight 主场景「质量检测 → AI 优化 → **更新 Creative**」，建议把 **1.5** 定为「对**已有** Asset 的优化」，与 1.1/1.2 的「净新生成」区分。


| 项             | PRD 要点                                                |
| ------------- | ----------------------------------------------------- |
| 定位            | 不从零出片：对库内 / 在投素材做 **质量修复、规格合规修复、轻度增强**                |
| 典型触发          | Insight 质量 / 拒审检出；用户在 Asset 详情点「AI Optimize」          |
| 必填            | 源 Asset；问题类型或检测结果（可自动带入）                              |
| 选填            | Prompt（额外要求）；Logo / 参考；是否覆盖原 Asset vs 另存新版本           |
| Ad Type       | **建议必选或继承**：决定合规规则（字图比、安全区、禁元素等）                      |
| 输出            | 优化后 Asset；动作闭环倾向 **Update Creative**（非必须新建 Campaign）  |
| 子能力建议（可拆 MVP） | a. 清晰度 / 构图增强 b. 裁切适配某 Ad Type c. 拒审原因修复（去禁文字、调字号占比等） |
| 非目标（可另开模块）    | 大幅创意重做 → 应引导回 Image to Image / Product to Image       |


**若 1.5 不想做成「优化」**，备选命名（择一即可，勿并列膨胀）：


| 备选                   | 说明                                                       |
| -------------------- | -------------------------------------------------------- |
| 1.5 Batch / 风格变体     | 同输入一次出多风格（更接近竞品 Batch Mode）                              |
| 1.5 From Winning Tag | Insight 胜出 Tag 驱动再生成（偏闭环，可归 Insight 入口而非 Generator 一级菜单） |


**推荐**：一级菜单用 **Optimize**；Batch / From Tag 作为入口参数或 Insight 跳转，避免 Generator 菜单过长。

---

### 1.6 Compliance Check——功能待办

> 对标 Celtra **Pre- and In-flight Checks**：按品牌 / 平台 Criteria 自动审核素材是否合格（投放前 + 投放中）。与 **1.5 Optimize** 分工：本模块负责 **检出 Pass/Fail**；1.5 负责检出后的 **修复 / 再生**。


| 项    | PRD 要点                                                                 |
| ---- | ---------------------------------------------------------------------- |
| 定位   | 对 Image / Video Asset 跑可配置规则清单，输出逐条 Criteria Result（Yes / No）与版本对照     |
| 典型规则 | 前 N 秒出 Brand / Logo；正情绪；移动端构图；每帧字数上限；出镜 Talent；时长区间；字图比 / 安全区等（可按平台扩展） |
| 触发   | 生成后自动检；Asset / Creative 详情手动检；Insight 质量 / 拒审场景入口                       |
| 输出   | Criteria 清单 + Pass/Fail；不合格项可跳转 **1.5 Optimize** 或提示人工修改              |
| 非目标  | 不做大幅创意重做；不做预测打分（预测见 **1.7**，且仅 Video）                                      |
| 状态   | **待办**（Idea / PRD 待立项）                                                   |


---

### 1.7 Video Predictive Score（视频效果潜力分）——功能待办

> 对标 Smartly **Creative Predictive Potential** 等：用 CV + 注意力模型「读」视频，上线前给出效果潜力分。**范围仅限 Video**，不覆盖 Image。


| 项    | PRD 要点 |
| ---- | ------ |
| 定位   | 对 Video Asset 上线前打 AI 效果潜力分，辅助筛选 / 优先投放 / 先改再投 |
| 范围   | **仅 Video** |
| 主要因素 | 见下表（创意感知模型） |
| 触发   | 视频生成后自动评；Asset / Creative 详情手动评；Insight「上线前潜力」入口 |
| 输出   | 综合潜力分 + 分项（Attention / Emotion / Engagement 等）+ 热力图 / 衰减曲线 + 改进建议 |
| 与 1.6 区别 | 1.6 = 规则 Pass/Fail（合规硬门槛）；1.7 = 软性效果预测 |
| 状态   | **待办** |


**创意感知模型 — 主要因素（仅 Video）**

| 因素 | 在算什么 |
|------|----------|
| **Attention（注意力）** | 视线落点、热力图、开场几秒能否抓住人 |
| **Emotion / Sentiment（情绪）** | 情绪基调是否正向、是否易引发共鸣 |
| **Engagement（互动潜力）** | 预估点赞 / 评论 / 停留等互动倾向 |
| **节奏与衰减（Decay）** | 哪一段掉注意力、节奏是否拖沓 |
| **画面 / 文案细节** | 构图、卖点呈现、文案与视觉配合（常附改进建议） |


---



## 2. 模式对照总表（便于评审）


| ID    | 模块       | 模式                 | 主输入          | Prompt | 参考/Logo | Ad Type | 产品范围       |
| ----- | -------- | ------------------ | ------------ | ------ | ------- | ------- | ---------- |
| 1.1.1 | Image    | Text to Image      | —            | **必填** | 选填      | **必选**  | —          |
| 1.1.2 | Image    | Image to Image     | 图片           | 选填     | 选填      | **必选**  | —          |
| 1.1.3 | Image    | Product to Image   | 产品 1–3       | 选填     | 选填      | **必选**  | 当前支持平台     |
| 1.1.4 | Image    | URL to Image       | URL          | 选填     | 选填      | **必选**  | 任意 URL     |
| 1.2.1 | Video    | Text to Video      | —            | **必填** | 选填      | **必选**  | —（二期）      |
| 1.2.2 | Video    | Image to Video     | 图片           | 选填     | 选填      | **必选**  | —          |
| 1.2.3 | Video    | Product to Video   | 产品 1–3       | 选填     | 选填      | **必选**  | 当前支持平台     |
| 1.2.4 | Video    | URL to Video       | URL          | 选填     | 选填      | **必选**  | 任意 URL（二期） |
| 1.3   | Variants | Multi-Pixel        | 源 Asset      | —      | —       | 继承/必选   | —          |
| 1.4   | Variants | Multi-Language     | 源 Asset      | 选填     | —       | 继承      | —          |
| 1.5   | Optimize | Quality/Compliance | 源 Asset + 问题 | 选填     | 选填      | 继承/必选   | —          |
| 1.6   | Check    | Compliance Check   | 源 Asset      | —      | —       | 继承/必选   | —【待办】      |
| 1.7   | Score    | Video Predictive Score | Video Asset | —   | —       | 选填      | **仅 Video**【待办】 |
---



## 3. 跨切面需求（PRD 后续章节建议）

以下建议在正式 PRD 中单开章节，本文仅列提纲：


| 章节                  | 内容                                                             |
| ------------------- | -------------------------------------------------------------- |
| 平台 × Ad Type × 像素矩阵 | 各零售媒体可选项与默认规格                                                  |
| 输出与入库               | Asset 命名、Tag / Auto Tag、Asset Group、血缘（source / variant of）    |
| 权限与计费               | 谁可生成；次数 / 队列；失败重试                                              |
| 合规与审核               | 生成后自动规格检查；**1.6 Compliance Check**；拒审字段回写                        |
| 预测评估（Video）         | **1.7 Video Predictive Score**：Attention / Emotion / Engagement / Decay 等 |
| 与 Insight 联动        | 场景 1 质量 → 1.6 检出 → 1.5 优化；场景 6 上线前打分 → 1.7（仅 Video）；场景 3 多变体 → 1.1/1.2 + 批量；场景 4 大促 → Product/URL 批量 |
| 非功能                 | 耗时预期、并发、可取消、预览水印策略                                             |


---



## 4. 待你确认（阻塞项）

1. **1.5** 是否采用「质量 / 合规优化」？还是 Batch / 其他？
2. Video **(1) Text to Video / (4) URL to Video** 是否明确二期？
3. **Ad Type** 是否在所有 1.1 / 1.2 模式强制？（当前按你的描述为「需选择」→ 本文按必选落稿）
4. Product **1–3**：多产品时的默认构图 / 叙事是否要在 MVP 可配？
5. URL 抓取：是否做站点白名单与失败降级路径？
6. **1.6 Compliance Check**：MVP 先做品牌 Criteria，还是先做零售平台规格硬门槛？与现有 Creative Analysis 如何合并？
7. **1.7 Video Predictive Score**：MVP 是否只做 Attention + Decay，Emotion / Engagement 二期？是否需要账户历史样本（Pencil 路线）还是纯感知模型（Smartly 路线）？

---

## 4.1 AI 生成功能待办（Backlog）

| # | 功能 | 状态 | 备注 |
|---|------|------|------|
| 1 | Image Creative 一键生成（Headline / Subheadline / CTA Text / Logo / Image） | Idea 文案已整理 | 模型 + Prompt；本期仅 Image |
| 2 | AI Agent（Image Generation） | Idea 文案已整理 | 对话式：产品 / 参考图 + 人群 / 风格 / 细节 |
| 3 | AI Video Generation（Pacvue 自研） | Idea 文案已整理 | 替代有限 Amazon API；跨平台 |
| 4 | **Compliance Check** | **待办** | 对标 Celtra Pre-/In-flight；PRD §1.6 |
| 5 | 1.5 Optimize Existing | PRD 建议补齐 | 检出后的修复 / 再生，承接 1.6 |
| 6 | **Video Predictive Score（视频效果潜力分）** | **待办** | **仅 Video**；创意感知：Attention / Emotion / Engagement / Decay / 画面文案；PRD §1.7 |

---



## 5. 修订记录


| 日期         | 说明                                                       |
| ---------- | -------------------------------------------------------- |
| 2026-07-14 | 首版：按产品口述结构梳理 Asset Generator 1.1–1.5，补齐 Video 编号与 1.5 建议 |
| 2026-07-16 | 新增 **1.6 Compliance Check**；补充 §4.1 AI 生成功能待办列表 |
| 2026-07-16 | 新增 **1.7 Video Predictive Score**（仅 Video）；待办列表第 6 条 |
