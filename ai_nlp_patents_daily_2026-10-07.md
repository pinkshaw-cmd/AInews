# AI / NLP / 专利交叉领域前沿日报

**日期**：2026-10-07（对应检索窗口：2026-10-06 announce/release）  
**编制**：TraeCode Agent  
**数据来源**：arXiv (cs.AI, cs.CL, cs.CR, cs.IR), OpenAlex API  
**检索策略**：以 arXiv 各分类 recent/pastweek 列表的 announcement 日期（Tue, 6 Oct 2026）为主窗口，辅以 OpenAlex 的 `publication_date:2026-10-06` 交叉核验，聚焦 AI、NLP、以及 AI/NLP 与知识产权/专利/法律/科学文献交叉领域。

---

## 一、当日概览

在 2026-10-06 的 arXiv announcement 窗口内，**直接以“专利文本挖掘 / 专利分类 / 专利检索 / 专利生成”为核心主题的纯技术论文非常稀少**。经对 cs.AI（554 篇）、cs.CL（243 篇）、cs.CR（94 篇）、cs.IR（33 篇）等分类的标题与摘要进行逐层关键词筛查，未发现标题或摘要中明确出现 "patent"、"patent classification"、"patent retrieval"、"patent claim generation" 等字样的当日 announce 论文。

然而，在**“AI/NLP + 知识产权保护 / 溯源 / 法律文档理解 / 科学文献知识提取”**等高度关联的交叉方向，当日出现了多篇值得关注的前沿工作，共计 **9 篇**纳入本报告。其中：
- **模型知识产权保护与溯源**（4 篇）：LLM Agent 行为水印、蛋白质生成模型放射性水印、视觉溯源与水印、词级文本解混与所有权路由；
- **法律与科学文档 NLP**（5 篇）：俄语法典长文档域适应、开源 LLM 法律 NLI 评测、材料科学文献的 Agentic 知识提取、科学文献机制知识基底、临床时间线溯源重建。

这些工作在方法论上与专利场景（长法律/技术文档理解、结构化知识提取、文本溯源、模型 IP 保护）具有显著的迁移价值。

---

## 二、逐篇要点卡片

### 卡片 1：Semantic Behavioral Watermarking for LLM Agents

| 字段 | 内容 |
|------|------|
| **arXiv 编号** | 2610.08668 |
| **标题** | Semantic Behavioral Watermarking: Paraphrase-Robust and Forgery-Resistant Provenance for LLM Agents |
| **作者/机构** | Suxin Ji (UPenn), Hungtao Wan (Independent), Shaoxuan Chen (UMass Amherst), An Zhang (Chongqing University) |
| **核心问题与动机** | 现有 LLM Agent 水印绑定在精确动作符号上，一旦工具改名或观察被改写即失效；且已有工作只研究“去除鲁棒性”，未考虑“伪造攻击”。 |
| **主要方法** | 提出 **SBW (Semantic Behavioral Watermarking)**：(1) 在语义动作聚类层面嵌入水印（而非精确符号），历史条件化；(2) 引入**密钥碰撞 resistant 分箱**（keyed collision-resistant binning），在随机谕言机模型下证明不可预测性，抵抗伪造。 |
| **关键数据集与实验设置** | ToolBench（600 trajectories / model × 5 models, 3B–14B, 4 vendors）、ALFWorld（100 episodes / model）；3 种编码器；permutation-calibrated 1% FPR。 |
| **核心结果与指标** | **ToolBench 改写攻击下检测率**：cluster-level 0.49–0.66 vs. exact-symbol 0.05–0.17；choice agreement 72–83% vs. logit biasing 22–27%。**ALFWorld**：cluster-level 0.92–0.97 vs. exact-symbol 0.00–0.01。adaptive forgery 在 keyed binning 下从 100% 降至 false-positive floor。 |
| **创新点** | 首个面向 LLM Agent 的语义行为水印；首个对 Agent 水印进行伪造攻击研究并提出密钥防御。 |
| **局限性** | 当对手复制受害者自身步骤时，chained replay 仍保持 0.76–0.98 检测率（作者明确标为 open 问题）；paraphrase 鲁棒性以约一半每步水印容量为代价。 |

