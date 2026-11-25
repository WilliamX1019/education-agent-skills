---
# AGENT SKILLS STANDARD FIELDS (v2)
name: cognitive-load-analyser
description: "分析学习任务中的认知负荷问题并提出具体设计改进建议。适用于任务令学生不堪重负、指令显得复杂或需要简化学习材料时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "memory-learning-science/cognitive-load-analyser"
skill_name: "认知负荷分析器"
domain: "memory-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Sweller (1988) — Cognitive load during problem solving: effects on learning"
  - "Sweller (1994) — Cognitive load theory, learning difficulty, and instructional design"
  - "Paas & van Merriënboer (1994) — Instructional control of cognitive load in the training of complex cognitive tasks"
  - "Sweller et al. (2019) — Cognitive Architecture and Instructional Design: 20 Years Later (updated CLT)"
  - "Kalyuga et al. (2003) — The expertise reversal effect"
input_schema:
  required:
    - field: "task_description"
      type: "string"
      description: "待分析的学习任务、指令或教学资源"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及熟练程度（新手/中级/高级）"
  optional:
    - field: "task_materials"
      type: "string"
      description: "所用学习单、幻灯片或指令的描述或文本"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：工作记忆画像、先验知识数据"
    - field: "lesson_context"
      type: "string"
      description: "本任务在课堂中的前后衔接环节"
output_schema:
  type: "object"
  fields:
    - field: "load_analysis"
      type: "object"
      description: "内在负荷、外在负荷与相关负荷的拆解及评级"
    - field: "problem_areas"
      type: "array"
      description: "造成不必要认知负荷的具体要素"
    - field: "modification_suggestions"
      type: "array"
      description: "降低外在负荷并优化相关负荷的具体修改方案"
    - field: "expertise_reversal_check"
      type: "string"
      description: "支架是否可能对高阶学习者产生反效果"
chains_well_with:
  - "worked-example-fading-designer"
  - "explicit-instruction-sequence-builder"
  - "scaffolded-task-modifier"
  - "text-complexity-analyser"
teacher_time: "4 分钟"
tags: ["cognitive-load", "task-design", "scaffolding", "instructional-design", "working-memory"]
---

# 认知负荷分析器

## 本技能的功能

从三个维度评估学习任务、指令集或教学资源的认知负荷：内在负荷（内容本身的固有复杂度）、外在负荷（由不良设计造成的不必要困难）和相关负荷（用于建构图式的有效认知投入）。生成关于负荷过载位置的具体诊断及可落地的修改建议。AI 在此处具有独特价值，因为认知负荷分析需要同时评估内容复杂度、教学设计质量以及学习者专业水平——这项技能通常需要教学设计方面的专业训练，而大多数教师并未接受过此类训练。

## 循证基础

Sweller（1988, 1994）确立了认知负荷理论（CLT），作为理解部分教学设计为何失效的框架：人类工作记忆同时只能容纳约 4-7 个要素，当总认知负荷超过工作记忆容量时，学习就会失败。Sweller 区分了内在负荷（由要素交互性决定——必须同时处理多少个要素）、外在负荷（由不良教学设计引起）和相关负荷（用于建构图式的有效努力）。Paas 与 van Merriënboer（1994）将 CLT 操作化应用于教学设计，证明降低外在负荷能够持续改善学习成果。Sweller 等人（2019）更新了该理论，纳入了演化心理学并细化了生物初级知识与生物次级知识的区分。尤为关键的是，Kalyuga 等人（2003）发现了“专业逆转效应”（expertise reversal effect）——那些为新手降低负荷的教学技术（如样例、整合图表）反而可能因为要求高阶学习者处理冗余信息而增加其负荷。这意味着认知负荷分析必须始终考量学习者的专业水平。

## 输入模式

教师必须提供：
- **任务描述：** 待分析的学习任务、指令或资源。*例如：“学生阅读一篇关于渗透作用的两页文本，同时完成一张图表标注活动并回答理解问题” / “用配方法解一元二次方程——包含20道题的练习单”*
- **学生水平：** 年龄/年级及熟练程度。*例如：“十年级，首次接触该主题（新手）” / “十二年级，考前复习（高阶）”*

可选（如有，由上下文引擎注入）：
- **任务材料：** 实际使用的文本、学习单或指令
- **学生档案：** 工作记忆画像、已知学习困难、先验知识数据
- **课堂情境：** 本任务前后的教学安排

## 提示词

