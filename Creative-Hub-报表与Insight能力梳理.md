# Creative Hub：报表分析 / Insight 能力梳理

> 更新日期：2026-07-13  
> 范围：先梳理报表分析与 Insight 相关能力（竞品 + Creative Hub 现状），**暂不展开工作流落地设计**。  
> 相关文档：`Creative-Hub-竞品列表.md` · `Creative-Hub-AI生成场景与竞品实现.md`（Gen AI 场景与竞品实现）

---

## 1. 能力框架（先统一口径）

把「报表分析 / Insight」拆成以下能力层，便于横向对比：


| 能力层         | 说明                                           | 典型产出          |
| ----------- | -------------------------------------------- | ------------- |
| 基础报表        | 按广告结构 / 素材查看曝光、点击、花费、转化、ROAS 等               | 列表、图表、排行榜     |
| 多维透视        | 按 Platform、Ad Type、Brand、Tag、Asset Group 等切片 | 交叉对比、分组汇总     |
| 跨平台对比       | 同一素材 / Tag 在不同零售媒体或渠道的表现差异                   | 跨平台差距、同组分化    |
| 创意归因        | 把绩效归因到 Tag、元素、Hook / CTA 等创意特征               | Tag 胜出榜、元素贡献  |
| 诊断洞察        | 在数字之上给出「健康 / 疲劳 / 异常 / 机会」判断                 | 健康分、疲劳标记、异常卡  |
| 预测评估        | 上线前对素材潜力打分或预估                                | 预测分、注意力热力图    |
| 测试洞察        | 结构化 A/B 或多元测试，找胜出元件                          | 元件胜出结论        |
| 对话式 Insight | 自然语言提问，返回结构化洞察                               | Agent 问答、自动摘要 |


说明：本阶段只梳理「能看清什么、能解释什么」，不讨论「建议后如何跳到生成 / 替换」。

---

## 2. Creative Hub 现状（报表 / Insight）

### 2.1 已具备