---

### 卡片 2：MARCO — 蛋白质生成模型的放射性水印

| 字段 | 内容 |
|------|------|
| **arXiv 编号** | 2610.08316 |
| **标题** | MARCO: The Radioactive Watermark for Protein Generative Models |
| **作者/机构** | Huajie Chen, Xin Guo, Yuchen Shi, Yuchen Zhong, Chi Liu, Congcong Zhu, Kun Gao, Minfeng Qi, Tianqing Zhu (City University of Macau); Minhui Xue (CSIRO / RAIR Centre, Adelaide University) |
| **核心问题与动机** | 蛋白质生成模型（PGMs）面临模型窃取与生物安全滥用双重风险，亟需同时保护知识产权并支持法医级溯源。 |
| **主要方法** | **MARCO (COnformation waterMARk)**：Dual-Layer 防御框架。(1) 在扩散逆去噪过程中通过辅助 encoder-decoder 迭代嵌入水印，原 PGM 参数冻结；(2) 针对 Cα 原子对距离和扭转角（ψ, ϕ）设计专门损失函数，结合对抗训练与随机攻击模拟；(3) **放射性**特性：水印自动转移至盗版模型的输出，抵抗模型提取攻击。 |
| **关键数据集与实验设置** | 蛋白质结构生成基准（具体数据集名待从正文中进一步提取）；评估 fidelity、robustness（SE(3) 变换与恶意攻击）、radioactivity（水印向派生模型转移）。 |
| **核心结果与指标** | 在保持高保真结构的同时实现水印嵌入；对常见结构扰动与攻击具有鲁棒性；成功验证水印向 pirate 模型的可转移性（具体数值待从正文表格中提取）。 |
| **创新点** | 首个针对 PGMs 的放射性水印框架；首个同时兼顾知识产权保护和生物安全溯源的 Dual-Layer 设计。 |
| **局限性** | 论文未明确报告在超大规模蛋白质复合物上的开销；对抗训练可能引入额外的计算成本。 |

---

### 卡片 3：Rethinking Visual Provenance — 跨生成路径的检测与水印

| 字段 | 内容 |
|------|------|
| **arXiv 编号** | 2610.08137 |
| **标题** | Rethinking Visual Provenance: Detection and Watermarking Across Direct Visual Generation and LLM-Driven Code Rendering |
| **作者/机构** | Zheng Gao, Xiaoyu Li, Zhicheng Bao, Yang Song, Jiaojiao Jiang |
| **核心问题与动机** | AI 生成视觉内容存在两条路径：直接图像/视频生成 vs. LLM 编写代码/图形描述后渲染。两条路径的表示、干预点和溯源证据截然不同，现有研究缺乏统一框架。 |
| **主要方法** | 构建**生产中心框架**，明确区分被动推断、消息恢复与认证溯源三种验证规格；按生产阶段组织图像、视频、源代码与渲染感知水印；基于 Claude、OpenAI 及渲染工具接口进行系统文档化。 |
| **关键数据集与实验设置** | **概念性研究议程，无实验**（作者明确声明：reports no experiments and claims no new theorems）。 |
| **核心结果与指标** | 提出 10 个研究问题，覆盖可识别性、可观察性、跨阶段公平比较、可恢复负载、重建、同步、组合、混合本地贡献、私有生产事件认证等。 |
| **创新点** | 首次系统对比直接视觉生成与 LLM 驱动代码渲染两条路径的溯源与水印需求；将工业界工具接口（Claude, OpenAI）纳入学术框架。 |
| **局限性** | 纯概念框架，缺乏实验验证与定量评估；附录结果为基础计算与接口文档，非经验性鲁棒性结论。 |

---

### 卡片 4：EPOR — 词级文本解混与证据保持所有权路由

