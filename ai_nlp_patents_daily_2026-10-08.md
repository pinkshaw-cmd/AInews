# AI / NLP / 专利交叉领域日报

**日期**：2026-10-08（对应检索目标日期：2026-10-07）  
**报告文件**：`ai_nlp_patents_daily_2026-10-08.md`

---

## 1. 当日概览

本次检索以 **2026-10-07** 为“前一天”目标日期，重点在 arXiv（cs.IR / cs.CL / cs.AI / cs.CE）、ACL Anthology 等公开源中查找 AI、NLP 与专利（patent）交叉领域的新发布工作。

**核心发现**：
- **2026-10-07 当日，arXiv 的 cs.IR / cs.CL / cs.AI 等目录中没有出现标题或主题直接聚焦“专利”的新论文**。当日 cs.IR 的 27 条新条目主要覆盖生成式信息检索、推荐系统、RAG、金融文档 QA 等方向，与专利场景间接相关但不构成专利专门研究。
- 目前可验证的**最新专利专项预印本**为 **2026-10-01** 发布的 `arXiv:2610.01553`（From Rules to Neural Graphs: Scalable Structured Prediction for Patent Prior Art Search）。
- 为回应“精选 5–10 篇”的要求，本报告纳入：
  1. **3 篇 2026-10-01 至 2026-10-05 期间发布/公告的最近期专利相关工作**；
  2. **5 篇 2026 年内在 ACL/EMNLP/ECML PKDD 等顶会或 arXiv 上出现的、具有代表性的 AI/NLP+专利交叉论文**；
  3. **1 篇 2026-10-07 发布的法律文档检索工作**作为 IP/NLP 相关方向补充。

**当日主题关键词**：专利先前技术检索（prior art search）、专利起草/生成（patent drafting / claim generation）、专利分类（CPC/IPC classification）、专利嵌入/表示学习、法律/知识产权 NLP。

---

## 2. 检索来源与关键词记录

| 来源 | 检索方式 | 关键词 / 过滤条件 | 结果状态 |
|---|---|---|---|
| arXiv 列表页 | WebFetch | `cs.IR/recent`、`cs.CL/recent`、`cs.AI/recent` 及其 `new` 页面 | 2026-10-07 无专利专项论文；最近期为 2026-10-01 |
| arXiv 单篇 | WebFetch | `2610.01553`, `2610.07437`, `2608.21249`, `2608.21249`, `2605.24297`, `2605.10073`, `2605.04875`, `2601.23200`, `2510.05431`, `2607.10480`, `2508.10496` | 已核验 |
| ACL Anthology | WebSearch + WebFetch | `patent NLP ACL 2026`、`Reasoning for Hierarchical Text Classification Patents`、`PatentMind` | 已核验（2026 年 Findings） |
| 通用搜索 | WebSearch | `arXiv AI NLP patent October 7 2026`、`site:arxiv.org patent classification retrieval NLP 2026` | 用于定位候选论文 |

**未使用付费/受限数据库；未检测到 `GIIISP_AUTH_TOKEN`，因此未调用 Giiisp 接口，改用开放源。**

---

## 3. 论文要点卡片

### 3.1 最近期专利相关工作（2026-10-01 至 2026-10-05）

#### 论文 1：From Rules to Neural Graphs: Scalable Structured Prediction for Patent Prior Art Search

