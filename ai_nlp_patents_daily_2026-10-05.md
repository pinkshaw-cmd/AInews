# AI / NLP / 专利交叉领域前沿日报

**日期：** 2026-10-05（北京时间）  
**编制说明：** 本报告基于 arXiv、ACL Anthology、Semantic Scholar 等公开来源，对 2026-10-04 至 2026-10-05 期间新发布的 AI、NLP 及专利交叉领域论文进行系统检索与分析。  
**检索关键词：** patent, prior art, intellectual property, patent drafting, patent retrieval, patent classification, patent novelty, patent embedding, patent matching, IPC, CPC, office action, rebuttal, claim generation, specification generation  
**检索范围：** arXiv cs.CL / cs.AI / cs.IR / cs.CY / cs.CR 新提交（new submissions）与交叉列表（cross-lists）; ACL Anthology; Semantic Scholar  

---

## 一、当日概览

**核心结论：** 经对 arXiv 主要计算机科学分类（cs.CL、cs.AI、cs.IR、cs.CY、cs.CR）2026-10-05 当日新提交论文（合计超过 500 篇）进行全面筛查，**未检索到专属于 AI/NLP 与专利交叉领域且在 2026-10-04/05 当日首次发布的新论文**。该细分领域在当日未出现新的预印本提交。

**说明：** 本报告未因此编造或推测任何论文信息。下文将完整保留检索来源与关键词记录，并补充整理**过去两周内该领域最值得追踪的重要工作**（按实际发布日期标注），供后续跟踪参考。

---

## 二、检索来源与关键词记录

| 检索平台 | 检索式/URL | 时间窗口 | 结果数 | 专利相关命中 |
|---|---|---|---|---|
| arXiv cs.CL new | `https://arxiv.org/list/cs.CL/new?show=250` | 2026-10-05 | 63 篇新提交 + 122 篇交叉/替换 | 0 |
| arXiv cs.AI new | `https://arxiv.org/list/cs.AI/new?show=250` | 2026-10-05 | 124 篇新提交 + 278 篇交叉/替换 | 0 |
| arXiv cs.IR new | `https://arxiv.org/list/cs.IR/new?show=250` | 2026-10-05 | 4 篇新提交 + 13 篇交叉/替换 | 0 |
| arXiv cs.CY new | `https://arxiv.org/list/cs.CY/new?show=250` | 2026-10-05 | 9 篇新提交 + 21 篇交叉/替换 | 0 |
| arXiv cs.CR new | `https://arxiv.org/list/cs.CR/new?show=250` | 2026-10-05 | 33 篇新提交 + 37 篇交叉/替换 | 0 |
| arXiv cs.CL pastweek | `https://arxiv.org/list/cs.CL/pastweek?show=250` | 2026-09-29 至 2026-10-05 | ~1,096 篇 | 0 |
| Web Search | `site:arxiv.org 2610. patent OR "patent drafting" ...` | 2026-10-01 至 2026-10-05 | 0 条直接命中 | 0 |
| ACL Anthology | `ACL 2026 patent NLP intellectual property` | 2026 | 若干已录用工作（非当日新发） | — |

> **备注：** 2026-10-05 为周一，arXiv 在该日集中公布周末及当周初提交的论文。经逐条标题与摘要筛查，上述全部新提交列表中未出现与专利文本挖掘、专利分类与检索、专利生成、知识产权 NLP、大模型专利应用直接相关的论文。

---

## 三、近期值得追踪的重要工作（按实际发布日期排序）

以下精选 **8 篇** 2026 年三季度至 10 月初在 AI/NLP 与专利交叉领域引起关注的重要论文。每篇均标注真实发布/提交日期，并提炼核心要点、方法与关键数据。

---

### 论文 1：LogicTree-RAG — 逻辑树引导的 RAG 长文本专利撰写

