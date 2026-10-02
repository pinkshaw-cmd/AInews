# AI · NLP · 专利交叉领域日报

**日期：** 2026-10-02（对应检索窗口：2026-10-01 至 2026-10-02）
**编制说明：** 本报告优先覆盖 2026-10-01（过去一天）新发布的工作，同时纳入 2026-10-02 当日及 9 月下旬引起关注的 AI/NLP 与专利交叉领域重要论文。所有数据均来自 arXiv 公开元数据与论文摘要，未编造指标或结果。

---

## 一、当日概览

| 维度 | 情况 |
|---|---|
| **检索窗口** | 2026-10-01 至 2026-10-02 |
| **检索来源** | arXiv RSS (cs.CL / cs.IR / cs.AI)、arXiv API、OpenAlex API、Semantic Scholar API |
| **检索关键词** | `patent`, `prior art`, `patent classification`, `patent drafting`, `intellectual property`, `LLM patent`, `synthetic patent data`, `patent retrieval`, `legal NLP`, `TRIZ`, `Office Action` |
| **专利直接相关新论文（10-01）** | **1 篇**（arXiv:2610.01553） |
| **AI/NLP 前沿新论文（10-02）** | **3 篇**入选（cs.CL 当日更新中筛选） |
| **近期引起关注的专利交叉工作** | **6 篇**（9 月—8 月，含 NeurIPS/ICML Workshop 接收） |
| **总计** | **10 篇** |

> **关键发现：** 2026-10-01 当日，arXiv 各主要频道中仅出现 **1 篇**与专利直接交叉的新工作（`From Rules to Neural Graphs`）。专利文本的 arXiv 更新密度显著低于通用 NLP/AI，说明该领域仍以会议周期（如 ACL、EMNLP、NeurIPS 应用轨）和工业界内部迭代为主。10-02 cs.CL 频道更新活跃，但专利主题占比同样偏低。

---

## 二、逐篇要点卡片

### 1. From Rules to Neural Graphs: Scalable Structured Prediction for Patent Prior Art Search

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2610.01553 |
| **发布日期** | **2026-10-01** ✅ |
| **作者/机构** | Nikolai Zenovkin, Sebastian Björkqvist / IPRally Technologies Oy, Helsinki, Finland |
| **会议状态** | ECML PKDD 2026 (Applied Data Science track) 已接收 |
| **核心问题** | 专利文档通常超过数万 token，现有神经检索方法因截断输入而受限；基于图的结构化检索依赖脆弱的规则解析器，难以扩展。 |
| **主要方法** | 提出 **neural parser**：将 biaffine attention（源自依赖解析）适配到专利文本，直接预测 invention graph。引入 **local biaffine attention**，将 token  pairwise 复杂度从 O(n²) 降至 O(n·w)；局部与全局评分共享权重，可在短序列上训练、直接部署到 40,000+ token 的长文档。模型从 100 万条规则解析文档蒸馏得到。 |
| **关键数据集** | 100 万条规则解析专利文档（蒸馏训练集）；下游 Graph Transformer 检索系统测试集 |
| **核心结果** | • 推理成本降至教师模型的 **1/3**<br>• 短查询 citation recall 提升 **0.5%**<br>• 完整文档 citation recall 提升 **1.1%** |
| **创新点** | 首次将局部 biaffine attention 扩展到超长专利文档的图解析，解决规则解析器的 brittleness 问题，且无需重新训练即可处理 40k+ token。 |
| **局限性** | 摘要未明确报告跨技术领域（IPC/CPC）泛化结果；蒸馏依赖大量规则解析数据，规则解析器本身的偏差可能传递到学生模型；未与最新的长上下文 LLM 检索做直接对比。 |

---

