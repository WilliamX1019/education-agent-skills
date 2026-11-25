---
# AGENT SKILLS STANDARD FIELDS (v2)
name: disciplinary-ai-literacy-sequence-designer
description: "设计跨学科对比教学序列，让学生对比 AI 在不同学科中处理同一类问题的方式，从而基于知识类型建立关于 AI 可靠边界的心理模型。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-literacy/disciplinary-ai-literacy-sequence-designer"
skill_name: "跨学科 AI 素养序列设计器"
domain: "ai-literacy"
version: "1.0"
contributor: "Gareth Manning"
evidence_strength: "moderate"
evidence_sources:
  - "Willingham (2007) — Critical thinking: why is it so hard to teach? (domain-specificity)"
  - "McPeck (1981) — Critical Thinking and Education: domain-specificity of critical thinking"
  - "Bernstein (1999) — Vertical and horizontal discourse: epistemic and social foundations of research contexts"
  - "Maton (2013) — Making semantic waves: a key to cumulative knowledge-building"
  - "Wineburg (2007) — Unnatural and essential: the nature of historical thinking"
input_schema:
  required:
    - field: "target_disciplines"
      type: "string"
      description: "需要对比的两到三个学校学科——例如‘生物与历史’、‘数学、历史与伦理学’、‘物理与文学研究’"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "anchor_question_type"
      type: "string"
      description: "跨学科转译的问题类型——因果类（为什么发生 X？）、评价类（X 有多好/多重要？）、程序类（X 如何运作？）或定义类（什么是 X？）"
    - field: "knowledge_type_focus"
      type: "string"
      description: "重点强调哪种知识结构区分——纵向 vs. 横向话语（Bernstein），或事实性 vs. 阐释性 vs. 态度倾向性"
    - field: "subject_area"
      type: "string"
      description: "若嵌入特定课程单元，所属的课程学科情境"
    - field: "time_available"
      type: "string"
      description: "可用于该教学序列的时长"
output_schema:
  type: "object"
  fields:
    - field: "knowledge_type_analysis"
      type: "object"
      description: "分析每个目标学科如何组织知识——提出什么类型的主张、什么算作证据，以及为什么这能预测 AI 可靠性"
    - field: "anchor_question_set"
      type: "array"
      description: "为每个学科改写的同一类问题——设计得足够平行以便对比，又足够具体以揭示学科差异"
    - field: "comparison_protocol"
      type: "object"
      description: "跨学科对比 AI 输出的结构化协议——观察什么、记录什么以及如何分析模式"
    - field: "ai_reliability_framework"
      type: "object"
      description: "面向学生的、基于知识类型预测 AI 可靠性的框架——整个序列最终建构的可迁移洞见"
    - field: "discussion_guide"
      type: "object"
      description: "全班综合讨论引导指南——从学生发现中建构跨学科 AI 素养框架"
chains_well_with:
  - "kud-knowledge-type-mapper"
  - "curriculum-knowledge-architecture-designer"
  - "ai-output-critical-audit-designer"
teacher_time: "5 分钟"
tags: ["AI-literacy", "disciplinary-thinking", "knowledge-types", "Bernstein", "Willingham", "domain-specificity", "AI-reliability"]
---

# 跨学科 AI 素养序列设计器

## 本技能的作用

设计一个多课时教学序列，让学生系统对比 AI 在不同学科中处理**同一类**问题的方式——从而基于学科所生产的知识类型，建立起“AI 在哪里可靠、在哪里扭曲”的原则性心智模型。核心洞见在于：AI 的可靠性并非均一——它处理已有定论的事实性知识，不同于处理存在争议的阐释性主张；处理序列化的程序知识，也不同于处理涉及价值与判断的倾向性知识。如果一名学生理解为什么 AI 解释光合作用时通常可靠，但在阐释法国大革命起因时却不可靠，他就掌握了可迁移的 AI 素养——而不仅仅是一份“AI 会答错的题目清单”，而是一套预测框架。该序列遵循 Maton（2013）的语义波（semantic wave）逻辑：从具体的学科案例出发，上升到抽象框架（AI 可靠性随知识类型而变化），再落回具体预测（“对于这门学科的这项作业，我预期 AI 的可靠性为 X，因为……”）。本技能借鉴了本技能库既有的知识架构框架：序列化知识（结构化、层级化、累积性——如数学或科学程序）往往能得到 AI 的良好服务；横向知识（多种有效框架并存且互不取代——如史学或文学批评）则是 AI 最容易抹平真实复杂性或对争议立场表现出虚假确定性的地方。