| 字段 | 内容 |
|---|---|
| **arXiv ID / 日期** | `arXiv:2610.01553v1` [cs.IR]，2026-10-01 发布 |
| **作者 / 机构** | Nikolai Zenovkin, Sebastian Björkqvist（IPRally） |
| **发表渠道** | ECML PKDD 2026（Applied Data Science track） |
| **核心问题** | 专利先前技术检索需处理数万 token 的长文档；现有神经检索通常截断输入，图检索虽可处理长文档但依赖脆弱的手工规则解析器。 |
| **主要方法** | 提出神经解析器（neural parser），将依存句法中的 **biaffine attention** 适配到专利文本，直接预测“发明图”（invention graph）。引入 **local biaffine attention**，把成对打分复杂度从 $O(n^2)$ 降到 $O(n \cdot w)$；局部与全局共享权重，可在短序列上训练、在 40,000+ token 文档上推理。通过从 100 万条规则解析文档蒸馏得到学生模型。 |
| **关键数据集** | 100 万条规则解析专利（训练）；5,000 条人工标注专利（内在评估）；5,000 条训练样本已公开；评估框架见 GitHub `iprally/invention_graph_eval`。 |
| **核心结果** | 在下游 Graph Transformer 检索系统中，神经图相比规则图：短查询引用召回提升 **0.5%**，完整文档查询提升 **1.1%**；推理成本为规则解析器的 **1/3**。 |
| **创新点** | 首次把滑动窗口 biaffine attention 从扁平 span 抽取扩展到长文档树/DAG 结构化预测；实现“学生超越老师”的蒸馏效果。 |
| **局限性** | 输出格式需与既有规则系统保持兼容，限制了替代方案探索；LLM 标注虽被讨论但未在本工作中大规模替代规则教师。 |

#### 论文 2：Benchmarking Patent Drafting from Inventor-Style Disclosures

| 字段 | 内容 |
|---|---|
| **arXiv ID / 日期** | `arXiv:2608.21249v1` [cs.CL]，2026-08-21 发布 |
| **作者 / 机构** | Lekang Jiang, Wenjun Sun, Stephan Goetz（University of Cambridge） |
| **发表渠道** | EMNLP 2026 |
| **核心问题** | 现有专利起草基准多使用已高度结构化或法律化的输入，而真实流程始于发明人撰写的非正式、去法律化披露材料。 |
| **主要方法** | 提出 **Dis2Pat** 数据集（从已授权专利经 LLM 改写得到伪披露文本，保留技术内容但去除专利法律风格）；提出 **Patent-MAF**，一个面向本地部署的多智能体专利起草框架（manager → drafter → polisher）。 |
| **关键数据集** | Dis2Pat：9,433 条样本（8,490 训练 / 943 测试），来自 Google Patents Public Dataset，每条含披露文本、附图、原始权利要求与说明书。原始专利平均 **11,207 tokens**，披露文本平均约 **1,196 tokens**。 |
| **核心结果** | Patent-MAF 在所有评估的开源模型上 consistently 更优，并与大型闭源模型性能相当；当前 LLM 在完整专利起草任务上仍存在明显局限。 |
| **创新点** | 首个面向“发明人披露 → 完整专利申请”端到端流程的基准；强调隐私约束下的本地多智能体方案。 |
| **局限性** | 披露文本为 LLM 生成的伪数据，可能与真实发明人披露存在风格差异；未做时间切分，主要评估条件生成能力。 |

#### 论文 3：A Study of Prior Case Retrieval Using Lexical, Semantic, and Rhetorical Role Information in Indian Legal Documents

| 字段 | 内容 |
|---|---|
| **arXiv ID / 日期** | `arXiv:2610.07437v1` [cs.IR]，2026-10-05 提交，2026-10-07 在 cs.IR 公告 |
| **作者 / 机构** | Sayed Ayaan Ahmed Sha 等 |
| **发表渠道** | arXiv 预印本 |
| **核心问题** | 印度法律裁判文书中的先前案例检索：需区分相关法律事实与单纯词汇相似， Statute 相似并不足以判定相关性。 |
| **主要方法** | 对比三种连续设计的检索系统；提出组合 rhetorical roles（Fact / Ratio / Precedent / Argument / Statute）的检索；引入 query-disjoint splitting 与 frozen validation fusion。 |
| **关键数据集** | IL PCR（Indian Legal Prior Case Retrieval）任务官方数据。 |
| **核心结果** | 最终四阶段流水线：Micro F1 **0.2549**，MRR **0.6081**，nDCG@10 **0.4187**；发现内部验证 MRR 高达 0.97 的重排序器在官方评估中 MRR 低至 0.14，揭示域内/官方评估鸿沟。 |
| **创新点** | 系统分析 rhetorical role、statute 相似度与 LLM 重排序在法律检索中的实际效用；提出避免泄漏的验证融合策略。 |
| **局限性** | 任务为法律案例检索，非专利先前技术检索；但方法对知识产权/法律 NLP 有迁移参考价值。 |