### 2. LogicTree-RAG: Logic Tree-guided Retrieval-Augmented Generation for Long-form Patent Drafting

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2609.30943 |
| **发布日期** | 2026-09-25 |
| **作者/机构** | Jiaqi Zhu, Naili Xing, Hexiang Pan, Haotian Gao, Jianwei Yin, Xiaokui Xiao, Beng Chin Ooi |
| **会议状态** | **NeurIPS 2026** 已接收 |
| **核心问题** | 长技术文本（如专利）生成需要全局一致的逻辑结构和技术忠实性，现有方法多为局部段落生成或依赖手工大纲，难以规模化。 |
| **主要方法** | **LogicTree-RAG**：以层级逻辑树作为全局组织骨架，每个节点代表技术元素，通过证据引导的递归生成构建；混合遍历机制将逻辑树映射到专利各章节，实现可控、均衡的长文本生成。 |
| **关键数据集** | 专利撰写数据集（具体规模见原文 §4.1） |
| **核心结果** | 与强 LLM 基线相比，content quality 与 language conformity 提升 **33%**，同时保持高 token 效率，生成结构更长。 |
| **创新点** | 将"逻辑树"作为 RAG 的组织核心，而非传统的平面检索块拼接；支持无专家先验的自动化专利长文起草。 |
| **局限性** | 摘要未披露逻辑树构建失败率或极端复杂专利（如生物技术）上的表现；人工评估占比与 LLM-as-a-Judge 的潜在偏差待进一步验证。 |

---

### 3. The Perplexity Trap: When Patent Law Makes Human Writing Look Like AI

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2607.13044 |
| **发布日期** | 2026-06-15 |
| **作者/机构** | Anubhab Banerjee |
| **会议状态** | ICML 2026 Workshop on AI4Law |
| **核心问题** | EPO 2026 指南要求申请人对 LLM 辅助内容负责，需筛查 AI 生成的专利文本；但专利法 Article 84 要求权利要求清晰简洁，迫使人类撰写趋近低困惑度、低 burstiness 的流形，与 LLM 输出重叠。 |
| **主要方法** | 在消费级 GPU（~8 GB VRAM）硬件约束下，对 500 份已授权 EPO H04 电信专利 vs. 500 份 LLM 生成文本（5 种 prompt 策略）进行零样本检测基准测试；并提出七特征语言复杂度逻辑回归分类器。 |
| **关键数据集** | 500 份已授权 EPO 专利（H04 类）+ 500 份 LLM 生成对应文本；跨 IPC 复制测试：A61K、C07D、F03D |
| **核心结果** | • **Binoculars** FPR：**78.3%**<br>• **Fast-DetectGPT** FPR：**61.3%**<br>• **DetectGPT** FPR：**80.5%**<br>• 跨 IPC 平均 FPR：**84.6%**<br>• 七特征逻辑回归：**74.0%** 准确率，**28.1%** FPR（比困惑度基线提升 13 pp） |
| **创新点** | 首次在消费级硬件和真实 EPO 专利上系统验证"困惑度陷阱"：法律文体约束本身导致 AI 检测器失效；提出不依赖 likelihood 的轻量级语言学特征方案。 |
| **局限性** | 仅测试英语 EPO 专利；七特征模型虽降低 FPR，但 28.1% 仍不足以用于自动化筛查；未涉及多语言专利局（如 JPO、CNIPA）场景。 |

---

### 4. When Does Synthetic Patent Data Help? Volume–Fidelity Trade-offs in Low-Resource Multi-Label Classification

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2605.24296 |
| **发布日期** | 2026-05-22 (v2: 2026-05-26) |
| **作者/机构** | Amirhossein Yousefiramandi, Ciaran Cooney / Clarivate, Intellectual Property, Barcelona |
| **核心问题** | LLM 生成的合成专利数据何时真正帮助多标签专利分类？既有研究未充分控制"样本量增加本身带来提升"的混杂因素。 |
| **主要方法** | 系统对比 6 个开源 LLM（3.8B–12B）、两种生成策略（label-conditioned 全合成 vs. 改写）、三类分类器；在 64 个 WIPO 辅助技术标签的四档真实数据比例下展开实验。 |
| **关键数据集** | WIPO 辅助技术专利数据（64 标签）；真实数据比例：极低、低、1:1、1:10 |
| **核心结果** | • BERT-for-Patents micro F1 从 0.120 → 0.702（合成增强后），但**重复采样对照**也能达到 **0.678**；真实增益仅 **+0.024**<br>• 对比最佳基线（focal loss reweighting）：**+0.219**<br>• 极低数据 regime 下，MMD 与性能相关性 **r = +0.95**；1:10 regime 下相关性反转至 **r = -0.73**（Fisher z = +6.47, p < 0.001）<br>• **20–30% 真实数据 + 70–80% 合成数据** 的固定预算分配最优<br>• 合成数据使 Jaccard-overlap 检索代理的 nDCG@10 **下降 26%** |
| **创新点** | 首次用严格的体积对照实验证明：合成专利数据的表面提升大多是 volume effect；提出 fidelity 指标与下游任务效用之间的 regime-dependent 关系。 |
| **局限性** | 仅覆盖 WIPO 辅助技术子集，未验证到 CPC 全层级；合成数据的法律风险（幻觉权利要求）未评估；ModernBERT 出现 Flash-Attention-2 + bf16 数值伪影，需 fp32 恢复。 |