```
You are an expert in Cognitive Load Theory (CLT) with deep knowledge of Sweller's (1988, 1994) framework, Sweller et al.'s (2019) updated theory, and Kalyuga et al.'s (2003) expertise reversal effect. You understand the distinctions between intrinsic, extraneous, and germane cognitive load and how instructional design affects each.

Your task is to analyse the following learning task for cognitive load:

**Task:** {{task_description}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Materials:** {{task_materials}} — if provided, analyse these specific materials. If not provided, base your analysis on the task description alone.
**Lesson context:** {{lesson_context}} — if provided, consider what comes before and after the task when assessing cumulative load. If not provided, analyse the task in isolation.
**Student profiles:** {{student_profiles}} — if provided, consider specific working memory and prior knowledge factors. If not provided, base your analysis on typical expectations for the stated year group and expertise level.

Conduct your analysis using these CLT principles:

1. **Intrinsic load assessment:** Count the element interactivity. How many elements must a student hold in working memory simultaneously to complete this task? Consider:
   - Number of new concepts introduced at once
   - Whether elements can be learned in isolation (low interactivity) or must be understood in relation to each other (high interactivity)
   - Prior knowledge that may reduce intrinsic load through chunking

2. **Extraneous load identification:** Identify design features that consume working memory without contributing to learning:
   - **Split-attention effect:** Must students mentally integrate information from two or more separated sources (e.g., a diagram on one page and explanation on another)?
   - **Redundancy effect:** Are students processing the same information in multiple formats unnecessarily?
   - **Modality effect:** Could some visual information be presented as audio (or vice versa) to use dual channels?
   - **Transient information effect:** Is important information presented transiently (speech, animation) when it needs to be persistent?
   - **Unnecessary complexity:** Are instructions more complex than necessary? Are there decorative elements that don't aid learning?

3. **Germane load assessment:** What productive cognitive effort does the task demand?
   - Schema construction: Does the task build mental models or just require recall?
   - Comparison and contrast: Does the task require students to see relationships?
   - Self-explanation: Does the task prompt students to explain why, not just what?

4. **Expertise reversal check (Kalyuga et al., 2003):** If the student level is intermediate or advanced, check whether scaffolds or supports that would help novices are actually creating redundancy for these learners.

5. **Total load assessment:** Is the combined load (intrinsic + extraneous + germane) likely to exceed working memory capacity for these learners? If yes, what must change?

Return your output in this exact format:

## Cognitive Load Analysis

### Task Summary
[1–2 sentence restatement of the task]

### Load Breakdown

**Intrinsic Load: [Low / Medium / High]**
- Element interactivity count: [number of elements that must be processed simultaneously]
- [Specific explanation of what makes this content inherently simple or complex]

**Extraneous Load: [Low / Medium / High]**
- [List each source of extraneous load with specific reference to the CLT effect it violates]

**Germane Load: [Low / Medium / High]**
- [What schema-building work the task demands]

### Overall Assessment
[Is total load likely within working memory capacity? Will learning occur or will students be overwhelmed?]

### Problem Areas
[Numbered list of specific elements creating unnecessary load]

### Modification Suggestions
For each problem area, provide a specific, actionable modification:
- **Problem:** [What's wrong]
- **Principle:** [Which CLT principle it violates]
- **Fix:** [Exact change to make]

### Expertise Reversal Check
[Is this task appropriately calibrated for the stated expertise level? Would the scaffolding help or hinder?]

**Self-check before returning output:** Verify that (a) you have distinguished intrinsic from extraneous load — do not label inherent content complexity as a design problem, (b) every modification suggestion is specific and actionable, not generic advice like "simplify the task," (c) you have considered the expertise reversal effect, and (d) modifications reduce extraneous load without also reducing germane load (productive difficulty should be preserved).
```

## 示例输出

**场景：** *任务：“七年级学生阅读一篇关于水循环的两页文本，同时完成一张空白图表标注活动，并在另一张单独的学习单上回答10道理解问题。文本、图表和问题分别印在三张纸上。” / 学生水平：“七年级科学，首次学习水循环（新手）”*

---

## 认知负荷分析

### 任务摘要
七年级新手学习者需要同时使用三张独立的纸张，阅读关于水循环的文本、标注空白图表并回答理解问题。

### 负荷拆解

**内在负荷：中等**
- 要素交互性计数：约 8–10 个要素（蒸发、凝结、降水、汇集、径流、地下水流、蒸腾，以及它们作为循环系统之间的相互关系）
- 水循环具有中等程度的要素交互性——每个过程都可以单独理解，但理解**循环**需要同时在工作记忆中保持多个过程并追踪它们之间的关系。对于没有先验图式的七年级新手学习者而言，这处于可管理内在负荷的上限。

**外在负荷：高**
- **分散注意效应（严重）：** 三张独立的纸张迫使学生在文本、图表和问题之间不断切换。他们必须在文本中搜寻信息，在切换到图表或问题纸时将其保持在工作记忆中，然后再加以应用——且每次都会丢失阅读位置。这是分散注意的典型案例（Sweller, 1994）。
- **冗余风险：** 文本和图表可能重复呈现了相同的信息。如果图表只是简单地配图说明文本已描述的内容，学生就在没有额外学习收益的情况下以两种形式处理相同内容。
- **无目标问题缺失：** 理解问题强加了特定的搜寻目标，迫使学生采用手段-目的分析——学生搜寻答案，而非建立对整个系统的理解。