| 字段 | 内容 |
|------|------|
| **arXiv 编号** | 2610.06603 |
| **标题** | Word-Level Text Unmixing via Evidence-Preserving Ownership Routing with Language Models |
| **作者/机构** | Jinglin He, Siyang Jiang, Lixing He, Guoliang Xing, Hongkai Chen (The Chinese University of Hong Kong) |
| **核心问题与动机** | 当多源文本的归属元数据丢失时（如重叠语音转录、文档阅读流、并发 Agent 输出），需要将交错词流精确还原为原始源序列，且**不遗漏、不重复、不 hallucinate**任何词。 |
| **主要方法** | 提出 **EPOR (Evidence-Preserving Ownership Routing)**：(1) 解耦所有权预测与重建，因果 LLM 仅预测规范所有权路径；(2) 推理时结合**完成安全约束解码**与**确定性索引重建**，保证每个观测词恰好出现一次；(3) 引入 **UNMIXBENCH** 评测基准。 |
| **关键数据集与实验设置** | UNMIXBENCH（5 条评测轨道）：受控合成混合、AMI/ICSI 时间戳语音、ReadingBank 布局派生文档流、模拟并发数字输出；与 compact source-array generation 基线及零样本前沿 LLM 对比。 |
| **核心结果与指标** | 4B EPOR 模型在 5 条轨道上的**平均最小置换词错误率**（mean min-permutation WER）相对 compact source-array generation 基线降低 **22.3%**；与零样本前沿 LLM 保持竞争力。 |
| **创新点** | 首次形式化 Word-Level Text Unmixing 问题；提出所有权-重建解耦框架 + 完成安全约束解码，保证精确重建。 |
| **局限性** | 当前评估局限于特定领域语音与文档流；在高度语义重叠的混合场景下性能边界待探索。 |

---

### 卡片 5：俄语法典 ModernBERT 长法律文档域适应

| 字段 | 内容 |
|------|------|
| **arXiv 编号** | 2610.06715 |
| **标题** | Domain adaptation of Russian ModernBERT for long legal documents |
| **作者/机构** | I. Litvak, D. Gvozdetsky, F. Lashkin, V. Kirova, S. Lagutin, V. Volf, T. Maksiyan, A. Kostin, R. Leva, I. Kiselev |
| **核心问题与动机** | 法律文档（包括专利等知识产权文件）通常具有超长文本、高度专业化术语与复杂句法结构，通用预训练模型在长法律文档上的掩码预测与实体识别性能不足。 |
| **主要方法** | 在俄语立法文档上继续预训练 Russian ModernBERT，得到 **RuModernBERT-ruLaw**；对比原始模型与适配模型在固定外部集合上的掩码交叉熵与法律实体提取性能。 |
| **关键数据集与实验设置** | 304,382 份立法文档，194,425,905 个语料库 token；1,031 段法院判决外部评测集；5 种掩码实现；输入长度 512 / 2,048 / 8,192 tokens。 |
| **核心结果与指标** | 最大输入长度下，mean masked-token cross-entropy 分别降低 **0.10942** (512)、**0.07052** (2,048)、**0.06604** (8,192) nats；entity-level F1 原始模型 **0.99852**，适配模型 **0.99820**（但 99.95% 测试 span 与训练集表面形式相同，泛化证据有限）。 |
| **创新点** | 系统分析不同长度窗口下法律文档域适应的效果；用可编辑图示与示例清晰解释掩码目标、重叠窗口与实体边界评分。 |
| **局限性** | 实体提取评测中训练-测试表面形式高度重叠，难以证明对未见形式的迁移能力；未隔离远距离上下文贡献。 |

---

### 卡片 6：开源 LLM 法律文档 NLI 评测