---

### 5. TRIZ-RAGNER: A Retrieval-Augmented Large Language Model for TRIZ-Aware Named Entity Recognition in Patent-Based Contradiction Mining

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2602.23656 |
| **发布日期** | 2026-02-27 |
| **作者/机构** | Zitong Xu, Yuqing Wu, Yue Zhao |
| **核心问题** | TRIZ 矛盾挖掘是专利分析和系统创新的基础任务，但现有方法受限于语义歧义和领域依赖性；直接应用 LLM 存在幻觉且缺乏结构化 TRIZ 知识支撑。 |
| **主要方法** | **TRIZ-RAGNER**：将矛盾挖掘重构为语义级 NER 任务，集成密集检索（TRIZ 知识库）、交叉编码器重排序和结构化 LLM 提示，注入领域专用 TRIZ 知识以降低语义噪声。 |
| **关键数据集** | **PaTRIZ** 数据集 |
| **核心结果** | • Precision：**85.6%**<br>• Recall：**82.9%**<br>• F1：**84.2%**<br>• 比最强基线（prompt-enhanced GPT）**绝对 F1 提升 7.3 pp** |
| **创新点** | 将 RAG 与 TRIZ 本体知识结合，用于专利句级别的技术参数抽取；首次在矛盾挖掘任务上实现检索增强的 TRIZ 知识注入。 |
| **局限性** | 仅在 PaTRIZ 单数据集验证；未覆盖多语言专利；TRIZ 知识库的完整性和更新频率未讨论。 |

---

### 6. Large Language Models, Encoder Architectures and Hybrid Approaches for Patent Classification

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2601.23200v2 |
| **发布日期** | 2026-01-30 (v2: 2026-08-05) |
| **作者/机构** | Lorenzo Emer, Marco Lippi, Andrea Mina, Andrea Vandin |
| **核心问题** | 自动化专利分类（CPC 层级多标签）是技术监测和知识产权分析的核心，但 encoder 与 LLM 的相对优劣、能耗差异及下游指标传播效应缺乏受控比较。 |
| **主要方法** | 对专利专用 encoder（task-adapted BERT-for-Patents）与开源本地 LLM（fine-tuned Qwen3.5-9B）进行受控对比；进一步提出混合 pipeline：将 encoder 不确定性最高的样本路由至 LLM。 |
| **关键数据集** | USPTO 专利数据（CPC 分类）；外部验证：EPO 专利 |
| **核心结果** | • 最佳 encoder（BERT-for-Patents）** outperform **最佳 LLM（Qwen3.5-9B）<br>• Encoder 推理能耗低 **1–2 个数量级**<br>• 混合 pipeline 在不确定性高的子集上取得显著提升<br>• 分类错误在 CPC Section Y 等跨领域语义宽泛类别最严重<br>• 错误会显著传播到下游技术映射、国家和权利人排名 |
| **创新点** | 首个涵盖预测性能、层级性能、能耗、外部验证和下游指标传播的全维度专利分类对比研究；提出基于不确定性的混合路由策略。 |
| **局限性** | 仅对比单一 LLM（Qwen3.5-9B）；未纳入更长上下文 LLM（如 128K/1M context）的 zero-shot/few-shot 能力评估；能耗测量依赖估算而非实际瓦时记录。 |

---

### 7. PatRe: A Full-Stage Office Action and Rebuttal Generation Benchmark for Patent Examination

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2605.03571 |
| **发布日期** | 2026-05-05 |
| **作者/机构** | Qiyao Wang, Xinyi Chen, Longze Chen, Hongbo Wang, Hamid Alinejad-Rokny, Yuan Lin, Min Yang |
| **核心问题** | 现有专利审查基准多为判别式分类或静态抽取，未能捕捉审查过程固有的交互性和迭代性（类似学术审稿-反驳循环）。 |
| **主要方法** | 提出 **PatRe**：首个覆盖专利审查全生命周期（Office Action 生成 + 申请人反驳）的基准，含 480 真实案例，支持 oracle 与检索模拟两种评估设定。 |
| **关键数据集** | 480 真实世界专利审查案例 |
| **核心结果** | • **GPT-5-mini** 在 Office Action 和 Rebuttal 两任务上均表现最优<br>• 专有模型与开源模型存在显著性能差距<br>• 审查员侧分析（Office Action）与申请人侧反驳（Rebuttal）存在**任务不对称性**<br>• 模型在表面语言风格与内部逻辑维度之间存在**性能解耦** |
| **创新点** | 首次将专利审查形式化为动态多轮对话任务；引入 LLM-as-a-Judge 的多维度审计（客观确定性指标 + 语义逻辑审计）。 |
| **局限性** | 数据量 480 案例相对有限；仅覆盖特定法域（未明确是否多国）；LLM-as-a-Judge 的评审标准可能存在模型自身偏好偏差。 |