---

### 3.2 2026 年代表性 AI/NLP+专利交叉论文

#### 论文 4：Benchmarking Patent Embeddings: A Multi-Task Evaluation of 22 Models Across Retrieval, Classification, and Clustering

| 字段 | 内容 |
|---|---|
| **arXiv ID / 日期** | `arXiv:2605.24297v2` [cs.IR]，2026-05-22 发布 / 05-26 修订 |
| **作者 / 机构** | Amirhossein Yousefiramandi, Ciaran Cooney |
| **发表渠道** | arXiv 预印本 |
| **核心问题** | 专利嵌入模型是否存在“一招鲜”？单一专利领域的微调是否可迁移到其他技术领域？ |
| **主要方法** | 在 **22 个预训练嵌入模型**（22M–12B 参数）上，于检索、分类、聚类三项任务做对照实验；比较 4 种微调配方（R1–R4），并在 WIPO 辅助技术语料与外部 DAPFAM 语料上做跨领域验证。 |
| **关键数据集** | WIPO assistive technology：113,148 条专利，46,069 条引用查询；DAPFAM（外部跨领域测试）；分类/聚类基于 WIPO taxonomy。 |
| **核心结果** | 最优配方因任务而异：cross-sectional alignment（R3）对检索 nDCG@10 提升 **+7.1%**；combined-signal（R4）对分类 F1 提升 **+7.1**、对聚类 V-measure 提升 **+10.9**。单一领域微调显著损害跨领域检索（8 种模型-配方组合中 5 种下降）。IN-domain 与 OUT-of-domain 性能差距达 **55–65%**，BM25-dense 融合无法弥合。 |
| **创新点** | 首次大规模、多任务、跨领域系统评估专利嵌入；揭示任务特异性微调配方与跨领域泛化风险。 |
| **局限性** | 主要覆盖英文专利；超大规模 LLM 嵌入未完全纳入。 |

#### 论文 5：Heterogeneous Dependency Graph-Guided Attention for Patent Representation Learning（PHAGE）

| 字段 | 内容 |
|---|---|
| **arXiv ID / 日期** | `arXiv:2605.10073v3` [cs.CL]，2026-05-11 发布 / 08-31 修订 |
| **作者 / 机构** | Yongmin Yoo, Qiongkai Xu, Zhangkai Wu, Longbing Cao |
| **发表渠道** | arXiv 预印本 |
| **核心问题** | 预训练语言模型将专利权利要求视为扁平 token 序列，忽略权利要求间的层级/引用依赖。 |
| **主要方法** | **PHAGE**：构建区分“法律引用”与“技术关系”的异构权利要求图；通过 connectivity mask 与可学习 relation-aware bias 将 claim-level 拓扑投影到 token-level attention；采用双粒度对比目标（inter-patent taxonomy + intra-patent topology）。推理时移除图相关组件，仅标准 encoder 前向即可。 |
| **关键数据集** | 专利分类、检索、聚类标准数据集（具体名称未在摘要中详列，沿用该团队此前工作设置）。 |
| **核心结果** | 在分类、检索、聚类任务上 consistently 超过领域自适应与引用感知基线；intra-patent claim topology 比 inter-patent 引用图提供更强归纳偏置。 |
| **创新点** | 把 claim 异构依赖结构无损注入 Transformer attention，同时保持推理高效。 |
| **局限性** | 图构建依赖确定性规则管道；对非英文专利与多模态专利图未做扩展。 |

#### 论文 6：Anticipating Innovation Using Large Language Models（TechToken）