| 字段 | 内容 |
|------|------|
| **arXiv 编号** | 2610.06345 |
| **标题** | Breaking Bureaucracy: Evaluating open-source LLMs for legal document review |
| **作者/机构** | Farrukh Baratov, Niki van Stein, Suzan Verberne (Leiden University) |
| **核心问题与动机** | 法律审查流程常涉及机密数据，无法使用云端 API；需要评估开源生成式 LLM 在无标注数据场景下对法律文档进行自然语言推理（NLI）的可行性。 |
| **主要方法** | 在 ContractNLI 与两个 NLI4Wills 数据集上，零样本评测多款开源生成式 LLM；复现监督基线 Span NLI BERT；分析无效输出率、温度稳定性与跨域表现。 |
| **关键数据集与实验设置** | ContractNLI（合同 NLI）、NLI4Wills（遗嘱 NLI）；多款开源生成模型；zero-shot 提示。 |
| **核心结果与指标** | **Gemma-4 26B** 在生成模型中表现最优，accuracy 达到 **81.2%**，在某一指标上甚至超过监督模型；**Qwen-3.6 35B** 在 ContractNLI 与遗嘱领域均表现稳健。整体上，zero-shot 开源生成模型仍无法在 accuracy 上全面超越监督模型，但在无标注数据场景下是可行替代方案。 |
| **创新点** | 首次系统对比多款开源 LLM 与监督基线在法律 NLI 上的零样本表现；引入无效率与温度稳定性分析。 |
| **局限性** | 仅评测英文法律文本；未探索少量样本（few-shot）或检索增强（RAG）的进一步增益；模型版本随开源生态快速迭代。 |

---

### 卡片 7：Agentic 材料科学文献知识提取

| 字段 | 内容 |
|------|------|
| **arXiv 编号** | 2610.06322 |
| **标题** | Agentic schema-guided extraction of materials process knowledge from scientific literature |
| **作者/机构** | Sameer Sadruddin, Jennifer D'Souza |
| **核心问题与动机** | 材料科学文献中的实验知识（流程、化学实体、测量值）以异构形式呈现，且依赖过程特定上下文，传统抽取方法难以聚合。 |
| **主要方法** | **SciKGExtract**：Schema-guided 框架，结合 LLM 抽取、PubChem 化学归一化、Agent-based 评估与精炼，最终集成至知识图谱。 |
| **关键数据集与实验设置** | 176 篇原子层沉积（ALD）论文（ZnO 与 IGZO）；专家标注的全 schema 子集；65 个实验属性 + 155 个定量测量节点的深度嵌套 schema。 |
| **核心结果与指标** | PubChem 归一化提升所有测试模型的 exact-match F1；ZnO 最佳 F1 从直接归一化抽取的 **0.591** 提升至 Agentic 精炼后的 **0.805**；IGZO 最佳 F1 为 **0.344**（多组分超循环工艺难度更高）。 |
| **创新点** | 将化学规范归一化与 Agentic 验证结合，形成互补控制；在深度嵌套 schema 上暴露过程分割与数值分配错误。 |
| **局限性** | IGZO 等多组分复杂工艺抽取性能仍较低；深度嵌套 schema 的错误分析显示过程分割与数值分配是主要瓶颈。 |

---

### 卡片 8：科学文献机制知识基底

| 字段 | 内容 |
|------|------|
| **arXiv 编号** | 2610.06248 |
| **标题** | From Papers to Mechanisms: An Evidence-Grounded Knowledge Substrate for Scientific Language Models |
| **作者/机构** | Qiuhui Chen, Yibo Liu, Tao Dai, Jiafan Lu, Zhenglei Zhou, Weimin Zhong |
| **核心问题与动机** | 科学语言模型通常通过无类型文本块访问文献，破坏了机制性问题所需的功能与证据结构。 |
| **主要方法** | 提出**证据锚定的机制知识基底**，将科学文献组织为溯源链接的证据单元、角色类型实体与有向机制路径；实例化为 **MS³**（Material-Sensor-Signal-System）schema；对比闭卷生成、Web 搜索、Raw-PDF RAG 与 MS³ 检索。 |
| **关键数据集与实验设置** | 13,689 篇论文、131,083 条证据项、26,648 个机制对象；导电纤维柔性传感器领域；10 款语言模型；in-domain 与 coverage-shift QA 基准。 |
| **核心结果与指标** | MS³ 检索在 macro-averaged scientific correctness、citation entailment 与 answer completeness 上均优于 Raw-PDF RAG 与 Web 搜索；证据不足时触发从链接论文的定向检索，而非假设用户已提供正确 PDF。 |
| **创新点** | 机制路径作为科学语言模型的可靠表示层；源修复工作流（source-repair workflow）。 |
| **局限性** | 当前仅在导电纤维传感器领域验证；schema 构建依赖领域专家；跨领域泛化能力待验证。 |

---

### 卡片 9：临床时间线溯源重建