## 实证基础

Willingham（2007）证明批判性思维具有领域特定性——在历史课上能批判性思考的学生，并不会自动把该技能迁移到生物学上，因为不同学科对“好证据”的界定各不相同。这有一个直接的 AI 推论：AI 在某一领域的局限性不能自动推演为在其他领域的表现预测。跨学科 AI 素养需要逐个领域加以评估。McPeck（1981）指出，批判性思维是由学科知识构成的——如果不理解历史学家如何论证，就无法评估历史学科的 AI 输出，正如不理解科学推理就无法评估科学领域的 AI 输出一样。本序列将其操作化：学生用自己的学科知识作为评估工具。Bernstein（1999）对纵向话语（vertical discourse，层级化、累积性的知识结构，新知识涵盖或取代旧知识——如自然科学）与横向话语（horizontal discourse，分段式知识结构，竞争性框架并存——如社会科学与人文学科）的区分，直接预测了 AI 可靠性模式。AI 基于人类知识生产的全分布进行训练——在纵向话语领域，该分布收敛于正确答案；在横向话语领域，它会在竞争性框架间取平均，从而可能抹平它们之间的区别。Maton（2013）的语义波概念提供了教学设计逻辑：序列必须引导学生在具体案例（AI 对特定学科特定主题的回答）与抽象原则（解释该模式的知识类型框架）之间往返，再回到具体预测。Wineburg（2007）将历史思维视为“反直觉的”提供了具体例证：学科专家使用的技能并非天生直觉——必须教授给学生。跨学科 AI 素养同样如此：必须显性教导学生追问“这门学科生产的是哪种知识，这对 AI 的可靠性意味着什么？”

## 输入规范

教师必须提供：
- **目标学科（Target disciplines）：** 要对比的学科。*例如：“生物与历史” / “数学、历史与伦理学” / “物理与文学研究” / “地理与哲学”*
- **学生水平（Student level）：** 年级。*例如：“十一年级，正在为国家考试同时学习多门学科” / “十二年级，A-level 学生”*

可选项（如可用则由上下文引擎注入）：
- **锚定问题类型（Anchor question type）：** 跨学科转译的问题类型
- **知识类型焦点（Knowledge type focus）：** 重点强调哪种知识结构区分
- **学科领域（Subject area）：** 若嵌入在特定课程单元中
- **可用时间（Time available）：** 序列持续时长

## 提示词（Prompt）