| 字段 | 内容 |
|---|---|
| **arXiv ID / 日期** | `arXiv:2605.04875v1` [cs.CL]，2026-05-06 发布 |
| **作者 / 机构** | Enrico Maria Fenoaltea, Filippo Santoro, Giordano De Marzo, Segun Taofeek Aroyehun, Andrea Tacchella |
| **发表渠道** | arXiv 预印本 |
| **核心问题** | 如何预测未来首次出现的技术组合（technological combinations）？该信号对创新政策与专利布局有重要意义。 |
| **主要方法** | 提出 **TechToken**：将 IPC 分类码作为特殊 token 加入语言模型词表，通过专利文本微调让模型“学习技术语言”；以 code embedding 的 context similarity 衡量技术间语言收敛度，用于预测未来组合。 |
| **关键数据集** | 全球专利文献及其 IPC 代码（用于构建技术共现网络与语言模型微调）。 |
| **核心结果** | 语言收敛信号可在新技术组合出现**数十年前**被检测；TechToken 在多个专利相关任务上超过现有 SOTA。 |
| **创新点** | 把分类代码作为“词汇”嵌入 LM，实现技术空间与语言空间的统一表示；为技术预测提供可解释信号。 |
| **局限性** | 长期预测的可操作性与噪声来源需进一步分析；对 CPC 等更细粒度分类体系的扩展未报告。 |

#### 论文 7：Large Language Models, Encoder Architectures and Hybrid Approaches for Patent Classification

| 字段 | 内容 |
|---|---|
| **arXiv ID / 日期** | `arXiv:2601.23200v2` [cs.CE]，2026-01-30 发布 / 08-05 修订 |
| **作者 / 机构** | Lorenzo Emer, Marco Lippi, Andrea Mina, Andrea Vandin |
| **发表渠道** | arXiv 预印本 |
| **核心问题** | 自动化 CPC 层级多标签专利分类：编码器与 LLM 各有什么优势？混合能否取长补短？ |
| **主要方法** | 在控制条件下比较专利专用编码器（task-adapted BERT-for-Patents）与开源本地 LLM（fine-tuned Qwen3.5-9B）；提出将编码器不确定性最高的样本路由给 LLM 的混合流水线。 |
| **关键数据集** | CPC 分类任务数据；EPO 专利用于外部验证。 |
| **核心结果** | 最佳编码器 **BERT-for-Patents 优于最佳 LLM Qwen3.5-9B**；编码器推理能耗低 **1–2 个数量级**。混合流水线在不确认样本上取得显著提升。错误在 CPC Section Y（交叉/语义宽泛类别）最突出，并对技术映射、国家/申请人排名等下游指标产生实质性影响。 |
| **创新点** | 提供编码器 vs. LLM 在专利分类上的全面对照，包括能效、层级性能与下游指标传播分析。 |
| **局限性** | 主要关注英文与 CPC；未充分探索更大规模闭源 LLM。 |

#### 论文 8：Self-Filtered Distillation with LLMs-generated Trust Indicators for Reliable Patent Classification（SFD）

| 字段 | 内容 |
|---|---|
| **arXiv ID / 日期** | `arXiv:2510.05431v4` [cs.CL]，2025-10-06 发布 / 2026-05-19 修订 |
| **作者 / 机构** | Yongmin Yoo, Xu Zhang, Longbing Cao |
| **发表渠道** | arXiv 预印本 |
| **核心问题** | 用 LLM 生成的 rationales 蒸馏小模型做专利分类时，rationales 中的逻辑错误、标签不匹配、taxonomy 错位会被学生模型无差别吸收。 |
| **主要方法** | **Self-Filtered Distillation（SFD）**：把 LLM rationales 视为“信任信号”而非 ground-truth。综合三种无监督信任指标：Self-Consistency、Class Entailment Alignment、LLM Agreement Scoring，形成统一信任分并动态调节每样本训练贡献。 |
| **关键数据集** | USPTO-2M：超过 200 万条美国专利。 |
| **核心结果** | 在 4 种学生架构上 Macro-F1 相对提升最高达 **38.7%**；信任分与专家判断的皮尔逊相关系数 **r = 0.685**。 |
| **创新点** | 首次在专利分类蒸馏中引入可解释、可审计的信任评分机制，实现“自过滤”而非后验纠错。 |
| **局限性** | 信任指标设计依赖 LLM 多次采样，计算成本高于普通蒸馏；对超大规模学生模型未做验证。 |