| 字段 | 内容 |
|------|------|
| **arXiv 编号** | 2610.06177 |
| **标题** | Auditable Clinical Timeline Reconstruction with Provenance-Aware Evidence Graphs |
| **作者/机构** | Judith Jeyafreeda Andrew |
| **核心问题与动机** | 患者时间线重建系统只有在保留每条答案背后的提及、记录事实修订方式、并在证据不足时拒绝回答时，才是可审计的。 |
| **主要方法** | 在完全合成语料上测试三种可审计属性；两种溯源感知 Evidence Graph 算子；BioClinicalBERT 门控与零样本 LLM 门控对比；时间版本化溯源图将弃权存储为类型化可查询边。 |
| **关键数据集与实验设置** | 1,000 名患者、3,353 条记录、220 条修订边；6,813 个可回答查询点；482 个再生 gold span。 |
| **核心结果与指标** | Evidence Graph 算子将节点+边数降至 **67%** 和 **63%**（序列化大小 77–78%），同时保留所有答案与提及链接；固定窗口基线对 53.4% 查询点无提示地返回空值。BioClinicalBERT accuracy **93.8%**（marker-free controls 降至 59.3%）；LLM coverage **75.6%**（在其自身模型族判定为不可确定的记录上降至 27.7%）。LLM 引用证据 recall **0.850**、precision **0.864**。 |
| **创新点** | 将可审计性形式化为三属性测试；时间版本化溯源图存储弃权为类型化边；揭示 clean task 存在 0.651 accuracy 的 shortcut。 |
| **局限性** | 结果基于合成数据，非真实临床性能；BERT 的 span head 未在 span 标签上训练，无法定位证据。 |

---

## 三、横向数据对比

### 表 1：模型知识产权保护与溯源方法对比

| 论文 | 场景 | 保护对象 | 核心机制 | 关键指标 | 实验规模 |
|------|------|----------|----------|----------|----------|
| **SBW (2610.08668)** | LLM Agent | 行为决策溯源 | 语义聚类 + 密钥分箱 | ToolBench det. 0.49–0.66 (vs 0.05–0.17); ALFWorld 0.92–0.97 | 5 models, 600 traj./model |
| **MARCO (2610.08316)** | 蛋白质生成 | 模型 IP + 生物安全 | 扩散逆去噪嵌入 + 放射性转移 | Fidelity ↑, Robustness ↑, Transferability ✓ | PGMs 基准（待细化） |
| **Visual Provenance (2610.08137)** | 视觉生成 | 内容溯源 | 两路径（直接生成 vs LLM 代码渲染）框架 | 概念性，无实验 | 无 |
| **EPOR (2610.06603)** | 交错文本流 | 文本源所有权 | 所有权-重建解耦 + 约束解码 | 五轨 mean min-perm WER ↓ 22.3% | UNMIXBENCH 五轨道 |

**解读**：当日模型 IP 保护研究呈现**多模态、多层级**趋势：从文本（EPOR）到 Agent 行为（SBW）再到蛋白质结构（MARCO），溯源对象不断扩展。SBW 的量化对比最为充分，明确展示了语义级水印相对于符号级水印的**数量级优势**（检测率提升约 3–10 倍）。MARCO 填补了生物计算领域的空白，但其具体数值待从正文进一步提取。EPOR 则展示了在**完全观测词证据**前提下，结构化解码比自由生成更可靠的原理。

### 表 2：法律/科学文档理解与知识提取对比

| 论文 | 任务 | 模型/方法 | 数据规模 | 核心指标 | 亮点 |
|------|------|-----------|----------|----------|------|
| **RuModernBERT (2610.06715)** | 法律文档 MLM + NER | ModernBERT 持续预训练 | 304K 文档, 194M tokens | MLM Δ 0.109→0.066 nats; F1 0.99852 vs 0.99820 | 长文档多长度分析 |
| **Breaking Bureaucracy (2610.06345)** | 法律 NLI | 开源 LLM 零样本 | ContractNLI + NLI4Wills | Gemma-4 26B acc 81.2% | 零样本接近监督基线 |
| **SciKGExtract (2610.06322)** | 科学文献 KE | LLM + Agentic 精炼 | 176 ALD 论文 | ZnO F1 0.591→0.805; IGZO 0.344 | 化学归一化 + Agentic 验证 |
| **MS³ (2610.06248)** | 科学 QA / RAG | 机制知识基底 | 13.7K 论文, 131K 证据 | macro correctness ↑, citation entailment ↑ | 源修复工作流 |
| **Clinical Timeline (2610.06177)** | 临床时间线重建 | Evidence Graph + BERT/LLM | 1K patients, 3.4K notes | Graph 压缩 67–63%; BERT acc 93.8% | 可审计性三属性测试 |

