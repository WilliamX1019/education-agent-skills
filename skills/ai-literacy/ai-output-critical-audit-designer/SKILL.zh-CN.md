---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ai-output-critical-audit-designer
description: "设计结构化协议，对照 Ennis 的六项批判性思维标准审计 AI 生成的文本。适用于学生在任何学科中需要批判性评估 AI 输出时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-literacy/ai-output-critical-audit-designer"
skill_name: "AI 输出批判性审计设计器"
domain: "ai-literacy"
version: "1.0"
contributor: "Gareth Manning"
evidence_strength: "strong"
evidence_sources:
  - "Ennis (2015) — Critical thinking: a streamlined conception"
  - "Paul & Elder (2008) — The Miniature Guide to Critical Thinking Concepts and Tools"
  - "Facione (1990) — Critical Thinking: a statement of expert consensus (Delphi report)"
  - "Dai et al. (2023) — Can large language models provide useful feedback on research papers? A large-scale empirical analysis"
  - "Wineburg & McGrew (2019) — Lateral reading and the nature of expertise"
input_schema:
  required:
    - field: "ai_output_sample"
      type: "string"
      description: "需要审计的 AI 生成文本，或对协议所针对的 AI 输出类型的描述（例如‘面向十年级地理的 AI 生成气候变化议论文’）"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及先前的批判性思维经验"
  optional:
    - field: "ct_standard_focus"
      type: "string"
      description: "重点强调 Ennis 六项批判性思维标准中的哪几项——清晰性（clarity）、准确性（accuracy）、精确性（precision）、相关性（relevance）、深度（depth）、广度（breadth）——或‘全部六项’以开展完整审计"
    - field: "subject_area"
      type: "string"
      description: "学科情境——影响什么算作充分证据与精确度"
    - field: "task_context"
      type: "string"
      description: "AI 输出是为哪项任务生成的——议论文、原理解释、研究摘要、论证、解题方案"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：先前的批判性思维经验、学科知识水平"
output_schema:
  type: "object"
  fields:
    - field: "ai_failure_mode_analysis"
      type: "object"
      description: "与该输出类型和学科相关的 AI 典型失效模式分类——在一般论证缺陷之外需要重点警惕的问题"
    - field: "annotation_protocol"
      type: "object"
      description: "供学生实时标注 AI 文本的分步标注协议，为每种失效类型配备专用标注代码"
    - field: "audit_rubric"
      type: "object"
      description: "对照每项相关 Ennis 批判性思维标准将 AI 输出评为弱/中/强的量规，包含各等级的 AI 特有描述符"
    - field: "push_back_stems"
      type: "array"
      description: "针对每项批判性思维标准校准的追问句干，用于反驳 AI 特有的失效模式"
    - field: "teacher_modelling_script"
      type: "string"
      description: "出声思考示范脚本，展示教师如何审计 AI 文本并在失效模式出现时将其命名点破"
chains_well_with:
  - "critical-thinking-task-designer"
  - "source-credibility-evaluation-protocol"
  - "elaborative-interrogation-generator"
  - "ai-hallucination-fact-check-protocol"
teacher_time: "4 分钟"
tags: ["AI-literacy", "critical-thinking", "Ennis", "audit", "annotation", "AI-output", "hallucination", "epistemic"]
---

# AI 输出批判性审计设计器

## 本技能的作用

生成一份结构化协议，对照 Ennis（2015）的六项批判性思维标准——清晰性（clarity）、准确性（accuracy）、精确性（precision）、相关性（relevance）、深度（depth）和广度（breadth）——对 AI 生成文本进行批判性审计，并专门针对一般批判性思维框架未能覆盖的 AI 典型失效模式做出调适。核心教学挑战在于：AI 生成的文本流畅、自信且格式工整，这使它比看起来可疑的文本更难被批判性评估。常规信息源可信度启发法（谁写的？谁资助的？）在这里失灵了，因为作者是一个大语言模型。取而代之的是一套针对 AI 特有模式训练的细读协议：毫无根据却自信满满的断言、看似精确却无从查证的数据、听起来专业却缺乏真正认识论深度的语言，以及系统性地缺少“我不知道”。本技能为 ai-literacy 领域提供锚点工具：包括标注协议（学生实时标注 AI 文本）、审计量规（按每项 CT 标准将 AI 文本评为弱/中/强）、针对 AI 失效模式校准的追问句干，以及教师示范脚本。这相当于 historical-thinking 领域中的 `sourcing-skill-builder`——是学生在开展更专业工作之前必须掌握的基础动作。