```
You are an expert in curriculum theory and AI literacy pedagogy, with knowledge of Willingham's (2007) research on domain-specificity, McPeck's (1981) domain-specific critical thinking, Bernstein's (1999) vertical/horizontal discourse distinction, Maton's (2013) semantic wave concept, and Wineburg's (2007) work on disciplinary thinking. You understand that AI reliability is not uniform — it varies systematically by the type of knowledge a discipline produces. Students who understand this pattern can predict AI reliability, not just recall a list of examples.

CRITICAL PRINCIPLES:
- **The central concept is knowledge type, not subject difficulty.** The question is not "which subjects are harder?" but "what KIND of knowledge does each discipline produce?" Sequential/cumulative/vertical knowledge (where new knowledge builds on and displaces old) tends to be better served by AI than horizontal/interpretive knowledge (where competing frameworks coexist and the same evidence supports multiple conclusions).
- **AI flattens contested claims.** In disciplines with active interpretive debates (history, ethics, literary studies, social science), AI tends to present one interpretation as consensus, or to produce an averaged blend of competing views that misrepresents the genuine state of scholarly debate. Students in these disciplines need specific AI evaluation skills.
- **AI is reliable on the settled parts, unreliable on the contested parts.** Biology has both: the mechanism of photosynthesis is settled (AI is reliable); the ethical implications of genetic engineering are contested (AI less so). History has both: the date of the Battle of Hastings is settled; the causes and long-term significance are contested. The framework must be specific about this distinction, not just "AI is good at science."
- **The comparison drives the learning.** The sequence's power comes from comparing AI's outputs across disciplines side-by-side — not from abstract explanation. Students must run the queries, compare outputs, and build the framework from their findings.
- **The endpoint is a predictive framework.** The sequence should culminate in students being able to say "For this question, in this subject, AI is likely to be [reliable/unreliable] because [knowledge type reasoning]" — a transferable prediction, not just "AI was wrong about the French Revolution."

Your task is to design a disciplinary AI literacy comparison sequence for:

**Target disciplines:** {{target_disciplines}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore fields marked "not provided."

**Anchor question type:** {{anchor_question_type}} — if not provided, use a causal question type ("Why did X happen?") as the anchor — it translates well across disciplines and reveals disciplinary differences clearly.
**Knowledge type focus:** {{knowledge_type_focus}} — if not provided, use Bernstein's (1999) vertical/horizontal distinction as the primary framework.
**Subject area:** {{subject_area}} — if not provided, design as a cross-curricular standalone sequence.
**Time available:** {{time_available}} — if not provided, design for two 45-minute lessons.

Return your output in this exact format:

## Disciplinary AI Literacy Sequence: [Disciplines]

**For:** [Student level]
**Disciplines compared:** [List]
**Anchor question type:** [Type]
**Knowledge type framework:** [Vertical/Horizontal / Factual-Interpretive-Dispositional / other]

### Knowledge Type Analysis

[For each target discipline:]

**[Discipline]:**
- **Knowledge structure:** [Vertical/horizontal; what kind of claims this discipline makes]
- **What counts as evidence here:** [How evidence works in this discipline]
- **Settled vs. contested:** [Examples of settled knowledge and contested knowledge in this discipline]
- **Predicted AI reliability:** [Where AI is likely reliable and where unreliable in this discipline, with reasoning]

### Anchor Question Set

[The same question type reformulated for each discipline — designed to be parallel for comparison]

**The question type:** [e.g. "Why did X happen?"]

**[Discipline 1]:** [Specific question in this discipline]
**[Discipline 2]:** [Specific question in this discipline]
**[Discipline 3]:** [Specific question in this discipline, if applicable]

**Why this question set works for comparison:** [What makes these questions equivalent enough to compare but different enough to reveal disciplinary AI reliability differences]

### Comparison Protocol

**Lesson 1 — Running the queries:**

[Step-by-step instructions for students to run each anchor question, record AI responses, and make initial observations]

**What to record for each discipline:**
- AI's position (if there is one) and certainty language
- Evidence cited (type, specificity, verifiability)
- Whether the AI acknowledges debate or presents its answer as settled
- What the AI does NOT say — what is missing

**Lesson 2 — Pattern analysis:**

[How students compare across disciplines — what to look for, what patterns to identify]

**Comparison questions:**
[4-5 questions that guide students from specific observations to the abstract framework]

### AI Reliability Framework

[The student-facing framework that the sequence builds toward — a way to predict AI reliability based on knowledge type]

**The reliability prediction principle:**
[A concise statement students can apply to future situations]

**The framework in practice:**
[A table or structured summary students can use as a reference]

| Knowledge type | AI tends to... | Because... | Example |
|---|---|---|---|
| [Type 1] | [AI behaviour] | [Reason] | [Example from the sequence] |
| [Type 2] | [AI behaviour] | [Reason] | [Example from the sequence] |

### Discussion Guide

**Activating findings (5 minutes):** [Opening question]
**Building the framework (10 minutes):** [How to move from specific discipline findings to the generalised knowledge-type framework]
**Testing the framework (5 minutes):** [A new discipline or question type students apply the framework to — a transfer test]
**The metacognitive close:** [The question that turns disciplinary AI literacy into a personal practice: "How will you use this framework in your own work?"]

**Self-check before returning output:** Verify that (a) the knowledge type analysis is specific to the stated disciplines, not generic, (b) the anchor questions are genuinely parallel while revealing disciplinary differences, (c) the comparison protocol generates findings students can analyse, not just collect, (d) the reliability framework is a genuine predictive tool, not a list of examples, and (e) the discussion guide includes a transfer test that asks students to apply the framework to a new case.
```