**解读**：法律与科学文档 NLP 当日呈现**“长文档 + 结构化 + 可审计”**三大趋势。RuModernBERT 和 Breaking Bureaucracy 分别从预训练适应和零样本推理两端推进法律文本理解；SciKGExtract 与 MS³ 则在科学文献领域探索**从抽取到机制推理**的跃迁。特别值得注意的是，SciKGExtract 的 Agentic 精炼将 F1 从 0.591 提升至 0.805（+36.2%），提示 Agent-based 后处理在复杂 schema 抽取中的巨大潜力。

---

## 四、趋势观察与值得后续追踪的方向

### 4.1 当日趋势

1. **模型知识产权保护成为 cs.CR 当日高频主题**：在 2026-10-06 的 cs.CR 列表中，水印、指纹、溯源类论文占比显著，涵盖 Agent、蛋白质、视觉等多模态场景，反映出大模型商业化背景下 IP 保护的紧迫学术需求。
2. **“去自由生成化”的结构化推理**：SBW 的语义聚类水印、EPOR 的约束解码、SciKGExtract 的 schema-guided 抽取，共同体现了一条从“端到端自由生成”向“结构化、可验证、可审计推理”迁移的方法论趋势。
3. **法律/科学文档 NLP 的域适应与零样本并重**：RuModernBERT 展示持续预训练在长法律文档上的收益，Breaking Bureaucracy 则验证零样本 LLM 已接近监督基线，二者为专利等长技术文档的处理提供了互补路径。

### 4.2 专利场景的直接迁移价值

- **SBW / EPOR**：专利审查中常涉及多源文本（权利要求、说明书、对比文件）的交错比对，EPOR 的词级解混与 SBW 的溯源框架可直接迁移至专利文本溯源与抄袭检测。
- **SciKGExtract / MS³**：专利的核心价值在于“技术方案-技术效果-技术问题”的机制路径，MS³ 的机制知识基底与 SciKGExtract 的 schema-guided 抽取为专利知识图谱构建提供了可直接借鉴的方法论。
- **RuModernBERT / Breaking Bureaucracy**：专利文本兼具法律性与技术性，法律 NLP 的长文档适应与 NLI 能力可直接支撑专利有效性分析、侵权判定等下游任务。

### 4.3 后续追踪方向

1. **直接专利技术论文的窗口追踪**：2026-10-06 当日 arXiv 上直接以 patent 为核心的技术论文缺失，建议持续追踪 arXiv cs.IR / cs.CL / cs.AI 的每日新列表，以及 ACL Anthology 的近期预印本，捕捉专利分类、检索、生成的突破性工作。
2. **SBW 的伪造攻击边界**：作者明确标注 chained replay 仍为开放问题，建议追踪其后续版本或第三方安全审计。
3. **MARCO 的定量评估细节**：待获取正文中的 fidelity（RMSD/TM-score）、robustness（bit-recovery under attack）、radioactivity（pirate model detection rate）具体数值，以评估其在生物计算领域的实际可用性。
4. **SciKGExtract 的跨领域泛化**：当前仅在 ALD 材料验证，追踪其在更广泛材料体系（如电池、催化剂）及专利文本上的适配工作。
5. **EPOR 向专利权利要求解混的迁移**：专利审查中权利要求的从属关系、多独立权利要求的交错引用，与 EPOR 的文本解混问题具有结构相似性，值得追踪后续应用研究。

---

## 五、检索来源与关键词记录

### 5.1 检索来源

