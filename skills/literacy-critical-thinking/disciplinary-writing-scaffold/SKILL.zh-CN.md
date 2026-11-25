---
# AGENT SKILLS STANDARD FIELDS (v2)
name: disciplinary-writing-scaffold
description: "创建教授特定学术学科体裁规范的写作支架。适用于学生撰写实验报告、历史论文或其他特定学科文本类型时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "literacy-critical-thinking/disciplinary-writing-scaffold"
skill_name: "学科写作支架"
domain: "literacy-critical-thinking"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Halliday (1993) — Towards a language-based theory of learning"
  - "Martin & Rose (2008) — Genre Relations: mapping culture"
  - "Christie & Derewianka (2008) — School Discourse: learning to write across the years of schooling"
  - "Graham & Perin (2007) — Writing Next: effective strategies to improve writing of adolescents"
  - "Shanahan & Shanahan (2008) — Teaching disciplinary literacy to adolescents"
input_schema:
  required:
    - field: "writing_task"
      type: "string"
      description: "学生必须完成的具体写作任务"
    - field: "discipline"
      type: "string"
      description: "学科领域——例如科学、历史、英国文学、数学、地理"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及当前在该学科的写作能力"
  optional:
    - field: "genre"
      type: "string"
      description: "具体体裁——例如实验报告、历史解释、文学分析、数学证明、地理案例研究"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：写作水平、语言水平、EAL 状态"
    - field: "assessment_criteria"
      type: "string"
      description: "该写作将依据的评分标准或量规"
    - field: "model_text"
      type: "string"
      description: "学生已经看过的范例或范文"
output_schema:
  type: "object"
  fields:
    - field: "scaffold"
      type: "object"
      description: "结构化写作支架，包含特定学科的板块、各板块目的以及语言特征"
    - field: "language_toolkit"
      type: "object"
      description: "特定学科的词汇、句首提示、连接词以及模糊限制语（hedging language）"
    - field: "annotated_model"
      type: "string"
      description: "展示支架实际运用的简短批注范例，标出特定学科语言特征"
    - field: "differentiation"
      type: "object"
      description: "支持与拓展调整方案"
chains_well_with:
  - "argument-structure-scaffold-generator"
  - "vocabulary-tiering-tool"
  - "academic-language-sentence-frame-generator"
  - "text-complexity-analyser"
  - "pedagogical-content-knowledge-developer"
  - "critical-thinking-task-designer"
teacher_time: "3 分钟"
tags: ["disciplinary-literacy", "writing", "genre-pedagogy", "scaffold", "academic-language"]
---

# 学科写作支架

## 本技能的作用

为特定学科写作体裁——实验报告、历史论证、文学分析、数学解释、地理案例研究——生成一个反映该学科真实规范的支架，而不是套用千篇一律的“通用作文结构”。每个学科都有通过写作建构知识的独特方式：科学家通过证据报告并解释现象；历史学家通过阐释并围绕重要性展开论证；文学批评家分析作者工艺与效果。一个长得像英语议论文的科学支架就是失败的。输出包括结构支架、特定学科语言工具箱（词汇、句首提示、模糊限制语、连接词）、批注范例以及分层教学选项。AI 在此尤为有价值，因为大多数教师是本学科内容的专家，却未必是其写作规范的专家——他们知道优秀的学科写作长什么样，却往往难以把其中的语言特征显性化、可教化。

## 循证基础

Halliday (1993) 与系统功能语言学传统确立了“语言不是内容的中立容器”——不同学科之所以以不同方式使用语言，是因为它们以不同方式建构知识。科学写作使用名词化（将过程转化为事物："the water evaporated" 变成 "evaporation"）、被动语态与模糊限制语，因为这些特征服务于科学目的（客观性、精确性、审慎性）。历史写作使用评价性语言、因果连接词与限定表达，因为历史学家建构关于重要性的论证。Martin & Rose (2008) 绘制了学校各学科使用的体裁图谱，表明每个学科都要求学生用多种具有独特结构与语言特征的体裁写作。Christie & Derewianka (2008) 证明，学生在学科体裁中写作的能力随学段发展而逐步形成，需要显性教学——学生不会仅仅通过阅读范例就自然习得科学或历史写作的语言特征。Graham & Perin (2007) 发现显性教授文本结构是最高效的写作干预措施之一（效应量 0.82）。Shanahan & Shanahan (2008) 主张，随着学生年级升高，读写教学必须越来越具学科针对性——通用阅读与写作策略不足以支撑高阶学科学习。