| 能力                | 现状说明                                                                              | 来源                                                                                                       |
| ----------------- | --------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| 基础报表              | Creative 页查看跨平台素材绩效；Asset 详情含关联活动与绩效                                              | V1.0 发布说明                                                                                                |
| Asset Group 对比    | 相似素材成组，可跨平台 / Campaign / Ad Group 比较                                              | V1.0 发布说明                                                                                                |
| Tag 透视            | 手动 Tag + AI Auto Tag；可按 Tag 看绩效（含规划中的 Dashboard 维度）                               | V1.0；Dashboard PRD                                                                                       |
| 跨平台统一数据           | Amazon / ADSP / Walmart 等统一管理与查看（持续扩展）                                            | V1.0；后续迭代                                                                                                |
| 对话式分析（规划/建设中）     | Pacvue Agent · Creative Hub Analysis：自然语言查创意绩效、排行榜、Tag 分析、跨平台对比                   | [PACID-6345](https://pacvue-enterprise.atlassian.net/browse/PACID-6345)                                  |
| Creative 绩效分析能力规划 | 支持按 Asset Tag、Asset Object、Platform、Ad Type 筛选；Group by Creative/Ad 或 Asset Group | [Creative Performance Analysis](https://pacvue-enterprise.atlassian.net/wiki/spaces/PRD/pages/475103692) |


### 2.2 相对薄弱或尚未成体系


| 能力           | 现状判断                                                      |
| ------------ | --------------------------------------------------------- |
| 诊断洞察         | 仍以查数、列表、图表为主；缺少标准化的「健康分 / 疲劳 / 异常结论」                      |
| 创意元素归因       | 有 Tag / Object 方向，但未达到 VidMob 级元素拆解与贡献解释                  |
| 预测评估         | Creative Analysis 偏规格合规，缺少上线前效果潜力分                        |
| 测试洞察         | 未见完整的结构化多元测试归因能力                                          |
| Dashboard 洞察 | Dashboard 已有需求方向（Tag / Campaign Tag / AI 素材维度），完整洞察体验仍在建设 |


### 2.3 一句话定位（现状）

Creative Hub 在 **跨零售媒体素材绩效报表 + Tag / Asset Group 透视 +（建设中）Agent 对话分析** 上有基础；  
在 **诊断结论、元素级归因、预测打分、测试洞察** 上与头部 Insight 型竞品仍有差距。

---

## 3. 竞品报表 / Insight 能力梳理

只收录在 Report / Insight 上有代表性能力的产品（生产型弱报表产品略写）。

### 3.1 能力对照总表


| 产品            | 链接                                                       | 基础报表    | 多维透视           | 跨平台对比       | 创意归因              | 诊断洞察                | 预测评估                    | 测试洞察   | 对话式 Insight   |
| ------------- | -------------------------------------------------------- | ------- | -------------- | ----------- | ----------------- | ------------------- | ----------------------- | ------ | ------------- |
| Creative Hub  | —                                                        | 有       | 有（Tag / Group） | 有（跨 RMN）    | 中（Tag）            | 弱                   | 弱                       | 弱      | 建设中（Agent）    |
| VidMob        | [vidmob.com](https://www.vidmob.com/)                    | 强       | 强              | 中（多社媒渠道）    | 极强（元素级）           | 强（Health / Fatigue） | 中                       | 中      | 中             |
| Motion        | [motionapp.com](https://motionapp.com/)                  | 强       | 强（Tag 集群）      | 弱–中（偏 Meta） | 强（AI Tag）         | 中强                  | 弱–中                     | 中      | 强（AI 任务 / 摘要） |
| Smartly       | [smartly.io](https://www.smartly.io/)                    | 强       | 强              | 强（社媒 / 程序化） | 强                 | 强                   | 强（Predictive Potential） | 强      | 中强            |
| Celtra        | [celtra.com](https://celtra.com/)                        | 强       | 强              | 强（多渠道）      | 强                 | 强                   | 强                       | 中      | 中             |
| Marpipe       | [marpipe.com](https://www.marpipe.com/)                  | 中       | 强（元件维度）        | 弱           | 极强（Hook/Body/CTA） | 中                   | 弱                       | 极强     | 弱             |
| Omneky        | [omneky.com](https://www.omneky.com/)                    | 中强      | 中强             | 中           | 中                 | 中                   | 中                       | 中      | 弱–中           |
| Flashtalking  | [flashtalking.com](https://www.flashtalking.com/)        | 强（投放验证） | 中              | 强（多 DSP）    | 弱–中               | 中                   | 弱                       | 弱      | 弱             |
| Pencil        | [trypencil.com](https://www.trypencil.com/)              | 弱–中     | 弱              | 弱           | 弱                 | 弱                   | 强（预测分）                  | 弱      | 弱             |
| Creatify      | [app.creatify.ai](https://app.creatify.ai/tool/ai-tools) | 中       | 弱–中            | 中           | 弱                 | 弱                   | 弱–中                     | 中（A/B） | 中（Ad Chat）    |
| AdCreative.ai | [adcreative.ai](https://www.adcreative.ai/)              | 弱       | 弱              | 弱           | 弱                 | 弱                   | 中（转化评分）                 | 弱      | 弱             |
| Rocketium     | [rocketium.ai](https://rocketium.ai/)                    | 弱       | 弱              | 弱（偏生产合规）    | 弱                 | 弱                   | 弱                       | 弱      | 弱             |
| Meta Ads      | [business.facebook.com](https://business.facebook.com/)  | 强       | 强（生态内）         | 无（单生态）      | 弱–中               | 中                   | 中                       | 中      | 弱–中           |
| Google Ads    | [ads.google.com](https://ads.google.com/)                | 强       | 强（生态内）         | 无（单生态）      | 弱–中               | 中                   | 中                       | 中      | 弱–中           |


### 3.2 重点竞品能力说明

#### VidMob

- **链接**：[https://www.vidmob.com/](https://www.vidmob.com/)
- **强项**：Creative Intelligence；计算机视觉拆解 logo、文案、人物、情绪等，并关联绩效；Creative Health Score、Creative Fatigue Tracker。
- **报表形态**：元素级对比、版位 / 目标 / 受众侧表现、行业与账户基准。
- **对 Creative Hub 的参考价值**：诊断层（健康 / 疲劳）与「为什么差」的可解释归因。

#### Motion

- **链接**：[https://motionapp.com/](https://motionapp.com/)
- **强项**：AI Tagging 自动给素材打多类标签；按 Tag 集群看胜出模式；AI 任务生成账户 / 报表级摘要。
- **报表形态**：素材与指标同屏；比较报表；Tag 维度切分。
- **对 Creative Hub 的参考价值**：把 Auto Tag 真正用进默认分析视图，而不是只存在于 Tag 管理页。

#### Smartly

- **链接**：[https://www.smartly.io/](https://www.smartly.io/) · [Creative Predictive Potential](https://www.smartly.io/product-features/creative-predictive-potential)
- **强项**：投放与创意一体报表；Creative Predictive Potential（上线前注意力 / 情绪 / 互动预测）；测试反馈与跨渠道洞察。
- **报表形态**：统一 Intelligence 视图，强调「发生了什么 + 可能发生什么」。
- **对 Creative Hub 的参考价值**：上线前预测分 + 上线后真实绩效的两阶段评估。

#### Celtra

- **链接**：[https://celtra.com/](https://celtra.com/)
- **强项**：创意生命周期绩效洞察；预测打分；元素级优化建议；跨市场 / 跨渠道表现。
- **报表形态**：生产—激活—洞察一体中的绩效与治理视图。
- **对 Creative Hub 的参考价值**：Insight 作为素材全生命周期中的常驻能力，而不是独立报表孤岛。

#### Marpipe

- **链接**：[https://www.marpipe.com/](https://www.marpipe.com/)
- **强项**：结构化多元测试；Hook / Body / CTA 等元件胜出分析。
- **报表形态**：测试结果导向，明确「哪个元件赢」。
- **对 Creative Hub 的参考价值**：Tag / 元件维度的测试归因模型。

#### Omneky

- **链接**：[https://www.omneky.com/](https://www.omneky.com/)
- **强项**：AI 创意生成 + 多渠道表现分析。
- **参考价值**：轻量多渠道 Insight，非主对标。

#### Pencil

- **链接**：[https://www.trypencil.com/](https://www.trypencil.com/)
- **强项**：上线前预测打分；生成侧强。
- **参考价值**：预测评估形态参考。

#### Creatify

- **链接**：[https://app.creatify.ai/tool/ai-tools](https://app.creatify.ai/tool/ai-tools)
- **强项**：Ad Chat / A/B；视频生成侧强。
- **参考价值**：轻量对话式洞察参考。

#### AdCreative.ai

- **链接**：[https://www.adcreative.ai/](https://www.adcreative.ai/)
- **强项**：转化评分。
- **参考价值**：轻量预测评分，报表深度弱。

#### Rocketium

- **链接**：[https://rocketium.ai/](https://rocketium.ai/)
- **强项**：零售合规生产。
- **参考价值**：报表 / Insight 弱，偏生产侧。

#### Flashtalking

- **链接**：[https://www.flashtalking.com/](https://www.flashtalking.com/)
- **强项**：投放验证、程序化效果追踪。
- **短板**：缺跨零售媒体统一创意 Insight。

#### Meta Ads / Creative Hub

- **链接**：[https://business.facebook.com/](https://business.facebook.com/)
- **强项**：生态内原生投放与创意报表完整。
- **短板**：单生态，无跨 RMN 统一 Insight。

#### Google Ads

- **链接**：[https://ads.google.com/](https://ads.google.com/)
- **强项**：生态内 Asset 与投放报表完整。
- **短板**：单生态，无跨 RMN 统一 Insight。

---

## 4. 按能力层看差距（Creative Hub vs 头部）


| 能力层         | Creative Hub                 | 头部水平参考                    | 差距简述                     |
| ----------- | ---------------------------- | ------------------------- | ------------------------ |
| 基础报表        | 已有跨平台素材绩效                    | Smartly / 平台原生            | 基础可用，体验与指标完整度可持续补齐       |
| 多维透视        | Tag / Asset Group / Platform | Motion / Celtra           | 方向正确，默认分析入口与联动可加强        |
| 跨平台对比       | 跨 RMN 是优势                    | 多数竞品偏社媒 / 单生态             | **相对优势**，应作为 Insight 主叙事 |
| 创意归因        | Tag 级                        | VidMob 元素级 / Marpipe 元件级  | 中等差距                     |
| 诊断洞察        | 弱                            | VidMob Health / Fatigue   | 明显差距                     |
| 预测评估        | 弱                            | Smartly / Pencil / Celtra | 明显差距                     |
| 测试洞察        | 弱                            | Marpipe                   | 明显差距                     |
| 对话式 Insight | 建设中                          | Motion AI 任务              | 可快速追平并叠加跨 RMN 数据优势       |


---

## 5. 报表分析角度 → 可产出的建议类型

> 目标：先想清楚「从哪些角度读报表」，以及每个角度**自然能给出什么建议**。  
> 本阶段只做角度与建议类型梳理，不展开产品落地与工作流设计。

### 5.1 总览：分析角度地图


| 分析角度              | 核心问题           | 主要看什么                                          | 典型建议类型                | Creative Hub 现状      |
| ----------------- | -------------- | ---------------------------------------------- | --------------------- | -------------------- |
| A. 绩效排行           | 谁好谁差？          | ROAS / CTR / CVR / Spend 排行榜                   | 放大胜者 / 替换或下架败者        | 已有基础报表               |
| B. 投入产出失衡         | 钱花在哪却没效果？      | 高 Spend + 低 ROAS / 高 CPA                       | 优先刷新高花费低效素材           | 可基于现有指标做             |
| C. 跨平台落差          | 同一素材为何平台间差很大？  | 同 Asset / Asset Group 跨 Amazon / Walmart / DSP | 只换差的平台素材 / 把赢家分发到弱平台  | **优势角度**             |
| D. 时间趋势与疲劳        | 是不是开始疲了？       | 近 7/14/30 天斜率、花费天数                             | 疲劳刷新 / 暂缓加投           | 诊断层较弱，规则可定义          |
| E. Tag / 创意特征     | 什么风格在赢？        | Tag、场景、风格、Object 聚合绩效                          | 基于胜出 Tag 扩量；停用失效 Tag  | Tag 有，默认分析可加强        |
| F. Asset Group 分化 | 相似图为何表现不一？     | Group 内跨平台 / 跨广告对比                             | 组内用赢家替换输家             | Asset Group 已有       |
| G. 广告结构下钻         | 问题出在哪一层？       | Profile → Campaign → Ad Group → Creative       | 定位到具体 Creative 再建议动作  | 结构数据已有               |
| H. Ad Type / 版位   | 不同广告类型是否分化？    | SP / SB / SD / Display / 视频等                   | 按 Ad Type 差异化素材策略     | 维度已有                 |
| I. 品牌 / 产品线       | 哪条线素材更有效？      | Brand、产品、品类                                    | 资源向高潜品牌线倾斜            | Agent / 报表方向已有       |
| J. 规格与合规          | 能不能投、适不适合该广告位？ | 尺寸、格式、平台要求                                     | 合规修复 / Pixel Variants | Creative Analysis 偏此 |
| K. 同质化 / 多样性      | 是不是都长得太像？      | Tag 分布、相似素材占比                                  | 生成差异化变体               | 可结合 Tag / Group      |
| L. 上线前潜力（中长期）     | 还没投，值不值得投？     | 预测分、注意力                                        | 优先上线高分 / 先改再投         | 目前弱                  |
| M. 测试元件（中长期）      | 哪个部件在贡献？       | Hook / CTA / 主图等                               | 保留胜出元件、替换失败部件         | 目前弱                  |


### 5.2 各角度详解（分析什么 → 建议什么）

#### A. 绩效排行（Leaderboard）

- **分析**：Top / Bottom N（按 ROAS、CTR、Sales、Spend 等）；可加最低花费门槛避免样本噪音。  
- **可给建议**：  
  - 胜者：加大使用范围、复制到更多广告 / 平台  
  - 败者：替换素材、暂停关联、进入 AI 再生成队列

#### B. 投入产出失衡

- **分析**：Spend 高、效果差的交叉区（如高花费低 ROAS）；「浪费预算」清单。  
- **可给建议**：优先处理「烧钱最多」的差素材（比只盯绝对最差更有业务价值）。

#### C. 跨平台落差（Creative Hub 差异化主角度）

- **分析**：同一 Asset / Asset Group / Tag 在 Amazon vs Walmart vs ADSP 等的 ROAS / CTR 对比；找出「一边好一边差」。  
- **可给建议**：  
  - 只替换表现差的平台版本（不必全盘换）  
  - 把强平台赢家适配规格后分发到弱平台  
  - 检查是否规格 / 文案不适配某平台

#### D. 时间趋势与疲劳

- **分析**：按日 / 周看绩效斜率；投放天数 + 指标下滑；相对账户均值的「健康度」。  
- **可给建议**：标记疲劳 → 建议刷新 / 换图 / 换语言变体；未疲劳的胜者避免误杀。  
- **竞品参考**：VidMob Fatigue / Health Score；Smartly 疲劳预测。

#### E. Tag / 创意特征归因

- **分析**：按 Tag 聚合看胜出 / 失效模式；Auto Tag + 手动 Tag 交叉；「某场景 / 风格」整体好坏。  
- **可给建议**：  
  - 胜出 Tag：基于该风格再生成更多变体  
  - 失效 Tag：减少使用或改写该特征  
  - 空白 Tag：某类风格几乎没测过，建议补测
- **竞品参考**：Motion AI Tag + Comparative Report；VidMob 元素归因。

#### F. Asset Group 内部分化

- **分析**：相似素材成组后，组内谁好谁差；是否某一平台拖累整组。  
- **可给建议**：组内用高表现图替换低表现图；统一组策略（保留主图 / 换辅图）。

#### G. 广告结构下钻

- **分析**：先看账户 / Campaign 异常，再下钻到 Creative / Asset，避免「只看素材、忽略投放结构」。  
- **可给建议**：明确问题归属——是素材问题还是投放设置问题；仅素材问题时才建议换图 / 生成。

#### H. Ad Type / 版位差异

- **分析**：同一产品在 SB vs SD vs Display 等的素材表现差异。  
- **可给建议**：按广告类型配置不同主图 / 文案规格；弱类型用 Pixel Variants 做适配。

#### I. 品牌 / 产品线

- **分析**：Brand、品类、产品线维度的素材效率。  
- **可给建议**：创意产能向高潜品牌线倾斜；低效线先做诊断再扩量。

#### J. 规格与合规

- **分析**：是否满足平台像素、比例、格式、审核要求。  
- **可给建议**：不合规 → Creative Analysis / Pixel Variants / Language Variants；合规后再谈效果优化。

#### K. 同质化 / 多样性

- **分析**：在投素材的 Tag 分布是否过窄；Asset Group 是否大量近似图。  
- **可给建议**：提示「创意多样性不足」→ 生成差异化变体；对齐 Motion「diversification」思路。

#### L / M. 预测与测试（中长期角度）

- **L 预测**：上线前潜力分 → 建议先改再投或优先上线。  
- **M 测试**：元件胜出 → 建议下一轮组合怎么搭。  
- 当前 Creative Hub 可先占位，不作为近期主分析角度。

### 5.3 建议类型清单（从分析角度汇总）


| 建议类型       | 常见触发角度        | 一句话含义                |
| ---------- | ------------- | -------------------- |
| 放大胜者       | A / C / E / F | 把已验证有效的素材扩到更多位置 / 平台 |
| 替换败者       | A / B / D / F | 换掉低效或疲劳素材            |
| 只换弱平台      | C             | 保留强平台，只处理跨平台落差侧      |
| 基于 Tag 再生成 | E / K         | 按胜出风格扩量，或补差异化        |
| 规格 / 合规适配  | J / H         | 先满足可投，再谈效果           |
| 语言 / 尺寸变体  | H / J / D     | 用变体做刷新或适配，不必全新创意     |
| 暂停 / 减投提示  | B / D         | 高花费低效或持续下滑时降风险       |
| 补测空白风格     | E / K         | 某类 Tag 几乎未覆盖时建议试投    |
| 结构排查（非素材）  | G             | 先排除投放结构问题，再动素材       |


### 5.4 与 Creative Hub 能力的匹配（先做哪些角度）

**短期更适合做深（数据与能力已接近）**

1. C 跨平台落差
2. A 绩效排行 + B 投入产出失衡
3. E Tag 透视 + F Asset Group 分化
4. J 规格合规（已有 AI Optimizer 相关能力）

**中期补规则即可增强**

1. D 疲劳 / 趋势诊断
2. K 同质化提示
3. H Ad Type 差异策略

**长期再评估**

1. L 上线前预测
2. M 元件级测试归因

### 5.5 分析角度之间的组合用法（读报表时的推荐顺序）

不必一次上齐，可按「漏斗」读：

```
1. 先看失衡与排行（A/B）——锁定要关心的素材集合
2. 再看跨平台落差（C）——区分「全局差」还是「某平台差」
3. 再看 Tag / Group（E/F）——解释「为什么」属于哪类创意问题
4. 再看趋势疲劳（D）——判断是偶发还是持续恶化
5. 最后落到建议类型（替换 / 生成 / 适配 / 放大）——先定义建议，再谈产品跳转
```

---

## 5.6 Insight → AI → Campaign 闭环场景（产品方向）

> 用户已定 4 条主闭环；以下补充推荐场景，用于补齐「谁该被优化 / 何时换新 / 如何闭环验证」。  
> Gen AI「怎么生成、竞品如何实现」见：`Creative-Hub-AI生成场景与竞品实现.md`。

### 已定主场景


| #   | 场景                | 分析触发                           | 动作闭环                                          |
| --- | ----------------- | ------------------------------ | --------------------------------------------- |
| 1   | 质量检测              | 检出 Creative 问题（规格 / 合规 / 清晰度等） | 建议 AI 优化 → **更新 Creative**                    |
| 2   | Asset Group 跨平台应用 | 高表现素材未覆盖某些平台 / Ad Type         | AI 生成对应 Creative → **用 Creative 创建 Campaign** |
| 3   | 多变体生成             | 高表现素材需扩量测试                     | 多变体 AI 生成 → **用 Creative 创建 Campaign**        |
| 4   | 节日 / 促销预热         | 大促前 2–3 周                      | 提供 AI 样例变体 → **提前创建新 Campaign**               |


### 推荐补充场景


| #   | 场景                   | 为什么值得做                                                   | 建议闭环                                                                |
| --- | -------------------- | -------------------------------------------------------- | ------------------------------------------------------------------- |
| 5   | **疲劳刷新**             | 高花费素材 CTR/ROAS 持续下滑，不换则会持续烧钱；与场景 1 不同，问题在「效果衰减」而非「质量不合格」 | 标记疲劳 → AI 生成刷新变体 → **Replace 在投 Creative**（或新建一组再切换）                |
| 6   | **赢家跨 Ad Type 适配**   | 场景 2 强调平台缺口；本条强调同一平台内 SB→SD/Display 等类型未覆盖               | 检出 Ad Type 缺口 → Pixel / 版位适配生成 → **补建对应 Ad Type 的 Campaign / Ad**   |
| 7   | **败者止损 + 赢家替换**      | 投入产出失衡清单（高 Spend 低 ROAS）是最快体现 ROI 的建议                    | 锁定烧钱差素材 → 用同 Group / 同 Tag 赢家或 AI 变体 **Replace** → 观察 7/14 天 uplift |
| 8   | **胜出 Tag 扩量**        | 比「单张好图」更可规模化：某风格整体赢，但覆盖素材少                               | Tag 胜出榜 → 基于该 Tag **批量多变体生成** → 创建测试 Campaign                       |
| 9   | **同质化破局**            | 在投素材过于相似时，简单「再生成一张」收益有限；需要强调差异化约束                        | 检测同质化 → AI 生成「差异角度」变体（场景/构图/文案）→ 创建对比 Campaign                      |
| 10  | **合规 / 拒审修复**        | 与质量检测相邻，但更聚焦「审不过 / 平台拒审」                                 | 检出拒审或不合规原因 → AI 合规修复 → **更新后再投放**                                   |
| 11  | **库存 / 货架信号联动**（中长期） | 零售媒体差异化：断货、Buy Box 丢失时创意仍在花                              | 库存异常 → 建议暂停或换主推 SKU 创意 → **更新 Creative / 暂停 Campaign**              |
| 12  | **优化后验证回写**          | 以上任何闭环若无「换前 vs 换后」，建议无法证明价值                              | Replace / 新建后自动钉住变更事件 → Dashboard 展示 7/14 天 uplift                  |


### 场景优先级建议（相对你的 4 条）

1. **紧挨主场景、短期可拼**：5 疲劳刷新、7 败者止损、10 合规拒审（与质量检测共用检测能力）。
2. **强化 Creative Hub 差异化**：6 Ad Type 缺口（与场景 2 同族）、8 胜出 Tag 扩量（与场景 3 同族）。
3. **体验完整度**：12 验证回写（建议作为所有闭环的公共尾部，而不是独立功能）。
4. **中长期**：9 同质化破局、11 库存联动。

### 与「更新 Creative」vs「创建 Campaign」的分工


| 闭环出口                       | 适用场景                                        | 含义                       |
| -------------------------- | ------------------------------------------- | ------------------------ |
| **更新 / Replace Creative**  | 1 质量、5 疲劳、7 止损、10 合规                        | 原广告位还在投，换素材即可，不必新建活动     |
| **用 Creative 创建 Campaign** | 2 跨平台/类型扩覆盖、3 多变体测试、4 大促预热、8 Tag 扩量、9 同质化破局 | 新覆盖面或新测试意图，适合拉新活动 / 新测试组 |
| **公共尾部**                   | 12 验证回写                                     | 两种出口都应记变更事件并回看 uplift    |


---

## 6. 能力优先级观察（仅梳理，不定方案）

基于「先把报表 / Insight 看清楚」：

1. **巩固优势**：跨平台素材绩效、Asset Group、Tag 透视做成更完整的分析体验。
2. **补诊断层**：在现有指标之上增加可读的结论（异常、落差、疲劳等）——先能力定义，后谈跳转动作。
3. **用好 Auto Tag**：让 Tag 成为默认分析维度，而不仅是管理字段。
4. **Agent Analysis**：把对话式查数做成稳定的 Insight 入口（对齐 PACID-6345）。
5. **中长期再评估**：元素归因、预测分、结构化测试——需单独评估投入产出，本阶段不展开。
6. **分析角度落地顺序**：优先 C 跨平台落差 → A/B 排行与失衡 → E/F Tag 与 Group → D 疲劳规则。

---

## 7. 后续可继续深化的问题（暂挂）

- 各能力层的指标字典与维度字典如何统一？  
- Dashboard / Creative / Tag / Agent 四个入口如何分工，避免重复？  
- 诊断洞察的规则（疲劳、落差、同质化）如何定义？  
- 各分析角度的「建议文案模板」如何标准化？  
- 报表 / Insight 成熟后，再讨论「建议 → AI 生成 / 替换」工作流。

---

## 8. 可直接观看的图片 / 视频资源（无需注册）

> 本节约只保留**打开即可看**的公开资源（YouTube、公开产品页截图、公开博客 / PDF）。  
> 已排除：需注册试用、预约 Demo、Unlock On-Demand、登录 App 才能看的链接。

### 8.1 优先直接看（YouTube）


| 产品                   | 说明                                                              | 链接                                                                                         |
| -------------------- | --------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| Motion               | 官方短演示：How To Use Motion（Creative Strategists）                   | [https://www.youtube.com/watch?v=uCF8IauzHm8](https://www.youtube.com/watch?v=uCF8IauzHm8) |
| Motion               | Top Video Hooks 报表演示                                            | [https://www.youtube.com/watch?v=kOtEM5FVayc](https://www.youtube.com/watch?v=kOtEM5FVayc) |
| Motion               | AI Tagging 短视频介绍                                                | [https://www.youtube.com/watch?v=I9J5XSh9C2k](https://www.youtube.com/watch?v=I9J5XSh9C2k) |
| Motion               | Top 1% Creative Strategist（含 AI Tag / Comparative Report 讲解与界面） | [https://www.youtube.com/watch?v=RhWBZHF7AzA](https://www.youtube.com/watch?v=RhWBZHF7AzA) |
| Motion               | Meta Ads Testing Strategy（文中演示 AI Tagging 用法）                   | [https://www.youtube.com/watch?v=TIWDiHzsjbI](https://www.youtube.com/watch?v=TIWDiHzsjbI) |
| Smartly              | 平台入门教程（含 Intelligence Suite 介绍）                                 | [https://www.youtube.com/watch?v=uH9Nf1jZuEY](https://www.youtube.com/watch?v=uH9Nf1jZuEY) |
| Marpipe              | 创始人谈 Catalog / DPA 与创意测试思路（非完整后台，但可了解洞察逻辑）                      | [https://www.youtube.com/watch?v=MVg_o8WU6mo](https://www.youtube.com/watch?v=MVg_o8WU6mo) |
| Creatopy / The Brief | A/B testing 功能演示（公开可看）                                          | [https://www.youtube.com/watch?v=KDx69rM_3SM](https://www.youtube.com/watch?v=KDx69rM_3SM) |
| Segwise（相关）          | Static Ads + AI Tag 报表工作流演示（Tag × 绩效形态可参考）                      | [https://www.youtube.com/watch?v=zx7X9YwXyhQ](https://www.youtube.com/watch?v=zx7X9YwXyhQ) |


Motion 官方频道可继续翻更多公开片：在 YouTube 搜索 `Motion Creative Analytics`。

### 8.2 可直接打开的产品示意图 / 图片


| 产品     | 说明                                              | 链接                                                                                                                                                                     |
| ------ | ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| VidMob | 体验页（多张 Analyze / 绩效示意图，无需登录）                    | [https://www.vidmob.com/experience-the-worlds-first-creative-marketing-platform](https://www.vidmob.com/experience-the-worlds-first-creative-marketing-platform)       |
| VidMob | 图片直链：Explore Performance                        | [https://www.vidmob.com/wp-content/uploads/2023/01/Explore-Performance.png](https://www.vidmob.com/wp-content/uploads/2023/01/Explore-Performance.png)                 |
| VidMob | 图片直链：Make Decisions in One Place                | [https://www.vidmob.com/wp-content/uploads/2023/01/Make-Decisions-in-One-Place.png](https://www.vidmob.com/wp-content/uploads/2023/01/Make-Decisions-in-One-Place.png) |
| VidMob | 图片直链：Optimize Ad Spend                          | [https://www.vidmob.com/wp-content/uploads/2023/01/Optimize-Ad-Spend.png](https://www.vidmob.com/wp-content/uploads/2023/01/Optimize-Ad-Spend.png)                     |
| VidMob | 图片直链：Analyze 模块示意                               | [https://www.vidmob.com/wp-content/uploads/2023/01/Analyze-300x257.png](https://www.vidmob.com/wp-content/uploads/2023/01/Analyze-300x257.png)                         |
| VidMob | WARC 白皮书 PDF（Creative Intelligence 概念与案例，可直接打开） | [https://vidmob.com/hubfs/Vidmob_May2024/Pdf/VidMob_WARC_Whitepaper.pdf](https://vidmob.com/hubfs/Vidmob_May2024/Pdf/VidMob_WARC_Whitepaper.pdf)                       |


### 8.3 可直接打开的公开产品 / 说明页（含文案与部分画面，无需账号）


| 产品        | 说明                                                         | 链接                                                                                                                                                                                                                                                 |
| --------- | ---------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| VidMob    | Creative Intelligence 能力页（Fatigue / Health Score 等）        | [https://vidmob.com/tech](https://vidmob.com/tech)                                                                                                                                                                                                 |
| VidMob    | CPG 场景 Insight 能力页                                         | [https://vidmob.com/cpg](https://vidmob.com/cpg)                                                                                                                                                                                                   |
| Motion    | 官网首页（视觉报表 / AI Tag 介绍与展示）                                  | [https://motionapp.com/](https://motionapp.com/)                                                                                                                                                                                                   |
| Motion    | AI Tagging 发布说明                                            | [https://motionapp.com/releases/introducing-ai-tagging](https://motionapp.com/releases/introducing-ai-tagging)                                                                                                                                     |
| Motion    | Getting Started 公开指南（Reports / Comparative / AI Tags 能力说明） | [https://getting-started.motionapp.com/](https://getting-started.motionapp.com/)                                                                                                                                                                   |
| Motion    | Top Hook 帮助文（含界面截图，一般可直接打开）                                | [https://help.motionapp.com/en/articles/8757708-see-your-top-video-hooks](https://help.motionapp.com/en/articles/8757708-see-your-top-video-hooks)                                                                                                 |
| Smartly   | Creative Predictive Potential 功能页                          | [https://www.smartly.io/product-features/creative-predictive-potential](https://www.smartly.io/product-features/creative-predictive-potential)                                                                                                     |
| Smartly   | Intelligence Suite 介绍页（页内若有嵌入视频可直接播）                       | [https://www.smartly.io/intelligence-suite](https://www.smartly.io/intelligence-suite)                                                                                                                                                             |
| Smartly   | Creative Insights 发布新闻稿                                    | [https://www.smartly.io/press/smartly-expands-ai-powered-intelligence-across-its-platform-with-new-creative-capabilities](https://www.smartly.io/press/smartly-expands-ai-powered-intelligence-across-its-platform-with-new-creative-capabilities) |
| Celtra    | 官网首页（含 Explainer Video，点开即可看）                              | [https://celtra.com/](https://celtra.com/)                                                                                                                                                                                                         |
| Celtra    | Creative Testing 指南                                        | [https://celtra.com/blog/the-complete-guide-to-creative-testing/](https://celtra.com/blog/the-complete-guide-to-creative-testing/)                                                                                                                 |
| Marpipe   | 多元测试说明                                                     | [https://www.marpipe.com/blog/multivariate-testing-the-new-secret-weapon-for-ad-agencies](https://www.marpipe.com/blog/multivariate-testing-the-new-secret-weapon-for-ad-agencies)                                                                 |
| Marpipe   | 视频 MVT 流程文（文内若嵌视频可直接播）                                     | [https://www.marpipe.com/blog/how-to-multivariate-test-video-on-marpipe](https://www.marpipe.com/blog/how-to-multivariate-test-video-on-marpipe)                                                                                                   |
| Improvado | Creative Analytics 工具对比长文（含各工具能力描述）                        | [https://improvado.io/blog/creative-analytics](https://improvado.io/blog/creative-analytics)                                                                                                                                                       |
| Authencio | Motion Review（视觉分析能力拆解）                                    | [https://www.authencio.com/blog/motion-guide-ad-creative-analytics-alternatives](https://www.authencio.com/blog/motion-guide-ad-creative-analytics-alternatives)                                                                                   |


### 8.4 说明：为什么少有「完整后台录屏」

竞品完整 Dashboard 多数藏在登录后或销售 Demo 里；公开可看的主要是：

1. **官方 YouTube 短演示 / 功能讲解**（最推荐）
2. **官网营销页示意图 + 图片直链**
3. **帮助中心 / 博客截图**

若后续需要更完整的后台界面，只能走内部 Demo 或销售录屏，不适合放进「免注册资源」清单。  


---

## 9. 参考

- `Creative-Hub-竞品列表.md`
- **Insight Dashboard UI 稿（可本地打开）**：`Creative-Hub-Insight-Dashboard-UI稿.html`（基于第 5 节 A–K 分析角度）
- [Creative Hub V1.0 released](https://pacvue-enterprise.atlassian.net/wiki/spaces/APRN/pages/1411383904/2026-04-14+Creative+Hub+V1.0+released)
- [Insight - Creative Hub Analysis (PACID-6345)](https://pacvue-enterprise.atlassian.net/browse/PACID-6345)
- [Creative Performance Analysis](https://pacvue-enterprise.atlassian.net/wiki/spaces/PRD/pages/475103692)
- [Creative Hub Dashboard](https://pacvue-enterprise.atlassian.net/wiki/spaces/PRD/pages/1590329376)