| 来源 | 检索方式 | 状态 |
|------|----------|------|
| **arXiv recent/pastweek 列表** | WebFetch: `cs.AI`, `cs.CL`, `cs.CR`, `cs.IR`, `cs.LG` 的 `recent` 与 `pastweek` 页面，按 announcement 日期筛选 Tue, 6 Oct 2026 | **主要来源** |
| **arXiv API** | `export.arxiv.org/api/query` 按 `submittedDate` 与 `all:patent` 查询 | **受限**（返回 429 Too Many Requests） |
| **OpenAlex API** | `api.openalex.org/works` 按 `publication_date:2026-10-06` 交叉检索 `concepts.id:C154945302` (AI)、`C162324750` (NLP)、`fulltext.search:patent` | **辅助核验**（返回 2 篇 AI+patent 法律政策论文，非技术方向） |
| **Semantic Scholar API** | `api.semanticscholar.org/graph/v1/paper/search` 按 `publicationDateOrYear=2026-10-06` 检索 | **受限**（返回 429） |
| **WebSearch** | Google 搜索 `site:arxiv.org "Tue, 6 Oct 2026" patent` 及 `arxiv 2610 patent` 等组合 | **辅助发现** |

### 5.2 检索关键词

**一级关键词（直接）**：
`patent`, `patent classification`, `patent retrieval`, `patent generation`, `patent claim`, `patent text mining`, `patent prior art`, `intellectual property`, `IP protection`, `patentsview`

**二级关键词（扩展）**：
`legal document`, `long document`, `scientific document`, `technical document`, `contract`, `watermark`, `fingerprint`, `model ownership`, `provenance`, `copyright`, `model stealing`, `text unmixing`, `knowledge extraction`, `mechanism extraction`

**三级关键词（方法论关联）**：
`RAG`, `long context`, `domain adaptation`, `zero-shot LLM`, `legal NLI`, `knowledge graph`, `schema-guided extraction`, `evidence graph`, `structured prediction`

### 5.3 当日直接专利论文缺失说明

经上述多源交叉检索，**2026-10-06（announcement 日期）在 arXiv 的 cs.AI、cs.CL、cs.IR、cs.CR、cs.LG 等主要计算机科学分类中，未发现标题或摘要中明确包含 "patent"、"patent classification"、"patent retrieval"、"patent claim generation" 等关键词的技术研究论文**。OpenAlex 同日返回的 2 篇 "AI+patent" 论文均为法律政策方向（"Black Technology: Invention..." 与 "AI Inventorship in Patent Law..."），非 NLP/技术方法论文。

因此，本报告将分析范围合理扩展至**“AI/NLP + 知识产权/溯源/法律文档/科学文献知识提取”**等高度关联方向，并明确标注每篇论文与专利场景的方法论关联。

---

## 附录：论文快速链接

| 编号 | arXiv | PDF |
|------|-------|-----|
| SBW | [2610.08668](https://arxiv.org/abs/2610.08668) | [PDF](https://arxiv.org/pdf/2610.08668) |
| MARCO | [2610.08316](https://arxiv.org/abs/2610.08316) | [PDF](https://arxiv.org/pdf/2610.08316) |
| Visual Provenance | [2610.08137](https://arxiv.org/abs/2610.08137) | [PDF](https://arxiv.org/pdf/2610.08137) |
| EPOR | [2610.06603](https://arxiv.org/abs/2610.06603) | [PDF](https://arxiv.org/pdf/2610.06603) |
| RuModernBERT | [2610.06715](https://arxiv.org/abs/2610.06715) | [PDF](https://arxiv.org/pdf/2610.06715) |
| Breaking Bureaucracy | [2610.06345](https://arxiv.org/abs/2610.06345) | [PDF](https://arxiv.org/pdf/2610.06345) |
| SciKGExtract | [2610.06322](https://arxiv.org/abs/2610.06322) | [PDF](https://arxiv.org/pdf/2610.06322) |
| MS³ | [2610.06248](https://arxiv.org/abs/2610.06248) | [PDF](https://arxiv.org/pdf/2610.06248) |
| Clinical Timeline | [2610.06177](https://arxiv.org/abs/2610.06177) | [PDF](https://arxiv.org/pdf/2610.06177) |