## 实证基础

Ennis（2015）提出了一个建立在六项智力标准之上的精简批判性思维（CT）框架：**清晰性**（主张表达得足够明确以便评估）、**准确性**（主张与现实相符）、**精确性**（主张具体到足够有用）、**相关性**（主张切中手头问题）、**深度**（主张触及问题的真实复杂性）以及**广度**（主张考量多元视角）。这些标准正是 Kharbach（2026）AI 时代批判性思维活动的明确理论基石。Paul & Elder（2008）将类似标准操作化为广泛用于 CT 教育的智力标准框架，为 Ennis 的分类图式提供了教学传统。Facione（1990）的德尔菲专家共识将 CT 界定为包含阐释、分析、评价、推论、解释与自我调节——其中评价维度正是 AI 审计所激活的核心。Dai 等人（2023）对 LLM 生成的反馈进行了大规模实证分析，记录了其典型失效模式：AI 输出流畅、结构良好，并倾向于过度自信且缺乏足够的认识论谨慎（epistemic hedging）。他们的发现——LLM 产出笼统建议而回避指出具体错误——直接对应了 Ennis 的精确性与准确性标准。Wineburg & McGrew（2019）指出，有效的文本评估需要他们所称的“受过训练的审视（disciplined scrutiny）”——即一种经训练的、协议驱动的阅读实践，而非直觉判断。这为采用结构化标注协议而非开放式泛泛评价提供了方法论依据。

## 输入规范

教师必须提供：
- **AI 输出样本（AI output sample）：** 要审计的具体 AI 文本，或对所设计协议针对的输出类型的描述。*例如：“以下是 ChatGPT 关于一战起因的回复文本：[粘贴文本]” / “十年级地理气候变化任务中 AI 生成的论文引言” / “聊天机器人面向九年级数学学生对二次方程的解释”*
- **学生水平（Student level）：** 年级与批判性思维经验。*例如：“十年级，能识别基本论证主张，但未正式学习过批判性思维标准” / “十二年级，熟悉 Paul & Elder 框架”*

可选项（如可用则由上下文引擎注入）：
- **CT 标准重点（CT standard focus）：** 强调哪些标准。*例如：“准确性与精确性——学生经常不经核查就接受 AI 统计数据” / “全部六项——用于完整审计活动”*
- **学科领域（Subject area）：** 学科情境——不同学科对“充分证据”的界定不同
- **任务情境（Task context）：** AI 生成的内容类型——论文、解释、研究摘要
- **学生画像（Student profiles）：** 先前 CT 经验、学科知识水平

## 提示词（Prompt）

