# Creative Hub：AI 生成场景与竞品实现

> 更新日期：2026-07-14  
> 视角：从 **Gen AI 生产** 横切竞品（「出什么素材、怎么出」），与报表 / Insight 闭环互补。  
> 相关文档：`Creative-Hub-竞品列表.md` · `Creative-Hub-报表与Insight能力梳理.md`（§5.6 闭环场景） · `PRD/Creative-Hub-AI-Generator-PRD.md`（产品 PRD 场景分类）

---

## 1. 场景总览

| # | 场景族 | 一句话 | 代表竞品 |
|---|--------|--------|----------|
| 1 | 从零生成 | URL / PDP / Prompt / 产品图 → 成片 | Creatify、Pencil、AdCreative.ai、Rocketium |
| 2 | 规格 / 版位适配 | 母版 → 多尺寸、多 Ad Type、多语言 | Bannerflow、Creatopy、Celtra、Smartly、Rocketium |
| 3 | 本地化与市场版本 | 同概念跨国家 / 语言规模化 | Storyteq、Smartly、Celtra |
| 4 | 零售 / 品牌合规生成 | 按零售商 / 品牌规范「合规后出片」 | Rocketium、Microsoft Retail Creative Studio、Amazon Creative X |
| 5 | 批量变体 / DCO / 测试矩阵 | 大批量变体或元件组合供测试 | Creatify、Smartly、Celtra、Marpipe、Hunch |
| 6 | 上线前打分筛选 | 先生成再按预测分挑 | Pencil、AdCreative.ai、Smartly、Celtra |
| 7 | 既有素材优化 / 修复 | 不重做，改清晰度 / 裁切 / 拒审点 | Rocketium（编辑层）、平台内编辑器、CH 质量检测方向 |
| 8 | 胜者驱动再生成 / 疲劳刷新 | 用胜出风格或衰减触发再出一批 | Omneky、Celtra、Smartly（Insight→再生产） |
| 9 | 季节 / 大促套件 | 节庆、促销主题批量样例 | Rocketium、Celtra、Bannerflow、Storyteq |
| 10 | Agent + 人工审校流水线 | AI 批量出稿 → 人工 / 品牌审核 → 交付 | Rocketium（最典型）、Celtra（治理偏自助） |

### 竞品站位速览

| 族 | 代表 | Gen AI 重心 |
|----|------|-------------|
| 零售合规生产 | Rocketium、Microsoft Retail Creative Studio、Amazon Creative X | 按 RMN / 零售商规范批量出 PDP / Banner，合规优先 |
| 高产效果广告 | Creatify、Pencil、AdCreative.ai、Omneky | 从零 / URL / 产品快速出图视频 + 预测分 |
| 企业创意自动化 | Celtra、Smartly、Bannerflow、Storyteq | 母版扩量、本地化、DCO、品牌治理 |
| Feed 动态 | Hunch | 商品目录驱动动态创意 |
| 测试导向变体 | Marpipe | 结构化元件组合，服务 A/B，非纯 GenAI 出片 |
| 弱 GenAI | Walmart Connect Creative Hub 等 | 上传 / 模板为主 |

**对 Creative Hub**：多数竞品停在「会出片」；CH 机会是嵌进 **跨 RMN 资产 + 绩效**（场景 7/8、2/4、5/9 与 Insight→更新 Creative / 创建 Campaign 最贴）。纯「URL 出一条视频」（场景 1）竞争最红海，不宜当主叙事。

---

## 2. 各场景：竞品如何实现

### 场景 1 — 从零生成

**实现模式**：输入商品信息 → 抽取卖点 / 素材 → 脚本或构图 → 渲染成片。

| 产品 | 实现方式 |
|------|----------|
| **Creatify** | Paste 商品 URL → 抓取详情与媒体 → AI 写脚本 → 选 Avatar / 模板 → 预览 → Render；另有 Aurora（单图说话人）、Product Video、Image Ads 等入口；支持 API（link → preview → render） |
| **Pencil** | Prompt / 品牌资产 / 上传参考 → GenAI 出静态或视频广告；工作区连接广告账户后接预测分（见场景 6） |
| **AdCreative.ai** | 品牌套件 + 产品信息 → 高产量图文广告模板生成 |
| **Rocketium** | Brief / 目标结果进工作室 → AI 从 brief 出净新图文视频，同时过品牌与平台规则（更偏「受管生产」而非自助 Prompt） |
| **Amazon Creative X 等原生** | 生态内商品 / ASIN 上下文原生生成，规格已锁死在平台 |