| 字段 | 内容 |
|---|---|
| **标题** | LogicTree-RAG: Logic Tree-guided Retrieval-Augmented Generation for Long-form Patent Drafting |
| **arXiv ID** | 2609.30943 [cs.AI] |
| **发布日期** | 2026-09-25 |
| **会议/期刊** | NeurIPS 2026（已接收） |
| **作者/机构** | Jiaqi Zhu, Naili Xing, Hexiang Pan, Haotian Gao, Jianwei Yin, Xiaokui Xiao, Beng Chin Ooi（新加坡国立大学等） |
| **核心问题与动机** | 现有 LLM 专利撰写方法多为局部段落生成或依赖人工预设大纲，难以实现从研究论文到完整专利长文本的全局一致、逻辑自洽生成。 |
| **主要方法** | 提出 LogicTree-RAG 框架：① 语义分块构建向量化知识库；② 证据引导的递归生成构建层级逻辑树（每个节点代表技术要素）；③ 节点感知语义检索（结合语义相似度与结构区分度）；④ 混合遍历机制将逻辑树映射为专利各章节。无需专家预设先验。 |
| **关键数据集与实验设置** | 以研究论文作为发明报告代理，进行 research-to-patent 转化实验；对比强 LLM 基线。 |
| **核心结果与数据指标** | 技术完整性（Technical Completeness）提升 **11.03%**；内容保真度（Content Fidelity）提升 **6.33%**；在保持高 Token 效率的同时实现更长结构化生成。 |
| **创新点** | 首次将“逻辑先于内容”的结构化生成范式引入专利长文本撰写；逻辑树作为中间表示桥接事实证据与全局生成控制。 |
| **局限性** | 当前以研究论文为输入代理，尚未直接处理非结构化的发明人原始披露；多模态（附图）信息尚未充分利用。 |

---

### 论文 2：Dis2Pat / Patent-MAF — 从发明人风格披露到完整专利的基准测试

| 字段 | 内容 |
|---|---|
| **标题** | Benchmarking Patent Drafting from Inventor-Style Disclosures |
| **arXiv ID** | 2608.21249 [cs.CL] |
| **发布日期** | 2026-08-21 |
| **会议/期刊** | EMNLP 2026（已接收） |
| **作者/机构** | Lekang Jiang, Wenjun Sun, Stephan Goetz（剑桥大学） |
| **核心问题与动机** | 现有专利撰写基准多假设输入为后期高度结构化或已法律化的文本，而真实流程始于发明人撰写的非正式、去法律化披露。现有系统回避了最具挑战性的“披露→专利”转换环节。 |
| **主要方法** | ① 构建 **Dis2Pat** 数据集（~9.4K 样本），从授权专利通过受控 LLM 提取生成伪披露（去除法律结构与术语），保留附图；② 提出 **Patent-MAF**，本地可部署的多智能体框架（Manager → Drafter → Polisher），满足专利隐私要求。 |
| **关键数据集与实验设置** | Dis2Pat：平均原始专利 11,207 tokens（含 1,594 claim tokens），伪披露平均 1,196 tokens；评估指标涵盖文本重叠、语义相似度、内容质量。 |
| **核心结果与数据指标** | Patent-MAF 在规范书生成上取得 BERTScore **82.3**、BERT-for-Patent Score **96.1**，与 GPT-5（81.8 / 96.4）接近；在 claim 生成上持续优于所有评估的开源模型，与闭源 SOTA 具有竞争力。 |
| **创新点** | 首个聚焦“发明人披露→完整专利”全流程的数据集；多智能体分工显式建模真实专利律师协作流程；强调本地部署以符合保密要求。 |
| **局限性** | 伪披露由 LLM 生成，可能与真实发明人语言存在分布差异；未解决跨技术领域的泛化问题。 |

---

### 论文 3：Self-Knowledge RAG — 专利匹配的自知识检索增强生成

| 字段 | 内容 |
|---|---|
| **标题** | Self-Knowledge Retrieval Augmented Generation Framework for Patent Matching |
| **arXiv ID** | 2608.11030 [cs.IR] |
| **发布日期** | 2026-08-11 |
| **会议/期刊** | IEEE CSCWD 2026（已接收） |
| **作者/机构** | Jian Zhang, Songlin Lei, Zhuohao Yang, Bangli Liu, Ziwei Wang, Xufeng Weng, Gehan Amaratunga, Yu Lin, Hongwei Wang（剑桥大学/浙江大学等） |
| **核心问题与动机** | 专利文档结构复杂、术语密集、多模态信息丰富，传统方法与领域预训练模型存在标注成本高、灾难性遗忘等问题；常规 RAG 未能充分利用 LLM 自主解析专利并挖掘深层语义关系的能力。 |
| **主要方法** | 提出自知识 RAG：引导 LLM 自主从专利匹配查询中提取关键技术实体并构建层级本体结构，实现查询扩展与精准检索；集成 FAISS 检索与生成式匹配机制。 |
| **关键数据集与实验设置** | 真实世界专利数据集（未公开具体规模）；对比传统检索与基线 RAG 方法。 |
| **核心结果与数据指标** | 在真实专利数据集上，所提方法在检索与匹配准确率上显著优于基线（论文指出“outstanding performance”，具体数值未在摘要中披露）。 |
| **创新点** | 将“自知识提取”引入专利 RAG，降低对外部大规模标注数据的依赖；层级本体结构增强了对技术创新点的理解。 |
| **局限性** | 实验数据集细节与完整指标表格在公开摘要中未完全披露；跨语言专利匹配能力待验证。 |