## 示例输出

**情景：** *目标学科：“生物与历史” / 学生水平：“十一年级，同时修读两门 GCSE 课程” / 锚定问题类型：“因果类——为什么会发生 X？” / 知识类型焦点：“纵向话语 vs. 横向话语”*

---

## 跨学科 AI 素养序列：生物与历史

**适用对象：** 十一年级 GCSE 学生
**对比学科：** 生物、历史
**锚定问题类型：** 因果类——“为什么会发生 X？”
**知识类型框架：** Bernstein 纵向/横向话语区分

### 知识类型分析

**生物：**
- **知识结构：** 高度纵向化——知识呈层级式与累积式发展。细胞学说涵盖了早期观察；自然选择进化论涵盖了早期的物种分类。新发现更新或拓展了现有框架，通常不会与旧版本作为同等有效的替代方案并存。
- **什么算作证据：** 对照实验、可重复观察、大数据集统计分析、同行评审。证据依据方法论和可重复性进行评估。
- **已定论 vs. 有争议：** *已定论：* DNA 转录机制、有丝分裂过程、胰岛素在血糖调节中的作用。*有争议：* 特定疾病中遗传因素与表观遗传因素的相对贡献；进化机制的某些细节；饮食与疾病的关系。
- **预测 AI 可靠性：** 在已定论机制（光合作用、细胞呼吸、遗传规律）上可靠性高。在前沿活跃研究领域、群体级统计数据（训练数据可能过时）以及健康主张领域（证据本身混杂，AI 容易过度简化）可靠性较低。

**历史：**
- **知识结构：** 横向化——多种史学阐释框架并存。Fischer 对一战起因的“蓄意论”解读与 Clark 的修正主义解读作为鲜活的学术立场并存；双方都没有像进化论推翻神创论那样“证伪”对方。历史学家生产的是相互竞争而非简单累积的阐释框架。
- **什么算作证据：** 一手史料、档案文献以及具名历史学家的论证，通过溯源（sourcing）、互证（corroboration）与语境化（contextualisation）加以评估。历史中的证据并不像生物学实验那样“证明”主张——而是以不同程度支撑各种阐释。
- **已定论 vs. 有争议：** *已定论：* 日期、事件顺序、文献的存在。*有争议：* 因果关系、历史意义、责任归属、动机阐释、长期后果。历史中几乎所有有意思的问题都是有争议的。
- **预测 AI 可靠性：** 在事实回忆（日期、人名、时间顺序、基本定义）上可靠性高。在因果问题（AI 容易把竞争性阐释抹平成单一自信的答案）、意义评价问题（真正存在争议）以及最新学术成果（训练数据偏向较老文献）上可靠性较低。

### 锚定问题集

**问题类型：** “为什么会发生 X？”

**生物：** “为什么 1 型糖尿病患者需要注射胰岛素？”
**历史：** “为什么德国在第一次世界大战中战败？”

**为何这组问题适合对比：** 两者都是符合 GCSE 水平的因果问题。生物问题有一个已定论的机制性答案（自身免疫破坏胰岛 β 细胞，导致内源性胰岛素分泌丧失）。历史问题则没有定论——历史学家积极争论军事战略、海上封锁、经济崩溃、政治革命与同盟动态各自占多大比重。同一类问题跨越不同知识结构，应当产出不同的 AI 输出——而研究这种差异就能建构起框架。

### 对比协议

**第 1 课时——运行查询（45 分钟）：**

学生两人一组。每组在两个独立对话窗口中，向同一款 AI 工具提出这两个锚定问题。将回应记录在下方追踪表中。

| | 生物问题 | 历史问题 |
|---|---|---|
| AI 的回答（用 2–3 句话概括） | | |
| 确定性语言（绝对肯定 / 有限定 / 非常不确定） | | |
| 引用的证据（类型与具体程度） | | |
| AI 是承认存在争论，还是只呈现一种观点？ | | |
| 文本中**没有**提到什么？ | | |

记录完成后：“通读你的两份 AI 回答。哪一份听起来更自信？哪一份给了你具体证据？哪一份承认人们对此有不同看法？”

**第 2 课时——模式分析（45 分钟）：**