---

### 3.3 顶会论文补充

#### 论文 9：PatentMind: A Multi-Aspect Reasoning Graph for Patent Similarity Evaluation

| 字段 | 内容 |
|---|---|
| **来源 / 日期** | ACL 2026 Findings（2026-07，San Diego） |
| **作者 / 机构** | Yongmin Yoo, Qiongkai Xu, Longbing Cao |
| **核心问题** | 专利相似度评估需同时考虑技术特征、应用领域、权利要求范围等多维结构，现有方法难以捕捉。 |
| **主要方法** | **PatentMind**：通过 Multi-Aspect Reasoning Graph（MARG）把专利文档拆分为技术特征、应用领域、权利要求范围三个维度；维度级相似度经上下文感知的动态加权整合。 |
| **关键数据集** | PatentSimBench：500 对专家标注专利对。 |
| **核心结果** | 与专家标注的皮尔逊相关系数 **r = 0.938**，显著超过嵌入基线、专利专用模型与提示工程基线。 |
| **创新点** | 提供可解释的多维相似度评估框架，可用于先前技术检索与侵权风险分析。 |
| **局限性** | 标注规模 500 对，扩展至更大规模或更多技术领域需进一步验证。 |

#### 论文 10：Reasoning for Hierarchical Text Classification: The Case of Patents（RHC）

| 字段 | 内容 |
|---|---|
| **来源 / 日期** | ACL 2026 Findings（2026-07，San Diego） |
| **作者 / 机构** | Lekang Jiang, Wenjun Sun, Stefan Goetz（University of Cambridge） |
| **核心问题** | 自动化专利主题分类是最困难的层级文本分类（HTC）场景之一，现有方法输出扁平标签集，缺乏可解释性。 |
| **主要方法** | **RHC**：将 HTC 重新表述为逐步推理任务。两阶段训练：cold-start 阶段对齐 CoT 推理格式；RL 阶段增强多步推理能力。 |
| **关键数据集** | 专利 HTC 基准（具体名称沿用该团队此前设置）及通用 HTC 基准。 |
| **核心结果** | 相比监督微调基线，准确率和 Macro F1 提升约 **3%**；在通用 HTC 基准上也达到 SOTA。 |
| **创新点** | 将链式推理与强化学习引入层级专利分类，兼具可解释性与可扩展性。 |
| **局限性** | 专利标签空间庞大，推理链长度与计算成本随层级深度增加。 |

---

## 4. 横向数据对比

### 4.1 任务-方法-指标对照表