**相关负荷：低**
- 按当前设计的任务将大部分认知努力引向了**寻找信息**（外在负荷），而非**理解系统**（相关负荷）。学生很可能会采取“搜寻并抄写”的方式，而不是建构水循环作为互联系统的心理模型。理解问题通过奖励定位具体事实助长了这种表层加工。

### 总体评估
对于七年级新手学习者而言，总负荷几乎肯定超过了工作记忆容量。来自三份材料分散注意的高外在负荷，加上主题本身的中等内在负荷，留给相关加工（真正理解循环）的工作记忆容量所剩无几。学生很可能会通过从文本向图表和问题抄写词语来完成任务，却无法建构连贯的图式。尽管表面上做了大量“作业”，学习效果却会微乎其微。

### 问题区域

1. **三张独立纸张造成严重的分散注意。** 学生必须在物理切换材料时将信息保存在工作记忆中，频繁丢失位置，并将工作记忆消耗在材料导航而非学习上。

2. **同步进行的活动争夺工作记忆。** 阅读、图表标注与回答问题是三项并行任务，每项都需要工作记忆。对于新手学习者，这些活动应当序列化安排，而非同时进行。

3. **理解问题助长“搜寻-抄写”，而非理解。** 学生在文本中扫描与问题匹配的关键词，而不是为了理解而阅读。这产生了高外在负荷（搜寻）和极低的相关负荷（理解）。

4. **缺少样例或过程模型。** 首次接触水循环的新手学习者没有用于组织信息的图式。在被要求独立产出之前，他们需要一个完整的样例（带有注释的全标注图表）。

### 修改建议

- **问题：** 三张独立纸张造成分散注意
- **原则：** 分散注意效应（Sweller, 1994）——当学习者必须在物理或时间上分离的来源之间进行心理整合时，外在负荷会增加
- **修复：** 将文本直接整合进图表本身。在图表相关位置直接放置简短的解释性标签（例如，在表示蒸发的箭头旁加注）。完全取消独立文本——带有整合文本的图表成为单一信息源。将问题放在同一张纸上，紧邻图表下方。

- **问题：** 同步活动使工作记忆超载
- **原则：** 要素交互性——同时处理过多新要素
- **修复：** 对活动进行序列化安排：（1）首先，用5分钟研究一张全标注、带注释的图表（样例——Sweller & Cooper, 1985）。（2）接着，尝试一张移除核心术语的部分标注图表（补全问题）。（3）最后，凭记忆尝试一张完全空白的图表（独立练习）。这就是样例渐隐序列。

- **问题：** 理解问题助长搜寻-抄写
- **原则：** 无目标效应——特定目标状态迫使进行手段-目的分析，增加外在负荷
- **修复：** 用一个无目标指令替换这10道理解问题：“研究水循环图表。写下你能想到的关于水如何在系统中移动以及为什么这样移动的所有内容。”这会鼓励图式建构而非信息搜猎。如果确实需要具体问题，请在自由研习阶段**之后**将其作为提取练习使用。

- **问题：** 新手学习者缺少样例
- **原则：** 样例效应（Sweller & Cooper, 1985）——新手从研究样例中学到的比直接解题更多
- **修复：** 在任何独立作业之前，提供一个完全完成且带注释的示例，详细展示水循环的一部分（例如蒸发-凝结-降水序列），并用明确注释解释每一步**为什么**发生。然后逐步撤除支持。

### 专业逆转效应检查
本任务面向新手学习者设计，上述修改对新手而言是恰当的。然而，如果将同一任务用于正在复习水循环的十年级学生（他们已经拥有稳固的图式），样例方法反而会适得其反——Kalyuga 等人（2003）证明，样例会增加专家的负荷，因为他们必须处理冗余信息。对于高阶学习者，应直接进入空白图表 + 提取练习阶段，跳过样例与补全阶段。

---

## 已知局限

1. **无法观察实际的学生行为。** 本分析基于任务设计，而非学生对任务的实际体验。取决于先验知识，两名学生在同一任务中可能经历截然不同的认知负荷。任务进行中教师的观察仍然至关重要——超载的迹象包括放弃任务、不理解地抄写，以及询问程序性问题（“答案写在哪里？”）而非内容性问题。

2. **在不改变内容的情况下，内在负荷无法降低。** 如果内容本身固有地复杂（高要素交互性），本分析只能降低外在负荷并优化排序——无法让复杂内容本身变简单。对于高内在负荷内容，解决方案往往是将内容拆分为跨越多节课教授的子要素，而不是试图在一节课内强行简化。

3. **专业逆转效应意味着建议具有专业水平依赖性。** 帮助新手的做法会阻碍专家，反之亦然。如果学生水平判断不准确（例如被描述为“新手”，但学生实际上拥有扎实的先验知识），修改方案可能会适得其反。教师必须基于学生真实的知识水平而非假设的知识水平进行校准。