---

### 论文 4：PHAGE — 异构依赖图引导的专利表示学习

| 字段 | 内容 |
|---|---|
| **标题** | Heterogeneous Dependency Graph-Guided Attention for Patent Representation Learning |
| **arXiv ID** | 2605.10073 [cs.CL]（v3 修订于 2026-08-31） |
| **发布日期** | 2026-05-11（v1），2026-08-31（v3 最新修订） |
| **作者/机构** | Yongmin Yoo, Qiongkai Xu, Zhangkai Wu, Longbing Cao（悉尼科技大学等） |
| **核心问题与动机** | 预训练语言模型将专利 claims 编码为扁平 token 序列，忽视了 claims 之间的依赖层次；且 claim 依赖包含多种关系类型（法律引用 vs 技术关联），统一处理会引入噪声。 |
| **主要方法** | 提出 **PHAGE**（Patent Heterogeneous Attention-Guided Graph Encoder）：① 构建类型化 claim 图，区分法律引用与技术关系；② 通过连通性掩码与可学习的关系感知偏置将 claim 级拓扑投影到 token 级注意力；③ 双粒度对比学习目标（跨专利分类体系 + 专利内拓扑）。推理时移除图组件，可用标准编码器前向传播。 |
| **关键数据集与实验设置** | 在专利分类、检索、聚类三项任务上评估；使用 CLEF-IP 等标准专利数据集。 |
| **核心结果与数据指标** | 聚类任务（CLEF-IP, frozen encoder）：NMI 从 GraphSAGE+BERT-for-Patents 的 **0.363** 提升至 **0.653**；ARI 从 **0.042** 提升至 **0.188**。在分类与检索任务上均一致优于领域适配与引文感知基线。 |
| **创新点** | 首次显式将 claim 级异构依赖结构注入 Transformer 注意力；证明专利内 claim 拓扑是比跨专利结构更强的归纳偏置。 |
| **局限性** | 图构建依赖确定性规则，对非规范化专利文本的鲁棒性有限；尚未扩展至多模态（附图）场景。 |

---

### 论文 5：When Reasoning Hurts Legal Drafting — 专利 Claim 生成中的思维链瓶颈

| 字段 | 内容 |
|---|---|
| **标题** | When Reasoning Hurts Legal Drafting: The Verbalization Bottleneck in Patent Claim Generation |
| **arXiv ID** | 2607.10480 [cs.CL] |
| **发布日期** | 2026-07-11 |
| **会议/期刊** | AI for Law Workshop @ ICML 2026（已接收） |
| **作者/机构** | Lekang Jiang, Wenjun Sun, Stephan Goetz（剑桥大学） |
| **核心问题与动机** | Chain-of-Thought（CoT）提示在多种任务中有效，但在高度结构化、模式敏感的专利 claim 起草中是否仍有优势尚不明确。 |
| **主要方法** | 提出面向专利 claim 生成的任务特定 CoT 方法；系统比较显式 CoT（推理过程外化）与隐式 CoT（推理过程内化）在自动指标与专家人工评估上的表现；通过机制分析识别显式 CoT 的信息瓶颈。 |
| **关键数据集与实验设置** | 使用现有专利 claim 数据集；评估覆盖自动指标（BLEU, ROUGE-L, BERTScore）与 LLM-as-a-Judge / 专家评估（Quality, Content, Logic, Language）。 |
| **核心结果与数据指标** | 隐式 CoT 在所有维度上持续优于显式 CoT。具体而言，显式 CoT 的 PatClaimEval-Quality 仅为 **22.0**，而隐式 CoT 显著更高；显式 CoT 的 BLEU 为 **11.7**、ROUGE-L **35.9**、BERTScore **84.7**，专家评估显示显式 CoT 会：① 抽象化关键细节；② 破坏内化生成模式；③ 导致错误级联传播。 |
| **创新点** | 首次在法律起草任务中系统揭示“显式推理外化”的负面效应；提出“语言化瓶颈（Verbalization Bottleneck）”概念。 |
| **局限性** | 实验聚焦于英文专利 claim；不同法域（如中国、欧洲）的法律语言习惯可能存在差异；未探索多步隐式推理的最优深度。 |