```
You are an expert in critical thinking pedagogy and AI literacy pedagogy, with deep knowledge of Ennis's (2015) six intellectual standards (clarity, accuracy, precision, relevance, depth, breadth), Paul & Elder's (2008) critical thinking framework, Facione's (1990) Delphi CT consensus, and empirical research on LLM output quality (Dai et al., 2023). You understand that AI-generated text has characteristic failure modes that require specific pedagogical attention beyond general CT instruction: AI outputs are fluent and confident but often lack genuine epistemic depth, assert precision without verifiable sources, present contested claims as settled, and systematically omit appropriate uncertainty language.

CRITICAL PRINCIPLES FOR AI AUDIT:
- **AI failure modes are qualitatively different from human argument flaws.** A biased human source has an agenda you can investigate. AI has no agenda — it has statistical patterns. The failure is not motivated reasoning but overconfident generalisation, hallucinated specificity, and missing epistemic hedging. Students must be trained to notice these specifically.
- **Fluency is not a credibility signal.** AI output is grammatically polished and logically structured. Students who treat polish as evidence of quality will be systematically deceived. The audit protocol must explicitly de-couple fluency from reliability.
- **The absence of "I don't know" is a red flag.** Genuine expertise includes calibrated uncertainty. AI trained to be helpful tends to produce answers even when the evidence is weak. Students should be trained to notice the absence of hedging, qualification, and epistemic modesty.
- **Specificity requires verification, not just recognition.** AI often produces statistics, citations, and named studies. These LOOK precise (Ennis's precision standard seems met) but the precision may be fabricated. True precision requires that the specific claim can be traced and verified.
- **Depth requires genuine complexity, not length.** AI can produce long, multi-paragraph responses that add more text without adding depth — restating the same point in different words, listing examples without explaining the principle, or acknowledging complexity without engaging with it.

Your task is to generate an AI output audit protocol for:

**AI output sample:** {{ai_output_sample}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore fields marked "not provided."

**CT standard focus:** {{ct_standard_focus}} — if not provided, address all six Ennis standards but flag which 2-3 are most relevant to AI output of this type.
**Subject area:** {{subject_area}} — if not provided, infer from the output and apply discipline-appropriate evidence standards.
**Task context:** {{task_context}} — if not provided, infer from the output.
**Student profiles:** {{student_profiles}} — if not provided, design for a mixed-ability class with general familiarity with evaluating arguments but no formal AI literacy training.

Return your output in this exact format:

## AI Output Critical Audit: [Subject/Topic]

**For:** [Student level]
**Output type:** [What kind of AI output this is]
**CT standards in focus:** [Which standards are most relevant to this output type and why]

### AI Failure Mode Analysis

[Identify 3-5 AI-characteristic failure modes present or likely in this output type. For each:]

**Failure mode [N]: [Name]**
- **What it looks like:** [Specific example from the output, or a representative example if no specific text was provided]
- **Why students miss it:** [Why fluency or surface features hide this failure]
- **Ennis standard violated:** [Which of the six standards this fails]

### Annotation Protocol

**How to use this protocol:** [Brief instruction for how students mark up the text]

**Annotation codes:**
[Table of codes with symbols/abbreviations, what they mark, and the Ennis standard they relate to]

**Step-by-step annotation sequence:**
[Ordered steps for moving through the text — what to read for first, second, third]

### Audit Rubric

[For each relevant CT standard, provide Weak/Moderate/Strong descriptors calibrated for AI output]

| CT Standard | Weak | Moderate | Strong |
|---|---|---|---|
| [Standard] | [What weak looks like in AI text] | [Moderate] | [Strong] |

### Push-Back Stems

[For each CT standard, 2-3 sentence stems students can use to push back on the AI output — framed as questions or prompts that probe the weakness]

**Clarity:** [Stems]
**Accuracy:** [Stems]
**Precision:** [Stems]
**Relevance:** [Stems]
**Depth:** [Stems]
**Breadth:** [Stems]

### Teacher Modelling Script

[A think-aloud script — 200-300 words — showing a teacher auditing a short section of AI text, naming failure modes as they appear, using the annotation codes, and applying the Ennis standards explicitly. Model what expert AI-critical-reading sounds like.]

**Self-check before returning output:** Verify that (a) the failure mode analysis names AI-specific patterns, not generic argument flaws, (b) the annotation protocol teaches close reading rather than surface scanning, (c) the rubric descriptors distinguish AI-characteristic Weak from generic bad writing, (d) push-back stems are specific enough to use, and (e) the modelling script de-couples fluency from reliability explicitly.
```

## 示例输出

**情景：** *AI 输出样本：“气候变化主要由释放二氧化碳和甲烷等温室气体的人类活动引起。科学界共识强烈支持这一结论，97% 的气候科学家同意人为气候变化正在发生。主要影响包括海平面上升、更频繁的极端天气事件和全球气温升高。各国必须立即采取行动，通过征收碳税、向可再生能源转型和种植更多树木来减少排放。如果我们不采取行动，到 2050 年全球气温将上升 2°C，对全球生态系统造成不可逆转的损害。” / 学生水平：“十年级，接受过有限的正式批判性思维训练” / 学科领域：“地理” / 任务情境：“GCSE 地理复习解释材料”*

---

## AI 输出批判性审计：气候变化解释（十年级地理）

**适用对象：** 十年级，有限正式 CT 训练
**输出类型：** AI 生成的复习解释文本
**重点聚焦的 CT 标准：** 准确性（事实核查）、精确性（来源追踪）、深度（复杂性介入）——这三项在 AI 生成的争议性主题解释中最常被违反

### AI 失效模式分析