小组间互相交换追踪表对比。全班讨论：

**对比问题：**
- “对于生物问题，AI 的回答大体准确吗？你怎么知道的？”
- “对于历史问题，AI 提到了哪些历史学家或阐释？它说他们有分歧，还是把一种观点当作正确答案？”
- “两者都是‘为什么’的问题。你认为为什么 AI 的回应方式如此不同？”
- “生物学本身的什么特质让 AI 的因果回答更可靠？历史学本身的什么特质让 AI 的因果回答没那么可靠？”
- “如果你正在写论文并直接照搬 AI 的回答——在哪门学科里这样做更危险？为什么？”

### AI 可靠性框架

**可靠性预测原则：**
*在知识已有定论且呈累积性的领域，AI 最可靠。在知识真正存在争议的领域——学者积极争论、多种阐释并存，或正确答案取决于价值判断而非单一证据——AI 最不可靠。*

**实践框架：**

| 知识类型 | AI 往往会…… | 原因在于…… | 序列中的例子 |
|---|---|---|---|
| 已定论/纵向型（机制、程序、既定事实） | 给出准确、自信且可核验的回答 | 训练数据收敛于一致的描述；专家达成共识 | “为什么糖尿病患者需要胰岛素？”——机制准确 |
| 有争议/横向型（因果、意义、阐释） | 听起来自信但抹平争论；把一种立场包装成共识 | 训练数据包含多种立场；AI 产出折中混合版或默认最常见观点 | “为什么德国一战战败？”——很可能漏掉 Fischer 与修正派争论 |
| 前沿或近期领域（最新研究、时事） | 可能过时或不准确 | 训练数据截止时间；快速变化的领域 | 近期临床试验、当前政治事件 |
| 价值负载型（伦理、美学、争议性社会主张） | 产出泛泛回应或“各打五十大板”式框架 | 被训练成回避争议；价值问题在训练数据中没有定论答案 | 基因编辑的伦理问题 |

### 讨论指南

**激活发现（5 分钟）：**
“不看笔记——你更信任哪一份 AI 回答，为什么？生物还是历史？”

**建构框架（10 分钟）：**
“你们的直觉是对的——现在我们来解释它。并不是生物‘更简单’，也不是 AI 在生物上‘更努力’。这两门学科有什么**本质区别**，解释了 AI 可靠性的差异？”[引导指向：知识的类型、专家是否一致、答案取决于什么]

**检验框架（5 分钟）：**
“把这个框架应用到我们今天没讨论过的学科上。如果你问 AI ‘为什么莎士比亚的《麦克白》意义重大？’，你预期它会给出可靠答案吗？那如果问‘计算动能的公式是什么？’呢？用这个框架做出预测——然后我们来验证。”

**元认知收尾：**
“在下次写作业前，问自己：‘我向 AI 询问的是哪种类型的知识？它是已有定论的，还是存在争议的？’这个问题只需 10 秒钟，却应当决定你对答案有多信任。”

---

## 已知局限

1. **纵向/横向的区分并非非黑即白。** Bernstein 的分类是分析性的——在实践中，每门学科都既有已定论知识也有有争议知识。该框架应作为实用启发法来教授，而非死板的分类体系。生物学也有争议领域；历史学也有既定事实。框架预测的是**模式**，而非绝对保证。

2. **不同 AI 模型处理争议性主张的能力各异。** 有些模型经过专门训练，会在阐释性领域承认争论并调低确定性。使用不同 AI 工具可能会得出不同发现。这本身就是一个有价值的发现——讨论为什么不同模型处理这些问题的方式不同，能进一步深化 AI 素养。

3. **该序列要求学生具备足够的学科知识来评估 AI 回答。** 如果学生还没充分学过一战，就无法判断 AI 对德国一战战败原因的叙述是否过度简化。该序列在单元中期或单元末、基础知识到位后使用效果最佳。

4. **跨学科 AI 素养教学法的直接实证证据非常有限。** 知识类型框架（Bernstein、Willingham、Maton）在一般课程设计中证据坚实。将其专门用作预测 AI 可靠性的框架合乎原则但属创新之举——关于教导学生运用知识结构推理来预测 AI 可靠性，目前尚无大量研究。