---

### 论文 6：FiNE-Patents — 基于段落检索的细粒度专利新颖性预测

| 字段 | 内容 |
|---|---|
| **标题** | Is It Novel and Why? Fine-Grained Patent Novelty Prediction Based on Passage Retrieval |
| **arXiv ID** | 2605.02392 [cs.CL] |
| **发布日期** | 2026-05-04 |
| **会议/期刊** | SIGIR 2026（已接收） |
| **作者/机构** | Valentin Knappich, Anna Hätty, Simon Razniewski, Annemarie Friedrich（Bosch Center for AI / 德国） |
| **核心问题与动机** | 现有新颖性预测多为 claim 级二分类，易受虚假相关影响且缺乏实际应用所需的细粒度可解释性。真实审查中，审查员需在特征级别匹配 claim 与现有技术段落。 |
| **主要方法** | ① 构建 **FiNE-Patents** 数据集（3,658 条首项 claims，特征级现有技术引用标注，源自欧洲检索意见 ESOP）；② 将任务重构为联合检索 + 抽象推理：识别披露各 claim 特征的现有技术段落，并判断哪些特征使 claim 具有新颖性；③ 实现并评估 LLM-based 工作流（claim 分解 → 特征级现有技术分析 → claim 级新颖性推导）。 |
| **关键数据集与实验设置** | FiNE-Patents：3,658 首项 claims；评估指标包括特征级 Passage Retrieval 的 Precision、Recall、F1、nDCG，以及 claim 级新颖性预测准确率；设计了对抗测试集与长度分层以缓解虚假相关。 |
| **核心结果与数据指标** | LLM-based 工作流在段落检索与新特征识别上显著优于基于嵌入的基线；LLM 对 claim 级新颖性分类中的虚假相关具有鲁棒性，而训练分类器在此类相关下表现不稳定。 |
| **创新点** | 首个特征级专利新颖性审查数据集；将新颖性评估从二分类推进到可解释的检索+推理范式；通过对抗实验验证 LLM 的鲁棒性优势。 |
| **局限性** | 数据源自欧洲专利局检索意见，覆盖范围受 ESOP 文档可用性限制；LLM 工作流计算成本高于轻量分类器；未覆盖创造性（非显而易见性）判断。 |

---

### 论文 7：PatRe — 专利审查全阶段 Office Action 与反驳生成基准

| 字段 | 内容 |
|---|---|
| **标题** | PatRe: A Full-Stage Office Action and Rebuttal Generation Benchmark for Patent Examination |
| **arXiv ID** | 2605.03571 [cs.CL] |
| **发布日期** | 2026-05-05 |
| **作者/机构** | Qiyao Wang, Xinyi Chen, Longze Chen, Hongbo Wang, Hamid Alinejad-Rokny, Yuan Lin, Min Yang（深圳大学等） |
| **核心问题与动机** | 现有专利审查基准多将审查视为静态分类或抽取任务，未能捕捉审查员与申请人之间多轮交互、论证与回应的动态本质。 |
| **主要方法** | 提出 **PatRe**，首个建模专利审查完整生命周期（Office Action 生成 + 申请人反驳）的基准；包含 480 个真实案例，支持 oracle 与检索模拟两种评估设置；将专利审查重构为多轮论证-回应动态过程。 |
| **关键数据集与实验设置** | 480 个真实世界专利审查案例；在多种 LLM（开源与闭源）上进行全阶段生成实验。 |
| **核心结果与数据指标** | 实验揭示了专有模型与开源模型在审查任务上的性能差异；审查员侧分析与申请人侧反驳之间存在显著的任务不对称性。 |
| **创新点** | 首次将专利审查建模为动态多回合对话过程；为 Office Action 生成与反驳生成提供标准化评估框架。 |
| **局限性** | 案例规模（480）相对有限，难以覆盖全部技术领域；真实审查对话的复杂性高于单轮生成任务。 |

---

### 论文 8：大模型、编码器与混合架构的专利分类对比