## 输入模式

教师必须提供：
- **Writing task（写作任务）：** 学生必须写什么。*例如："Write a conclusion for the enzyme experiment" / "Explain why the Weimar Republic failed" / "Analyse how Shakespeare presents Lady Macbeth in Act 1, Scene 5" / "Explain why your answer to the problem is correct"*
- **Discipline（学科）：** 学科领域。*例如："Science (Biology)" / "History" / "English Literature" / "Mathematics"*
- **Student level（学生水平）：** 年级与写作能力。*例如："Year 8, can write in paragraphs but their science writing reads like storytelling — 'we put the enzyme in and then it fizzed'"*

可选（如上下文引擎可用则自动注入）：
- **Genre（体裁）：** 具体体裁（如已知）
- **Student profiles（学生档案）：** 写作水平、语言水平、EAL 状态
- **Assessment criteria（评估标准）：** 评分标准或量规
- **Model text（范文）：** 学生已经看过的范例

## Prompt

```
You are an expert in disciplinary literacy and genre pedagogy, with deep knowledge of systemic functional linguistics (Halliday, 1993; Martin & Rose, 2008), Christie & Derewianka's (2008) research on school writing development, and Shanahan & Shanahan's (2008) work on disciplinary literacy. You understand that writing is not a generic skill — each discipline constructs knowledge through writing differently, and students must be taught the specific structural and linguistic features of their discipline's genres.

Your task is to generate a disciplinary writing scaffold for:

**Writing task:** {{writing_task}}
**Discipline:** {{discipline}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Genre:** {{genre}} — if not provided, identify the most appropriate disciplinary genre for this task (e.g., a science explanation, a historical argument, a literary analysis) and name it explicitly.
**Student profiles:** {{student_profiles}} — if not provided, design for a mixed-ability class that can write in paragraphs but hasn't been explicitly taught the conventions of this disciplinary genre.
**Assessment criteria:** {{assessment_criteria}} — if not provided, infer the likely assessment focus from the task and discipline.
**Model text:** {{model_text}} — if provided, use it as the basis for the annotated model. If not, generate a brief example.

Apply these evidence-based principles:

1. **Discipline-specific structure (Martin & Rose, 2008):**
   - Each discipline has characteristic genres with specific structural stages. Use the actual genre structure, not a generic essay template.
   - Science explanation: Phenomenon → Explanation sequence → Summary
   - Science lab report: Aim → Hypothesis → Method → Results → Discussion → Conclusion
   - Historical argument: Context → Thesis → Argument paragraphs (evidence + analysis) → Counter-argument → Judgement
   - Literary analysis: Context → Thesis → Close reading paragraphs (quotation + analysis of technique + effect) → Conclusion
   - Mathematical explanation: Statement → Working/proof → Justification → Conclusion
   - Geographical case study: Location/context → Description → Explanation → Evaluation/implications
   - Name the genre explicitly and explain its purpose: "In science, an explanation text answers HOW or WHY something happens."

2. **Discipline-specific language features (Halliday, 1993; Christie & Derewianka, 2008):**
   - Identify the key language features of this discipline's genre and teach them explicitly:
     - Science: nominalisation, passive voice, hedging ("suggests," "indicates"), technical vocabulary, causal connectives ("because," "as a result," "this leads to")
     - History: evaluative language ("significant," "decisive"), temporal connectives, qualification ("to some extent"), attribution ("According to...")
     - English Literature: analytical verbs ("suggests," "conveys," "implies"), language about technique ("metaphor," "juxtaposition"), effect language ("This creates a sense of...")
     - Mathematics: logical connectives ("therefore," "since," "if...then"), precision language, conditional statements
   - Provide these as a language toolkit students can draw from.

3. **Make the PURPOSE of each section explicit (Hillocks, 2011; Graham & Perin, 2007):**
   - Each section of the scaffold should explain WHY it's there — what work it does in the discipline.
   - "In a science conclusion, you explain what the results MEAN — not what happened (that's in your results section), but what it tells us about the scientific concept."

4. **Sentence starters that model disciplinary thinking (Shanahan & Shanahan, 2008):**
   - Sentence starters should model how experts in the discipline think and write.
   - Science: "The data suggests that..." / "This supports the hypothesis because..."
   - History: "The most significant factor was... because..." / "While [counter-argument], the evidence indicates..."
   - English: "Shakespeare uses [technique] to suggest..." / "The word '[quotation]' creates a sense of..."
   - These are NOT generic writing starters — they encode disciplinary reasoning.

Return your output in this exact format:

## Disciplinary Writing Scaffold: [Genre] in [Discipline]

**For:** [Student level]
**Task:** [The writing task]
**Genre:** [Named genre with one-sentence explanation of its purpose in the discipline]

### The Scaffold

[Complete structural scaffold with labelled sections, purpose of each section, guiding prompts, and discipline-specific sentence starters]

### Language Toolkit

**Key vocabulary:** [Discipline-specific terms needed for this task]
**Sentence starters:** [Organised by section of the scaffold]
**Connectives:** [Discipline-appropriate linking language]
**Hedging/qualifying language:** [If relevant to the discipline — especially important in science and history]

### Annotated Model

[A brief annotated example — one section or paragraph — showing the scaffold in use with disciplinary language features labelled]

### Differentiation

**Support:** [How to modify for weaker writers or EAL students — additional scaffolding, reduced sections, sentence frames]
**Extension:** [How to challenge stronger writers — removing scaffolds, requiring more sophisticated language features]

**Self-check before returning output:** Verify that (a) the scaffold reflects the actual genre structure of the discipline, not a generic essay template, (b) language features are discipline-specific, (c) sentence starters model disciplinary thinking, not just grammatical structure, (d) each section explains its purpose within the discipline, (e) the annotated model demonstrates realistic student-level writing, and (f) the scaffold would look different if the discipline changed — it is genuinely discipline-specific.
```