| 论文 | 任务 | 核心方法 | 数据集 | 关键指标 | 数值 |
|---|---|---|---|---|---|
| Zenovkin & Björkqvist, 2026 | 专利先前技术检索 | 局部 biaffine 神经图解析器 + Graph Transformer | 100万规则解析专利（训练）；5K 标注（评测） | 短查询引用召回提升 | **+0.5%** |
| Zenovkin & Björkqvist, 2026 | 专利先前技术检索 | 同上 | 同上 | 完整文档引用召回提升 | **+1.1%** |
| Zenovkin & Björkqvist, 2026 | 神经图解析 | 局部 biaffine vs. 规则解析器 | 同上 | 推理成本降低 | **3×** |
| Jiang et al., 2026 (Dis2Pat) | 披露 → 完整专利申请 | Patent-MAF 多智能体框架 | Dis2Pat：9,433 条（8,490 / 943） | 原始专利平均 token 数 | **11,207** |
| Jiang et al., 2026 (Dis2Pat) | 披露 → 完整专利申请 | Patent-MAF 多智能体框架 | Dis2Pat | 披露文本平均 token 数 | **~1,196** |
| Sha et al., 2026 | 法律先前案例检索 | Rhetorical role + 语义 + 词法融合 | IL PCR | Micro F1 / MRR / nDCG@10 | **0.2549 / 0.6081 / 0.4187** |
| Yousefiramandi & Cooney, 2026 | 专利检索 | Cross-sectional alignment（R3） | WIPO assistive tech（113K 专利，46K 查询） | nDCG@10 提升 | **+7.1%** |
| Yousefiramandi & Cooney, 2026 | 专利分类 | Combined-signal（R4） | WIPO taxonomy | F1 提升 | **+7.1** |
| Yousefiramandi & Cooney, 2026 | 专利聚类 | Combined-signal（R4） | WIPO taxonomy | V-measure 提升 | **+10.9** |
| Yousefiramandi & Cooney, 2026 | 跨领域检索 | 单一领域微调后外推 | WIPO → DAPFAM | IN/OUT-of-domain 差距 | **55–65%** |
| Yoo et al., 2026 (PHAGE) | 专利分类/检索/聚类 | 异构 claim 图引导 attention | 标准专利基准 | 在三个任务 consistently 优于基线 | 定性/无单一数值 |
| Fenoaltea et al., 2026 | 技术组合预测 | TechToken（IPC 作为 token） | 全球专利 + IPC | 预测首次组合提前量 | **数十年** |
| Emer et al., 2026 | CPC 多标签分类 | BERT-for-Patents vs. Qwen3.5-9B | CPC 任务 + EPO 外部验证 | 编码器 vs. LLM 能耗差距 | **1–2 个数量级** |
| Yoo et al., 2026 (SFD) | 专利分类 | Self-Filtered Distillation | USPTO-2M（>2M 专利） | Macro-F1 相对提升 | **最高 38.7%** |
| Yoo et al., 2026 (SFD) | 分类可信度 | 信任分 vs. 专家判断 | USPTO-2M 子集 | 皮尔逊 r | **0.685** |
| Yoo et al., 2026 (PatentMind) | 专利相似度评估 | Multi-Aspect Reasoning Graph | PatentSimBench（500 对） | 与专家标注皮尔逊 r | **0.938** |
| Jiang et al., 2026 (RHC) | 层级专利分类 | CoT + RL 两阶段推理 | 专利 HTC 基准 | 准确率 / Macro F1 提升 | **约 +3%** |

### 4.2 数据分析解读

1. **图结构 vs. 长文本**：Zenovkin & Björkqvist（2026）与 Yoo et al.（PHAGE，2026）共同说明，把专利的层级/引用结构显式建模（发明图、claim 依赖图）比单纯截断长文本或扁平编码更有效。两者都在推理阶段做了工程优化：前者用局部 biaffine 把解析成本降 3 倍，后者在推理时去掉图组件以保持标准 encoder 前向。
2. **任务特异性微调**：Yousefiramandi & Cooney（2026）证明不存在“万能”专利嵌入微调配方；检索、分类、聚类分别对 cross-sectional alignment 与 combined-signal 敏感，提示从业者按下游任务选择训练目标。
3. **编码器 vs. LLM 的能效权衡**：Emer et al.（2026）与 Jiang et al.（Dis2Pat，2026）分别说明：在分类任务上，专用编码器在准确率和能耗上双双优于本地 LLM；但在需要长文本生成与多智能体协调的披露 → 专利起草任务中，LLM/多智能体仍是当前主流方案。
4. **跨领域泛化瓶颈**：Yousefiramandi & Cooney（2026）的 55–65% IN/OUT gap 与 Sha et al.（2026）观察到的内部 MRR 0.97 但官方 MRR 0.14 共同揭示：法律/专利领域的域内-域外鸿沟与评估泄漏风险是核心挑战。
5. **可解释性趋势**：SFD（r=0.685）、PatentMind（r=0.938）、RHC（自然语言推理链）显示，2026 年专利 NLP 研究越来越重视可解释、可审计的预测，这对知识产权决策至关重要。

---

## 5. 趋势观察与值得后续追踪的方向

### 5.1 主要趋势