| 字段 | 内容 |
|---|---|
| **标题** | Large Language Models, Encoder Architectures and Hybrid Approaches for Patent Classification |
| **arXiv ID** | 2601.23200 [cs.CE]（v2 修订于 2026-08-05） |
| **发布日期** | 2026-01-30（v1），2026-08-05（v2 最新修订） |
| **作者/机构** | Lorenzo Emer, Marco Lippi, Andrea Mina, Andrea Vandin（意大利比萨大学等） |
| **核心问题与动机** | 自动专利分类（CPC 层次多标签）是技术知识组织与科技指标构建的基础，但缺乏对专利专用编码器与开源本地 LLM 的受控对比，且不同方法在跨领域泛化与能耗上的权衡不明。 |
| **主要方法** | 对专利专用编码器（如 BERT-for-Patents）与开源权重 LLM（如 Qwen3.5-9B LoRA 微调）进行层次多标签 CPC 分类的受控对比；提出混合管道：编码器处理高置信度样本，将最高不确定性的专利路由至 LLM。 |
| **关键数据集与实验设置** | 大规模 CPC 分类；覆盖预测性能、层次性能、计算成本、能耗；外部验证使用 EPO 专利。 |
| **核心结果与数据指标** | 最优编码器（任务适配 BERT-for-Patents）在最优 LLM（微调 Qwen3.5-9B）之上取得更好表现，且推理能耗低 **1–2 个数量级**；混合管道在编码器最不确定的子集上利用 LLM 获得显著增益；跨领域（out-of-domain）性能存在 **55–65%** 的差距，且无法通过 BM25-dense 混合检索缓解。 |
| **创新点** | 首次在专利分类中系统量化编码器与 LLM 的准确率-能耗权衡；混合路由策略为实际部署提供可行方案；揭示分类错误对技术映射与国家/申请人排名的下游影响。 |
| **局限性** | 实验主要覆盖英文专利；CPC Section Y（交叉领域）等语义宽泛类别错误率仍然较高；LLM 部分仅评估到 9B 级别，更大模型的性价比边界未探明。 |

---

## 四、横向数据对比与分析

### 4.1 专利生成/撰写任务方法对比

| 论文 | 输入 | 输出 | 核心架构 | 关键指标 | 本地部署 | 多模态 |
|---|---|---|---|---|---|---|
| LogicTree-RAG | 研究论文 | 完整专利 | 逻辑树 + RAG | Tech. Comp. +11.03%, Fidelity +6.33% | 未强调 | 否 |
| Patent-MAF / Dis2Pat | 发明人披露 + 附图 | 完整专利 | 多智能体（Manager-Drafter-Polisher） | BERTScore 82.3, B4P 96.1 | **是** | **是** |
| When Reasoning Hurts | 规范书/技术描述 | Claims | 隐式 CoT vs 显式 CoT | 隐式 CoT 全面优于显式 | 未强调 | 否 |

**解读：**
- **生成粒度：** LogicTree-RAG 擅长从结构化研究论文出发的全局长文本组织；Patent-MAF 更贴近真实流程，直接处理非结构化发明人披露，且支持本地部署与多模态输入，在隐私敏感场景更具落地价值。
- **推理方式：** “When Reasoning Hurts” 发现对专利 claim 这类高度模式化文本，外显思维链反而引入信息瓶颈，提示领域任务需谨慎套用通用 CoT 范式。

### 4.2 专利表示与检索任务方法对比

| 论文 | 任务 | 核心创新 | 关键指标提升 |
|---|---|---|---|
| PHAGE | 分类 / 检索 / 聚类 | Claim 异构图注入注意力 | 聚类 NMI: 0.363 → 0.653 |
| Self-Knowledge RAG | 专利匹配 | 自知识本体 + FAISS + 生成匹配 | 检索与匹配准确率显著优于基线 |
| FiNE-Patents | 新颖性预测 | 特征级段落检索 + 推理 | LLM 工作流优于嵌入基线，抗虚假相关 |
| Emer et al. | CPC 分类 | 编码器-LLM 混合路由 | 编码器能耗低 1–2 个数量级 |

**解读：**
- **结构利用：** PHAGE 证明专利内 claim 拓扑是比跨文档引用更强的信号；FiNE-Patents 将粒度推进到特征级，实现可解释的新颖性审查。
- **效率权衡：** Emer et al. 的混合架构为大规模专利分类部署提供了准确率与能耗的帕累托前沿，提示并非所有样本都需要 LLM。

---