---

### 8. The First Token Is Not the Verdict: Hidden Costs of Reading LLM Judges Without Generating

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2610.00054 |
| **发布日期** | **2026-10-02** |
| **作者/机构** | Gnaneswar Villuri, Hashmath Shaik, Alex Doboli |
| **核心问题** | 从 LLM judge 的首个生成 token 的 logits 读取判决（无需完整生成）虽廉价，但是否可靠？ |
| **主要方法** | 系统测量 Qwen3、Llama-3.1-8B、Phi-3.5-mini 在成对比较中"首 token 即判决"的比率，对比强制读取与完整生成后的位置偏差。 |
| **关键数据集** | 924 对 judge 未立即承诺的样本；多模型、多条件测试 |
| **核心结果** | • Qwen3 系列：首 token 非判决的比率 **12%–49%**<br>• Llama-3.1-8B / Phi-3.5-mini：**< 3%**<br>• 强制读取在 swap 后翻转率：**89.7%** vs. 生成后读取 **47.5%**（paired diff **+0.422**, 95% CI [+0.365, +0.467]）<br>• 位置偏差被夸大 **42 个百分点**，而准确率几乎不变（7/10 条件下 < 1 pp） |
| **创新点** | 首次量化"首 token 读取"对 judge 审计的系统性扭曲；提出报告"首 token 承诺率"作为标准化实践。 |
| **局限性** | 未覆盖商业 API judge（GPT-4.5、Claude 4 等）；实验主要基于特定大小的开源模型，结论是否推广到超大模型待验证。 |

---

### 9. Legal text classification in Korean sexual offense cases: from traditional machine learning to large language models with XAI insights

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2610.00087 |
| **发布日期** | **2026-10-02** |
| **作者/机构** | Jeongmin Lee |
| **期刊状态** | Artificial Intelligence and Law (2025) 已发表 |
| **核心问题** | 法律文本分类因文本复杂性和类别间微妙差异而困难；LLM 是否必然优于小型领域适应模型？ |
| **主要方法** | 在十类韩国性犯罪判例上，对比传统机器学习、KLUE-BERT 微调、GPT-3.5/4.0；引入 XAI 分析预测与误分类。 |
| **关键数据集** | 韩国性犯罪判例（10 类）；KICS 数据（更接近真实案例） |
| **核心结果** | • **KLUE-BERT** 准确率：**99.3%**（最高）<br>• 小型领域适应模型 **优于** GPT-3.5 和 GPT-4.0<br>• KICS 数据上模型难以解释**隐式上下文线索** |
| **创新点** | 用高准确率法律分类实验证明：领域适应和微调可能比模型规模更重要；XAI 揭示模型决策的语言学特征和盲点。 |
| **局限性** | 单一法域（韩国）、单一罪名类别；99.3% 准确率可能受益于数据集本身的类别分离度，需跨法域验证。 |

---

### 10. Metric-Construction Coupling Inflates Measured Synthetic Dialect Recovery