1. **结构化表示成为专利长文档处理的核心**：发明图、claim 依赖图、多维度推理图等方法正在替代简单的文本截断，以保留专利的法律与技术结构。
2. **生成式专利起草从“单任务”走向“端到端工作流”**：Dis2Pat / Patent-MAF 代表了从“权利要求生成”或“说明书生成”单任务，转向从发明人披露到完整专利申请的端到端、多智能体、本地部署方案。
3. **LLM 与专用编码器的混合架构兴起**：在分类等判别任务上，编码器仍具能效优势；在生成与复杂推理任务上，LLM/多智能体不可或缺。路由机制（router）成为连接两者的关键。
4. **可解释性与可信度受到重视**：信任分、推理链、多维相似度等机制不仅提升性能，更满足知识产权场景对可审计决策的需求。
5. **跨领域/跨语言泛化仍是开放问题**：单一领域微调、英语中心数据集、CPC/IPC 差异等问题尚未解决。

### 5.2 值得后续追踪的方向

- **2026-10-07 当日未出现的新论文**：未来数日应继续追踪 arXiv `cs.IR`/`cs.CL`/`cs.AI` 的 `new` 页面，以及 ECML PKDD、EMNLP 2026 的后续预印本发布。
- **Graph Transformer 专利检索的工业落地**：Zenovkin & Björkqvist（IPRally）与 Daniell et al.（PatentSemTech 2025）的图 Transformer 路线是否会在专利局或企业 IP 部门形成产品化方案。
- **多智能体专利起草的评估标准**：Dis2Pat 引入了端到端基准，但如何量化法律风险、可专利性、侵权规避等仍缺乏共识指标。
- **跨语言/跨法域专利 NLP**：当前工作以英文/USPTO/EPO 为主，中文、日文、韩文专利及不同法域（如中国 CNIPA、日本 JPO）的 NLP 工具相对空白。
- **LLM 在知识产权中的可信度与版权争议**：随着生成式专利起草的发展，LLM 生成内容的可专利性、训练数据版权、以及 AI 作为发明人/作者的法律地位将持续成为交叉研究热点。

---

## 6. 2026-10-07 当日未命中说明

- **arXiv cs.IR 2026-10-07 新条目**：共 27 条，主题涵盖生成式检索、推荐系统、RAG、金融 QA、法律案例检索等，无标题或摘要明确聚焦“专利”的论文。
- **arXiv cs.CL / cs.AI 2026-10-07**：通过 WebSearch 与列表页交叉核验，未检索到与专利直接相关的新预印本（受部分页面缓存/时区显示差异影响，以 cs.IR 当日列表为准）。
- **ACL Anthology**：无 2026-10-07 当日发布记录；2026 年已收录的专利相关论文已纳入本报告第 3.3 节。
- **结论**：若严格限定“2026-10-07 当日发布的 AI/NLP+专利论文”，则**未检索到符合要求的新论文**。本报告未编造数据，而是提供了：
  1. 当日最接近的专利相关工作（2026-10-01 发布）；
  2. 当日相关的法律/知识产权 NLP 工作（2026-10-05 提交，10-07 公告）；
  3. 2026 年内在该交叉领域具有代表性的 8 篇论文及 2 篇 ACL Findings 论文。

---

## 7. 参考链接

- arXiv:2610.01553 — https://arxiv.org/abs/2610.01553
- arXiv:2608.21249 — https://arxiv.org/abs/2608.21249
- arXiv:2610.07437 — https://arxiv.org/abs/2610.07437
- arXiv:2605.24297 — https://arxiv.org/abs/2605.24297
- arXiv:2605.10073 — https://arxiv.org/abs/2605.10073
- arXiv:2605.04875 — https://arxiv.org/abs/2605.04875
- arXiv:2601.23200 — https://arxiv.org/abs/2601.23200
- arXiv:2510.05431 — https://arxiv.org/abs/2510.05431
- arXiv:2607.10480 — https://arxiv.org/abs/2607.10480
- ACL 2026 Findings — PatentMind: https://aclanthology.org/2026.findings-acl.735/
- ACL 2026 Findings — RHC: https://aclanthology.org/2026.findings-acl.541/