**要点**：输入多为 URL / Feed / Brief，少依赖用户写复杂 Prompt；输出偏「可投广告单元」，不是通用设计工具。

---

### 场景 2 — 规格 / 版位适配

**实现模式**：锁定母版（layout / 品牌锁区）→ 规则或 AI 扩成多尺寸 / 多格式文件。

| 产品 | 实现方式 |
|------|----------|
| **Bannerflow** | 母版驱动 Display / Social / DOOH 等；一处改、多端同步；AI Studio 辅助跨格式产出 |
| **Creatopy** | 模板设计 + 一键多尺寸导出（格式跨平台，非账户级资产管理） |
| **Celtra** | 模板锁定字体 / 色板 / safe zone → 市场或投放团队填变体 → 导出 100+ 渠道规格 |
| **Smartly** | 导入 AE / PS / Figma / 自有模板 → AI Studio / 自动化按渠道适配；与投放模板联动 |
| **Rocketium** | Adaptation：从已批准 master 产出全尺寸、格式、本地化版本，并内嵌零售规格检查 |
| **Creative Hub（现状）** | AI Optimizer：尺寸 / 语言变体（Pixel Variants 方向），偏适配而非从零出片 |

**要点**：核心是「母版 + 约束」，不是每尺寸重画；合规类竞品把 **平台尺寸 / 字图比 / 安全区** 编进导出规则。

---

### 场景 3 — 本地化与市场版本

**实现模式**：同一创意概念 × 市场 / 语言 / 法规差异 → 批量版本管理。

| 产品 | 实现方式 |
|------|----------|
| **Storyteq** | 模板化 + 跨市场版本库；语言 / 市场为结构化元数据；强调规模化本地化 |
| **Smartly** | DCO / 自动化按 region、language、demographic 实时本地化；Feed 字段驱动文案与价格 |
| **Celtra** | 全球母版 + 本地团队在治理护栏内改文案 / 元素；品牌不漂移 |
| **Rocketium** | Adaptation / Production 流水线中带多市场版本与人工 QA |

**要点**：本地化 = 版本治理 + 数据字段替换 +（可选）GenAI 译写，企业 CMP 强于纯 GenAI 工具。

---

### 场景 4 — 零售 / 品牌合规生成

**实现模式**：规则前置于生成（或生成中校验），而不是成片后再审。

| 产品 | 实现方式 |
|------|----------|
| **Rocketium** | 将 Amazon / Walmart / Target 等技术规格（尺寸、分辨率、字图比、logo safe zone、品类免责声明等）编码进生产；AI Agent 做机械合规校验 → 专家 QA → 客户终审；自称「合规默认产出」而非事后抽检 |
| **Microsoft Retail Media Creative Studio** | 平台内 GenAI Banner，对齐该零售媒体品牌 / 版位规范 |
| **Amazon Creative / Ads 创意工具** | 生态内生成，规格原生合规，无法跨零售商复用工作区 |
| **Celtra** | 强在 **品牌治理**（锁模板、色板、字体）；弱在 Amazon / Walmart 零售商专属合规 |
| **Walmart Connect Creative Hub** | 偏自助创建 / 上传 / 审核列表，GenAI 弱，合规靠审核流程 |

**要点**：零售合规 ≠ 品牌治理。CH 若做场景 4，需同时覆盖 **RMN 规格规则库** 与品牌约束，并贴近「检测 → 修复 / 再生」而非只做上传审核。

---

### 场景 5 — 批量变体 / DCO / 测试矩阵

**实现模式**：三条技术路线——组合矩阵、模板随机/规则变体、Feed 动态组装。