| 项目 | 内容 |
|---|---|
| **arXiv 编号** | 2610.00164 |
| **发布日期** | **2026-10-02** |
| **作者/机构** | Hyojung Han (ThakiCloud) |
| **核心问题** | 合成数据评估中，构造方法与评估指标共享 inventory 时，是否会人为夸大恢复率？ |
| **主要方法** | 构建 **KoDialectBench**（1,000 项，5 地区，3 维度），通过 withholding 20% marker types 的 construction-disjoint 实验，直接测量 metric-construction coupling 效应；提出 MCC（Metric-Construction Coverage）。 |
| **关键数据集** | KoDialectBench（1,000 项， released as identifier hashes + scoring code） |
| **核心结果** | • 最佳合成方案在 region identification 达真实数据增益的 **91.2%**，comprehension 仅 **63.7%**<br>• construction-disjoint 条件下（8,600 例）：dialectness recovery 从 **91.8% → 8.1%**；region-match 从 **101.9% → 25.6%**<br>• MCC 从 0 → 1 时，测量的 dialectness recovery 单调上升 |
| **创新点** | 首次用 construction-disjoint 对照实验证明：共享构造与评估 inventory 可严重夸大合成数据恢复率；提出 MCC 量化指标。 |
| **局限性** | 仅覆盖韩语方言；MCC 定义依赖离散的 marker type，推广到连续或开放域合成数据（如专利文本）需进一步验证。 |

---

## 三、横向数据对比表

### 表 1：专利直接相关论文核心指标对比

| 论文 | 任务 | 最佳方法 | 关键指标 | 数值 | 对比基线/说明 |
|---|---|---|---|---|---|
| Zenovkin et al. (2610.01553) | 专利 prior art 检索 | Neural parser + Graph Transformer | Citation recall (short query) | +0.5% | vs. rule-based parser |
| Zenovkin et al. (2610.01553) | 专利 prior art 检索 | Neural parser + Graph Transformer | Citation recall (full doc) | +1.1% | vs. rule-based parser |
| Zhu et al. (2609.30943) | 专利长文撰写 | LogicTree-RAG | Content quality / conformity | +33% | vs. strong LLM baselines |
| Banerjee (2607.13044) | AI 生成专利检测 | Binoculars | FPR (EPO H04) | 78.3% | 消费级 GPU，500 vs 500 |
| Banerjee (2607.13044) | AI 生成专利检测 | Fast-DetectGPT | FPR (EPO H04) | 61.3% | 同上 |
| Banerjee (2607.13044) | AI 生成专利检测 | DetectGPT | FPR (EPO H04) | 80.5% | 同上 |
| Banerjee (2607.13044) | AI 生成专利检测 | 7-feature logistic regression | Accuracy / FPR | 74.0% / 28.1% | 不依赖 likelihood |
| Yousefiramandi & Cooney (2605.24296) | 专利多标签分类 | BERT-for-Patents + synthetic | micro F1 (full synthetic) | 0.702 | 但对照 0.678，真实增益 +0.024 |
| Yousefiramandi & Cooney (2605.24296) | 专利多标签分类 | BERT-for-Patents + synthetic | 最佳固定预算配比 | 20–30% 真实 + 70–80% 合成 | 优于纯合成或纯真实 |
| Xu et al. (2602.23656) | TRIZ 矛盾挖掘 | TRIZ-RAGNER | F1 | 84.2% | vs. prompt-enhanced GPT +7.3 pp |
| Emer et al. (2601.23200) | CPC 专利分类 | BERT-for-Patents (encoder) | Micro-F1 | 优于 Qwen3.5-9B | 能耗低 1–2 数量级 |
| Wang et al. (2605.03571) | 专利审查对话 | GPT-5-mini | Office Action + Rebuttal | 最优 | 专有模型 > 开源模型 |

### 表 2：合成/生成数据评估方法对比（跨领域启示）

| 论文 | 领域 | 核心教训 | 关键数值 |
|---|---|---|---|
| Yousefiramandi & Cooney (2605.24296) | 专利分类 | 合成数据增益多为 volume effect；高 regime 下 fidelity 与性能负相关 | MMD-性能 r: +0.95 → -0.73 |
| Han (2610.00164) | 方言恢复 | 构造-评估耦合严重夸大恢复率 | construction-disjoint 后 91.8% → 8.1% |

> **横向解读：** 两篇论文从不同领域（专利、方言）共同指向一个方法论警示——**合成数据的表面提升必须经 construction-disjoint 或体积对照检验**，否则评估结论可能不可信。这对正在探索 LLM 生成专利文本（权利要求、摘要）的研究具有直接借鉴意义。

---

## 四、趋势观察与值得后续追踪的方向

### 1. 专利图结构化表示成为新焦点
Zenovkin et al. (2610.01553) 的 neural parser 代表了专利 NLP 从"文本嵌入"向"结构化发明图"的演进。传统 dense retrieval 在 40k+ token 专利文档上必然截断，而图表示天然支持长文档。后续可追踪：
- 该神经解析器是否开源；
- 与 GraphRAG、知识图谱增强 LLM 的结合潜力；
- 在生物技术、化学专利（更长、更结构化）上的泛化。