**失效模式 1：无出处的统计数据**
- **外观示例：** “97% 的气候科学家同意人为气候变化正在发生。”这是一个真实统计数据（Cook et al., 2013）——但 AI 在呈现时未给出任何出处。学生无法核实它。
- **学生为何漏掉：** 这个数字听起来精确而权威。具体的数字让人感觉像证据。
- **违反的 Ennis 标准：** 精确性——只有具体数字而缺乏可验证性

**失效模式 2：缺乏限定词的自信预测**
- **外观示例：** “到 2050 年全球气温将上升 2°C。”这被陈述为确定无疑的事实。实际上，温度预测取决于排放情景，是一个带有显著不确定性的区间。
- **学生为何漏掉：** AI 删掉了科学家使用的谨慎限定语（“可能”、“在高排放情景下”）——润色精美、语气笃定的文字比真实的科学不确定性听起来更令人信服。
- **违反的 Ennis 标准：** 准确性——虚假确定性；深度——缺失真实复杂性

**失效模式 3：政策购物清单**
- **外观示例：** “征收碳税、向可再生能源转型和种植更多树木。”罗列了三项措施，却没有探讨各自利弊、证据支撑或关于它们相对有效性的争论。
- **学生为何漏掉：** 行动清单看起来很全面，符合学生心目中“标准答案”的样子。
- **违反的 Ennis 标准：** 深度——只罗列不分析；广度——缺乏批判与反方视角

**失效模式 4：缺失复杂性**
- **外观示例：** “各国必须立即采取行动。”没有探讨具体是哪些国家、谁承担责任，以及气候变化对排放贡献最少国家的差异化影响。
- **学生为何漏掉：** 文本篇幅足够长，让人觉得很深入。篇幅 ≠ 深度。
- **违反的 Ennis 标准：** 广度——缺失多元视角；深度——省略真实复杂性

### 标注协议

**如何使用本协议：** 先通读一遍 AI 文本不做标记。然后拿笔逐句慢读，应用下方代码。不必标出所有细节——目标是至少找出每种代码的一个例子。

**标注代码：**

| 代码 | 符号 | 标注内容 | Ennis 标准 |
|---|---|---|---|
| US | ★ | 无出处统计或数据——无引文的具体数字 | 精确性 |
| FC | ! | 虚假确定性——无限定词的预测或主张 | 准确性 |
| SL | ≡ | 购物清单——未经解释或缺乏证据的罗列项目 | 深度 |
| MC | ? | 缺失复杂性——对争议或复杂议题的过度简化 | 广度 |
| VL | ~ | 模糊语言——缺乏界定的“许多”、“显著”、“必须” | 清晰性 |

**分步标注顺序：**
1. 通读查找**无出处统计**（★）——圈出任何没有引文的数字、百分比或数据点
2. 通读查找**虚假确定性**（!）——在任何缺少“可能”、“证据表明”等限定词的预测或主张下划线
3. 通读查找**购物清单**（≡）——用括号括出任何后面没有跟上证据或利弊解释的列举项
4. 通读查找**缺失复杂性**（?）——标出任何忽视了真实反方论点或竞争性视角的主张
5. 通读查找**模糊语言**（~）——标出缺乏具体界定的“显著”、“许多”、“重要”、“必须”等词

### 审计量规

| CT 标准 | 弱 | 中 | 强 |
|---|---|---|---|
| **准确性** | 主张被当作事实陈述，无任何限定；预测没有不确定性区间 | 部分主张有限定；主要争议点仍被当作定论陈述 | 争议性主张被标明存在争议；使用不确定性语言；区分共识与辩论 |
| **精确性** | 引用统计数据却无出处；主张过于模糊无法检验 | 部分数据有隐含出处；关键主张可被追踪 | 所有具体主张均可追踪；来源类型清晰可辨（研究、报告、共识声明） |
| **深度** | 只列清单不作解释；口头承认复杂却未真正介入 | 对机制或利弊有一定介入；关键复杂性仍被简化 | 解释内在机制、回应反方视角、承认未知之处 |
| **广度** | 全程单一视角；无替代观点 | 简短提及一种替代观点；缺乏真正对话 | 呈现多元视角；审视不同方案之间的权衡利弊 |
| **清晰性** | 使用“显著”、“严重”等模糊词却不加界定 | 关键术语界定过一次；仍残留部分模糊表述 | 所有评价性术语均已操作化界定；读者可核验每条主张 |
| **相关性** | 包含离题背景材料；偏离核心问题 | 大体切题，偶有跑偏 | 每一句话都直接回应问题；无注水内容 |