## 示例输出

**场景：** *Writing task: "Write a conclusion for your enzyme experiment (investigating the effect of temperature on amylase activity)" / Discipline: "Science (Biology)" / Student level: "Year 8, can write in paragraphs but their science writing reads like a narrative — 'we heated it up and it went faster then we heated it more and it stopped working'"*

---

## 学科写作支架：科学实验结论

**适用对象：** 八年级科学（生物）
**任务：** 为酶实验（温度对淀粉酶活性的影响）撰写结论
**体裁：** 实验结论——实验报告中的一个板块，用于从科学概念的角度解释结果“意味着什么”。结论回答的是“这告诉了我们什么？”，而不是“我们做了什么？”。

### 写作支架

**第 1 部分：陈述发现（2–3 句）**
*目的：清晰且精确地告诉读者你的结果显示了什么——规律或趋势。这“不是”对你操作过程的描述，而是对你“发现”之物的陈述。*

引导提示：
- 结果的总体趋势是什么？
- 淀粉酶在哪个温度下反应最快？
- 在高于和低于该温度时发生了什么？

句首提示：
- "The results show that..."
- "As temperature increased from [X]°C to [Y]°C, the rate of amylase activity..."
- "The optimum temperature for amylase was approximately [X]°C, as shown by..."

**不要这样写：** "First we set up the test tubes and then we added the amylase..."——那是你的实验方法，不是你的结论。

---

**第 2 部分：解释科学原理（3–4 句）**
*目的：运用你的科学知识解释“为什么”得到这些结果。这是结论中最重要的部分——它将你的结果与生物学原理连接起来。任何人都能描述发生了什么；科学家解释为什么。*

引导提示：
- 为什么温度升高（直至最适温度）时酶活性会增强？
- 为什么在极高温度下酶活性会下降？
- 酶的结构发生了什么变化？

句首提示：
- "This can be explained by..."
- "At lower temperatures, the enzyme molecules had less kinetic energy, which means..."
- "At temperatures above [X]°C, the enzyme became denatured, meaning..."
- "The active site changed shape, so the substrate could no longer..."

**核心科学词汇：** kinetic energy（动能）、collisions（碰撞）、active site（活性位点）、substrate（底物）、denatured（变性）、optimum temperature（最适温度）。使用这些术语——它们表明你理解了科学原理，而不仅仅是做完了实验。

---

**第 3 部分：评估——联系你的假设（1–2 句）**
*目的：说明你的结果支持还是反驳了你的假设，以及原因。科学家总是将发现与预测对照检验。*

句首提示：
- "These results support / do not support the hypothesis that..."
- "The hypothesis predicted that... and the results confirm / contradict this because..."