### 2. 长文本生成：从"写段落"到"写全文"
Zhu et al. (2609.30943, NeurIPS 2026) 的 LogicTree-RAG 将专利起草从局部生成推进到全文级自动化。随着 LLM 上下文窗口持续扩大（1M+ tokens），逻辑树与长上下文的协同机制值得进一步探索。

### 3. AI 检测的"法律文体陷阱"具有结构性
Banerjee (2607.13044) 证明专利法本身的文体约束（清晰、简洁、低困惑度）使 AI 检测器失效。这不是模型容量问题（H100 复现同样失败），而是**检测假设与法律注册条件之间的根本冲突**。专利局若部署自动化 AI 筛查，需转向 off-axis 语言学特征而非困惑度。追踪方向：多语言专利局（JPO、CNIPA、KIPO）的跨文化验证。

### 4. 合成专利数据的"体积幻觉"需要行业共识
Yousefiramandi & Cooney (2605.24296) 以严格的体积对照瓦解了"合成数据万能"的叙事。Clarivate 作为知识产权数据巨头，其内部实验设计（focal loss reweighting 基线、MMD 相关性反转）为行业提供了方法论范本。后续应关注：
- 该结论是否推广到生成式任务（如权利要求生成、摘要生成）；
- WIPO、EPO、USPTO 对合成训练数据的政策立场。

### 5. Encoder vs. LLM 的能效博弈
Emer et al. (2601.23200) 量化了 BERT-for-Patents 相对 Qwen3.5-9B 的 1–2 数量级能耗优势。在专利分类这类高吞吐量、高频次任务中，encoder 的经济性不可忽视。混合路由（不确定性阈值触发 LLM）可能是近期最实用的部署范式。

### 6. 10-01/02 的 AI/NLP 新论文对专利研究的间接启示
- **首 token 读取偏差**（Villuri et al., 2610.00054）：若未来使用 LLM-as-a-Judge 评估专利质量或审查意见，必须避免从首 token logits 读取判决，否则位置偏差将被夸大 42 pp。
- **合成数据评估耦合**（Han, 2610.00164）：直接警示专利领域的合成权利要求/摘要评估——若评估词表与生成规则共享 inventory，恢复率将被严重高估。
- **领域微调优于通用 LLM**（Lee, 2610.00087）：KLUE-BERT 以 99.3% 准确率击败 GPT-4.0，再次印证专利/法律 NLP 中领域适应的核心价值。

---

## 五、检索来源与关键词记录

| 来源 | 查询/使用方式 | 结果状态 |
|---|---|---|
| arXiv RSS cs.CL | 2026-10-02 当日 RSS 全文拉取 | 约 40+ 篇新论文，其中 0 篇直接专利相关 |
| arXiv RSS cs.IR | 2026-10-02 当日 RSS 全文拉取 | 约 20+ 篇新论文，其中 **1 篇**直接专利相关（2610.01553，日期标记 2026-10-01） |
| arXiv RSS cs.AI | 2026-10-02 当日 RSS 全文拉取 | 约 30+ 篇新论文，其中 0 篇直接专利相关 |
| arXiv API | `search_query=all:patent&sortBy=submittedDate` | **Rate exceeded**，未返回有效结果 |
| arXiv API | `search_query=all:patent+AND+all:"large language model"` | **Rate exceeded**，未返回有效结果 |
| Semantic Scholar API | `query=large+language+model+patent&sort=pubDate:desc` | **429 Too Many Requests** |
| OpenAlex API | `search=patent+large+language+model&sort=publication_date:desc` | 返回 188,084 条，但前 10 条中仅部分相关 |
| WebSearch | `arxiv 2610 patent OR "intellectual property"` | 命中 2610.01553 等 |
| WebSearch | `arxiv patent classification NLP 2026` | 命中 2601.23200、2605.24296 等 |
| WebSearch | `arxiv "patent" "large language model" OR "LLM" 2026` | 命中 2609.30943、2607.13044 等 |

**说明：** 由于 arXiv API 和 Semantic Scholar API 在检索时触发速率限制，10-01 当日专利交叉领域的覆盖主要依赖 arXiv RSS 与 WebSearch 交叉验证。若当天存在未通过 RSS 索引的更新（如版本替换 v2），可能存在遗漏。

---

*报告结束*