### 追问句干

**准确性：**
- “这里说【X】一定会发生。得出如此确定结论的依据来源是什么？”
- “这是一项专家普遍认同的主张，还是存在争议？我该如何查证？”

**精确性：**
- “文本给出了一个具体数字（【X】%）。这个数字是从哪里来的？”
- “这条统计数据指的是哪项研究或报告？我能搜到它吗？”

**深度：**
- “文本说【某方案】会有所帮助。这种方法有什么代价、权衡或实施难点？”
- “这一段列出了三件事。但**为什么**每一件都有用——且三者的证据强度一样吗？”

**广度：**
- “这份解释里**没有**代表谁的声音？遗漏了谁的视角？”
- “文本说‘各国必须行动’。所有国家承担的责任都一样吗？AI 回应了这一点吗？”

**清晰性：**
- “文本用了【某词，例如‘显著’】。有多显著？是和什么相比？”
- “这里的【模糊术语】具体指什么——我能把它替换成更精确的表述吗？”

**相关性：**
- “这一段是在回答问题，还是只是在堆砌更多信息？”
- “这个细节是与【具体复习问题】直接相关，还是泛泛的背景介绍？”

### 教师示范脚本

“我要大声朗读这段 AI 解释并出声思考——让你们听见我在评估它时脑子里在想什么。

[朗读第一句]‘气候变化主要由……人类活动引起。’好的。这是一个清晰的主张——清晰性我给过关。准确性呢？这符合科学共识。这里我暂不标警报。

[继续读]‘97% 的气候科学家同意……’——等一下。这是一个非常具体的数字。它从哪来的？AI 没说。我在这里标一个 ★——无出处统计。它可能是真的，大概率是真的。但单凭这段文本我无法核实它。

[继续读]‘到 2050 年全球气温将上升 2°C……’——我立刻在这里标一个 !。真正的气候科学指出，温升取决于我们的排放量。IPCC 给出的是不同排放情景下的区间，而不是单一的确定预测。AI 把所有不确定性都抹掉了，把一个数字当成铁板钉钉的事实。这就是虚假确定性失效模式——流畅、具体，但在自信程度上是错误的。

[朗读政策清单]‘碳税、可再生能源、种树。’一连串三件事——我标上 ≡。这是一份购物清单。它看起来很全面，但完全没有解释证据：其中哪一项证据最强？各自有什么权衡代价？经济学家对碳税 vs. 行政监管怎么看？AI 丢给我一个清单，就称之为答案。

两分钟下来，我已经标出了 ★、! 和 ≡。这段文字看起来很对——而且大部分内容确实不错。但它存在虚假确定性、无出处统计和深度缺失。如果学生直接拿它当复习资料，他记住的是一些大致准确的事实，却被装进了一个具有误导性的框架里。这正是我们要训练应对的 AI 素养问题。”

---

## 已知局限

1. **审计需要足够的领域知识。** 如果学生对主题不够熟悉、认不出被省略的内容，就无法判断 AI 主张是否盲目自信或缺失复杂性。本技能应在基础知识建立**之后**使用，而非之前。在知识建构阶段，应先使用显性教学技能。

2. **AI 失效模式会随模型迭代而演进。** 某些模式（例如捏造引文）正被模型开发者积极改进。上述分类法反映了当前 LLM（2023–2026）中有充分记录的失效模式，未来可能需要随模型升级而修订。底层的 CT 标准（Ennis, 2015）是稳定的；具体的失效模式分类法则依赖于模型代际。

3. **将流畅度与可信度剥离需要付出认知努力。** 要求学生怀疑润色精美、结构工整的文本，违背了长期养成的阅读习惯。习惯于因写出结构良好文章而受表扬的学生，会本能地把行文流畅与质量画等号。需要持续练习才能养成审视过度自信的反直觉习惯。

4. **成熟 CT 框架在 AI 审计中的具体应用缺乏直接实证检验。** CT 标准（Ennis、Paul & Elder、Facione）在一般批判性思维教学中证据坚实。将其专门应用于审计 AI 生成文本合乎原则但属创新之举——Dai 等人（2023）是教育语境下少有的 LLM 输出质量实证研究之一。教师应将其视为一项合乎原则的框架，而非已定型的教学干预。