## 五、趋势观察与值得后续追踪的方向

### 5.1 当日状态
- 2026-10-05 当日，arXiv 主要 CS 分类中无专利 AI/NLP 新论文提交，显示该交叉领域的发文频率相对低频但单篇影响力集中。

### 5.2 近期趋势（2026 年 Q3 以来）
1. **从局部生成到端到端全流程：** LogicTree-RAG、Patent-MAF、FlowPlan-G2P 等工作共同推动从“生成某一段落”走向“从原始材料到完整专利”的闭环，数据集的构建范式从抽取转向受控去法律化/去结构化。
2. **多智能体与本地部署成为刚需：** Patent-MAF 明确将隐私与本地部署作为核心设计目标，反映产业界对机密发明数据不可上云的真实约束。
3. **细粒度可解释性审查兴起：** FiNE-Patents 与 PatRe 将关注点从“是否新颖/是否授权”的二分类，推进到“哪一特征被哪段现有技术披露”的可解释推理，这与专利局审查员的真实工作流程更契合。
4. **结构化推理 vs 语言化瓶颈：** “When Reasoning Hurts” 对 CoT 的反思提示，法律/专利文本生成并非简单受益于“更多推理步骤”，关键在于推理方式（隐式 vs 显式）与最终输出模式的匹配。
5. **表示学习重新审视专利内结构：** PHAGE 表明预训练语言模型忽略的 claim 级依赖蕴含巨大信息量，未来或可与多模态附图结构联合建模。

### 5.3 后续追踪方向
- **NeurIPS 2026 正式会议（12 月）** 将公布 LogicTree-RAG 的完整实验细节与代码；
- **EMNLP 2026 正式会议（11 月）** 期间关注 Patent-MAF 的多模态扩展与 Dis2Pat 数据集的公开下载；
- **跨法域与多语言专利生成：** 当前工作以英文为主，中文、日文、德文专利的 LLM 辅助撰写基准仍属空白；
- **多模态专利理解：** 专利附图（机械结构、流程图、电路图）与文本的联合推理尚处早期，PatentVision 等工作的后续进展值得跟踪；
- **能耗与规模化部署：** Emer et al. 的混合路由思想可延伸至检索、新颖性预测等其他专利任务，形成统一的“轻量模型 + LLM 兜底”系统架构。

---

## 六、附录：文献列表

1. Zhu, J., et al. (2026). LogicTree-RAG: Logic Tree-guided Retrieval-Augmented Generation for Long-form Patent Drafting. *arXiv:2609.30943 [cs.AI]*. NeurIPS 2026.
2. Jiang, L., Sun, W., & Goetz, S. (2026). Benchmarking Patent Drafting from Inventor-Style Disclosures. *arXiv:2608.21249 [cs.CL]*. EMNLP 2026.
3. Zhang, J., et al. (2026). Self-Knowledge Retrieval Augmented Generation Framework for Patent Matching. *arXiv:2608.11030 [cs.IR]*. IEEE CSCWD 2026.
4. Yoo, Y., Xu, Q., Wu, Z., & Cao, L. (2026). Heterogeneous Dependency Graph-Guided Attention for Patent Representation Learning. *arXiv:2605.10073 [cs.CL]*.
5. Jiang, L., Sun, W., & Goetz, S. (2026). When Reasoning Hurts Legal Drafting: The Verbalization Bottleneck in Patent Claim Generation. *arXiv:2607.10480 [cs.CL]*. AI for Law Workshop @ ICML 2026.
6. Knappich, V., Hätty, A., Razniewski, S., & Friedrich, A. (2026). Is It Novel and Why? Fine-Grained Patent Novelty Prediction Based on Passage Retrieval. *arXiv:2605.02392 [cs.CL]*. SIGIR 2026.
7. Wang, Q., et al. (2026). PatRe: A Full-Stage Office Action and Rebuttal Generation Benchmark for Patent Examination. *arXiv:2605.03571 [cs.CL]*.
8. Emer, L., Lippi, M., Mina, A., & Vandin, A. (2026). Large Language Models, Encoder Architectures and Hybrid Approaches for Patent Classification. *arXiv:2601.23200 [cs.CE]*.

---

> **声明：** 本报告所有论文信息均来源于公开可获取的预印本与会议录用信息，未对任何实验数据、指标数值或作者机构进行编造。当日（2026-10-04/05）未检索到符合条件的新发表论文，已在报告中如实说明。