---

**第 4 部分：承认局限性（1–2 句）**
*目的：指出可能影响结果的一个因素。这不是承认失败——而是展现科学思维。真正的科学家总是会考虑什么可能影响了数据。*

句首提示：
- "However, the results may have been affected by..."
- "A limitation of this experiment was..."
- "To improve reliability, the experiment could be repeated with..."

### 语言工具箱

**核心词汇：** enzyme, substrate, active site, denatured, optimum temperature, kinetic energy, rate of reaction, collisions, lock-and-key model

**按板块分类的句首提示：**
| 板块 | 句首提示 |
|---------|----------|
| 发现 | "The results show that..." / "The data indicates that..." / "The rate of reaction was highest at..." |
| 解释 | "This can be explained by..." / "This occurred because..." / "At the molecular level..." |
| 假设关联 | "These results support the hypothesis that..." / "This is consistent with the prediction that..." |
| 局限性 | "However, a source of error may have been..." / "The reliability could be improved by..." |

**因果连接词：** because, therefore, as a result, this means that, consequently, due to, which leads to, this suggests that

**模糊限制语（Hedging language）：** suggests, indicates, may have, it is likely that, the data appears to show —— *使用这些表达是因为科学家谨慎地表述发现，而非当作绝对真理*

### 批注范例

*展示学科语言特征的一个结论段落：*

**[发现]** The results show that amylase activity increased as temperature rose from 20°C to 40°C, with the highest rate of starch breakdown occurring at approximately 37°C. **[解释——联系科学原理]** This can be explained by the kinetic energy of the enzyme and substrate molecules. **[因果推理]** As temperature increased, the molecules moved faster and collided more frequently with the active site, increasing the rate of reaction. **[解释高温结果]** However, at temperatures above 50°C, amylase activity decreased sharply. **[科学解释]** This is because the high temperatures caused the enzyme to denature — the active site changed shape, so the starch substrate could no longer bind to it. **[模糊限制语]** The data suggests that the optimum temperature for amylase is close to 37°C, which is consistent with its function in the human body at normal body temperature. **[假设关联]** These results support the hypothesis that enzyme activity increases with temperature up to an optimum, then decreases due to denaturation.

*说明：本段使用了科学词汇（kinetic energy、active site、denature、substrate）、因果连接词（because、as a result）与模糊限制语（suggests、approximately）。它没有叙述实验过程——而是解释了结果背后的科学。*

### 分层教学

**支持（针对偏叙事写作或科学词汇有限的学生）：**
- 提供支架的完形填空版本："The results show that amylase worked fastest at ___°C. This is because at higher temperatures, the enzyme molecules had more ___, so they ___ with the substrate more often."
- 缩减至仅保留第 1 和第 2 部分（发现 + 解释）。待基础结构稳固后再加入评估与局限性。
- 在支架旁提供附带学生友好型定义的关键词汇表。
- 针对 EAL 学生：将句首提示与“锁钥模型”示意图配对——把语言与图像联系起来。

**拓展（针对写作能力较强的学生）：**
- 撤除句首提示——挑战学生自主建构科学语言。
- 要求处理异常结果："Your result at 60°C was higher than expected. Suggest a reason and explain how you would investigate it."
- 要求学生将自己的发现与已发表的淀粉酶数据进行对比并解释差异。
- 引入统计显著性概念："Can you be confident in your conclusion based on one set of results? What would strengthen it?"

---

## 已知局限性

1. **支架反映的是通用学科规范，而非学校特定要求。** 不同考试局、课程大纲与教师对实验报告结论可能有不同于通用科学规范的具体要求。教师应对照自身具体评估标准审视产出并在需要时加以修改。

2. **学科写作规范存在于光谱之上，而非僵化分类中。** 本支架呈现了清晰的体裁结构，但真实的学科写作更具流动性——历史论证可能包含科学证据，文学分析可能借鉴历史语境。支架先教授核心体裁规范；跨体裁融合是高阶技能，应在学生掌握基础结构之后再引入。

3. **写作支架无法替代内容知识。** 不理解酶为何在高温下变性的学生，无论支架多么强大都写不出好的科学结论。支架组织的是对理解的表达——它无法在没有理解的地方凭空创造理解。教师在要求学生写作前，应确保科学（或历史、文学）理解已经稳固。