| 产品 | 实现方式 |
|------|----------|
| **Creatify Batch Mode** | 同一 URL × 多脚本 × 多视觉模板 × 多 Avatar → 一次批量 Render，供 A/B |
| **Smartly DCO** | 模板 + 商品 Feed / 数据源 → 按受众 / 报价 / 地域规则实时组广告；逻辑由用户设定护栏 |
| **Celtra** | 模块化模板大批量变体；可接 live data（价、库存等）动态创意 |
| **Marpipe** | Hook / Body / CTA 等元件结构化组合，服务多元测试归因（生成服务测试，非 GenAI 炫技） |
| **Hunch** | Catalog / 商品 Feed 驱动社媒 DPA 类动态创意 |
| **Rocketium** | 单次请求可要求数百变体（offer / 标题 / 角度），仍走 Agent + 专家审校 |

**要点**：测试型（Marpipe）强调「元件可归因」；规模型（Smartly / Celtra）强调「模板 × 数据」；CH 多变体可介于：基于胜出 Tag / Asset Group 约束生成，并进入 Create Campaign。

---

### 场景 6 — 上线前打分筛选

**实现模式**：生成一篮素材 → 模型打分 → 优先上线高分 / 先改再投。

| 产品 | 实现方式 |
|------|----------|
| **Pencil** | Media Performance Score（0–100）：相对账户历史广告的 **CTR 分位**；需连接 Meta 账户且约有 200–300 条历史广告；用语义 embedding 找相似历史创意再预测；分数挂在 creative work item 上 |
| **AdCreative.ai** | 转化 / 表现评分，偏 SMB 轻量预测，深度弱于账户级个性化模型 |
| **Smartly Creative Predictive Potential** | 上线前用 CV + 注意力 / 情绪 / 互动模型；heatmap、attention、decay；给出改视觉 / 文案 / 节奏的建议 |
| **Celtra** | 生命周期中的预测打分 + 元素级优化建议，与生产同平台 |

**要点**：强实现都依赖 **历史绩效样本**（账户或库级）；CH 目前弱在预测层，可先规则筛选（合规通过 + Tag 胜出约束），中长期再上预测分。

---

### 场景 7 — 既有素材优化 / 修复

**实现模式**：检出问题维度 → 局部改图 / 改文 / 重裁，而非整条重生。

| 产品 | 实现方式 |
|------|----------|
| **Rocketium** | 交付后客户可自助小改；生产侧把规格违规在生成时挡掉；非「投放后质量看板 → 一键修」产品形态 |
| **平台原生编辑器** | Microsoft / Amazon / Meta 等：平台内改 Banner / 资产，规则绑定本生态 |
| **Celtra / Bannerflow** | 母版改一处同步多版本；偏运营更新，非「质量检测驱动」 |
| **Creative Hub（方向）** | 质量 / 合规检出 → AI 优化 → **更新 Creative**（用户主场景 1 / 补充场景 10） |

**要点**：竞品少有「绩效或质量 Insight 驱动的局部修复」闭环；这是 CH 相对独特的产品切口。

---

### 场景 8 — 胜者驱动再生成 / 疲劳刷新

**实现模式**：Insight（谁赢 / 谁疲）→ 约束条件（风格、元件、差异化）→ 再生成 → 替换或新 Campaign。

| 产品 | 实现方式 |
|------|----------|
| **Omneky** | AI 多格式生成与多渠道表现分析同工作流，强调效果营销迭代 |
| **Celtra** | 绩效情报「塑造 AI 生成什么」；元素级建议回流生产；Creative Services 可按洞察给新选项 |
| **Smartly** | Creative Insights（主题 / AI 摘要）+ 自动化再生产；Predictive + 投放一体缩短闭环 |
| **VidMob / Motion** | 强在诊断与 Tag / 元素洞察，GenAI 规模出片非主业；常「建议外包或他处生产」 |
| **Pencil / Creatify** | 强生成、弱「疲劳检测自动触发」；再生成多为用户手动开新任务 |

**要点**：真正闭环 = Insight 产品 × GenAI 产品一体，或明确 API / 工作流衔接。CH 可用 Asset Group / Tag / 跨平台落差触发（与用户主场景 2/3、补充 5/7/8/9 对齐）。

---

### 场景 9 — 季节 / 大促套件

**实现模式**：促销主题 brief 或活动日历 → 批量样例 / 全 SKU 套件 → 提前锁定渠道规格。

| 产品 | 实现方式 |
|------|----------|
| **Rocketium** | 零售大促 / sale events 批量产能是核心叙事（含 Amazon Fashion 等案例：活动频次受产能约束 → AI Studio 扩量） |
| **Celtra / Bannerflow / Storyteq** | Campaign toolkit / 母版换肤：主题色、主视觉、文案槽位批量换节庆 / promo |
| **Creatify / Pencil** | 用户按主题 Prompt 或 URL 批量出片，日历与库存联动弱 |

**要点**：企业 CMP / 零售生产靠「活动母版 + 批量适配」；CH 可用「大促前 2–3 周」时间触发 + AI 样例 → 提前 Create Campaign（用户主场景 4）。

---

### 场景 10 — Agent + 人工审校流水线

**实现模式**：Brief 入口 → AI Agent 执行机械步骤 → 人类专家审判断依赖项 → 客户终审 / 自助小改。

| 产品 | 实现方式 |
|------|----------|
| **Rocketium** | 最完整：邮件 / Slack / Teams / Web 进 brief → Brand Intelligence + AI agents 执行 → Design / Quality Experts 审校 → 客户批准与自助编辑；宣称「无需 Prompt 工程」 |
| **Celtra** | 偏自助 SaaS + 品牌治理；可选 Creative Services；推动 brand.json 等「机器可读品牌」给 Agent 用 |
| **Smartly** | AI Studio 自助规模化生产 + 投放一体；人工审校弱于 Rocketium 托管模式 |
| **纯 GenAI（Creatify / AdCreative 等）** | 用户自助生成与预览，人工审校在客户侧，不在平台流程内强制 |

**要点**：托管流水线适合「拒审成本高、规格复杂」的零售媒体；自助流水线适合速度与社媒测试。CH 可折中：自助生成 + 平台规格自动校验 +（可选）人工复核节点。

---

## 3. 实现骨架对照（横向）

| 实现骨架 | 典型竞品 | 适用场景 |
|----------|----------|----------|
| URL / Feed → 抓取 → 成片 | Creatify、Hunch | 1、5 |
| Brief → Agent → 人工 QA → 交付 | Rocketium | 1、2、4、9、10 |
| 母版锁定 → 扩尺寸 / 本地化 / DCO | Celtra、Smartly、Bannerflow、Storyteq | 2、3、5、9 |
| 生成 → 账户级预测分 → 筛选 | Pencil、Smartly、Celtra | 6 |
| 元件组合矩阵 → 测试归因 | Marpipe | 5、（Insight 侧） |
| 平台内规范生成 | Amazon、Microsoft、Meta、Google | 1、4（单生态） |
| Insight 结论 → 再生 / 刷新 | Omneky、Celtra、Smartly | 7、8 |

---

## 4. 与 Creative Hub 已定闭环的映射

| Insight / 产品闭环（报表文档 §5.6） | 主要落在 Gen AI 场景 |
|------------------------------------|----------------------|
| 1 质量检测 → 更新 Creative | 7、4、10 |
| 2 Asset Group 跨平台缺口 → 创建 Campaign | 2、4、5 |
| 3 高潜力多变体 → 创建 Campaign | 5、6、8 |
| 4 大促预热样例 → 提前创建 Campaign | 9、5、1 |
| 5 疲劳刷新 / 7 败者替换 | 8、7 |
| 8 胜出 Tag 扩量 / 9 同质化破局 | 5、8 |
| 10 合规拒审修复 | 4、7 |

---

## 5. 结论（给产品取舍）

1. **不要主打红海「纯从零 Prompt 出片」**：Creatify / Pencil / AdCreative 已占位；CH 应用资产库与跨平台绩效喂生成。  
2. **优先可产品化的实现**：规格适配（2）+ 合规修复（4/7）+ 绩效触发变体（5/8）+ 大促套件（9）。  
3. **预测分（6）与 Agent 托管（10）可分期**：先规则 / 合规硬门槛，再账户级预测与审校深度。  
4. **与 Insight 文档分工**：本文管「怎么生成」；`Creative-Hub-报表与Insight能力梳理.md` 管「何时触发、投完如何验证」。

---

## 备注

- 实现描述基于公开产品页、帮助中心与行业对比文，属相对判断，细节随版本变化。  
- Gen AI / Report / 跨平台 / Tag 强弱总表见 `Creative-Hub-竞品列表.md`。
