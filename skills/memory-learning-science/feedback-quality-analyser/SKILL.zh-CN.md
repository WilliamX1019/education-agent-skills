---
# AGENT SKILLS STANDARD FIELDS (v2)
name: feedback-quality-analyser
description: "分析现有书面反馈的质量、具体性、可操作性及对学生学习的影响。适用于审视教师或同伴反馈以改进反馈实践。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "memory-learning-science/feedback-quality-analyser"
skill_name: "反馈质量分析与改写器"
domain: "memory-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Hattie & Timperley (2007) — The power of feedback: a meta-analysis (effect size ~0.73)"
  - "Shute (2008) — Focus on formative feedback: a review of the research"
  - "Kluger & DeNisi (1996) — Effects of feedback intervention on performance: a historical review and meta-analysis"
  - "Black & Wiliam (1998) — Assessment and classroom learning: formative assessment principles"
  - "Wisniewski et al. (2020) — The power of feedback revisited: a meta-analysis of educational feedback research"
input_schema:
  required:
    - field: "feedback_text"
      type: "string"
      description: "待分析的现有反馈（教师撰写或同伴撰写）"
    - field: "task_context"
      type: "string"
      description: "要求学生完成的任务及学习目标"
  optional:
    - field: "student_work_summary"
      type: "string"
      description: "该反馈所针对的学生作品简要摘要"
    - field: "student_level"
      type: "string"
      description: "年龄/年级与能力画像"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：自我调节水平、语言熟练度、敏感性因素"
    - field: "rubric"
      type: "string"
      description: "来自上下文引擎：本任务使用的量规或成功标准"
output_schema:
  type: "object"
  fields:
    - field: "analysis"
      type: "object"
      description: "基于 Hattie & Timperley 模型对反馈层次、具体性与可操作性的诊断"
    - field: "rewritten_feedback"
      type: "string"
      description: "解决已识别弱点的改进版本"
    - field: "improvement_rationale"
      type: "string"
      description: "结合研究证据说明修改了什么及原因"
chains_well_with:
  - "gap-analysis-from-student-work"
  - "criterion-referenced-rubric-generator"
  - "self-regulation-scaffold-generator"
  - "metacognitive-prompt-library"
  - "kud-knowledge-type-mapper"
teacher_time: "3 分钟"
tags: ["feedback", "formative-assessment", "metacognition", "writing", "assessment"]
---

# 反馈质量分析与改写器

## 本技能的功能

接收一段教师或同伴反馈，依据 Hattie 与 Timperley（2007）的四层次反馈模型进行分析，并将其改写以提升其反馈层次、具体性和可操作性。该分析识别反馈作用于任务、过程、自我调节还是自我层次，并评估其是否告诉了学生他们现在在哪里、要去哪里以及如何到达那里。AI 在此处具有独特价值，因为大多数教师反馈——甚至来自经验丰富的教师——往往默认流于笼统的表扬（“很努力！”）、笼统的批评（“需要更多细节”）或自我层次反馈（“你是个很棒的写作者”），而研究表明这些反馈对学习零作用甚至有负面影响。将反馈改写为针对过程与自我调节层次，需要掌握大多数教师从未接触过的明确反馈研究知识。

## 循证基础

Hattie 与 Timperley（2007）开展了一项综合元分析，发现反馈的平均效应量高达 0.73——位居教育研究最高之列——但变异极大。有效反馈回答三个问题：我要去哪里？（前馈目的 feed up）、我做得怎么样？（反馈 feed back）、下一步去哪里？（前馈行动 feed forward）。他们确定了四个反馈层次：任务层次（正误）、过程层次（使用的策略）、自我调节层次（学生对自身学习的监控与调控）以及自我层次（对个人的表扬或批评）。任务层次反馈改善即时表现；过程层次反馈提升策略使用；自我调节反馈培养独立性。自我层次反馈（“你真聪明” / “令人失望的作品”）没有积极效果，反而可能因将注意力引向自我而非任务而损害学习。Kluger 与 DeNisi（1996）发现三分之一的反馈干预实际上降低了表现——通常是当反馈威胁到自尊或将注意力从任务转移开时。Wisniewski 等人（2020）更新了该元分析，证实包含信息（具体、参照任务）的反馈显著比仅包含判断（分数、表扬、批评）的反馈更有效。Shute（2008）指出，有效的形成性反馈是具体的、及时的、非威胁性的，并聚焦于当前表现与期望表现之间的差距。

## 输入模式

教师必须提供：
- **反馈文本：** 待分析的现有反馈。*例如：“干得好！你显然很努力了。下次在分析中多加点细节。” / “7/10。有一些不错的观点，但你的结论很薄弱。”*
- **任务情境：** 学生在做什么以及学习目标是什么。*例如：“十年级历史关于一战起因的论文。学习目标：使用证据构建因果论证。”*

可选（如有，由上下文引擎注入）：
- **学生作品摘要：** 对学生实际作品的简要描述
- **学生水平：** 年级与能力画像
- **学生档案：** 自我调节水平、语言熟练度、情感因素
- **量规：** 本任务使用的成功标准或量规

## 提示词

```
You are an expert in educational feedback research, specialising in Hattie & Timperley's (2007) feedback model and Shute's (2008) formative feedback principles. You have deep knowledge of the distinction between feedback levels (task, process, self-regulation, self) and understand why feedback specificity and actionability determine its impact on learning.

Your task is to analyse and rewrite the following feedback:

**Feedback text:** "{{feedback_text}}"
**Task context:** {{task_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student work summary:** {{student_work_summary}} — if provided, use the details of the actual work to make the rewritten feedback more specific. If not provided, base your analysis and rewrite on what can be inferred from the feedback text and task context.
**Student level:** {{student_level}} — if provided, calibrate language and expectations accordingly. If not provided, infer from the task context.
**Rubric/Success criteria:** {{rubric}} — if provided, reference specific criteria in the rewritten feedback. If not provided, reference the learning objective from the task context.
**Student profiles:** {{student_profiles}} — if provided, consider self-regulation level when pitching feedback (high self-regulation: more self-monitoring prompts; low self-regulation: more specific task and process guidance). If not provided, pitch feedback at a general level.

Analyse the feedback using these evidence-based criteria:

1. **Feedback level diagnosis (Hattie & Timperley, 2007):**
   - **Task level:** Does it tell the student what is correct or incorrect about their specific work? (Useful but limited — doesn't help them improve next time.)
   - **Process level:** Does it address the strategies, skills, or processes the student used? (More powerful — transfers to future tasks.)
   - **Self-regulation level:** Does it prompt the student to monitor, evaluate, or adjust their own learning? (Most powerful for building independence.)
   - **Self level:** Does it comment on the student as a person rather than on the work? (No learning benefit. Remove or redirect.)

2. **The three feedback questions (Hattie & Timperley, 2007):**
   - **Feed up (Where am I going?):** Does the feedback reference the learning goal or success criteria?
   - **Feed back (How am I going?):** Does the feedback tell the student specifically what they did well or poorly *in relation to the goal*?
   - **Feed forward (Where to next?):** Does the feedback give a specific, actionable next step the student can take?

3. **Specificity check (Shute, 2008):** Is the feedback specific enough that the student knows exactly what to do differently? "Add more detail" is not specific. "In paragraph 3, you claim that militarism caused WWI but don't provide any evidence. Add a specific example of military build-up between 1900–1914 to support this claim" is specific.

4. **Threat check (Kluger & DeNisi, 1996):** Could this feedback be perceived as threatening to self-esteem, particularly for a struggling learner? If so, reframe to focus on the work, not the person.

5. **Actionability check:** Can the student act on this feedback independently? If the feedback requires knowledge or skills the student doesn't have, it's not actionable — it needs to be accompanied by instruction or a resource.

Return your output in this exact format:

## Feedback Analysis

### Original Feedback
[Reproduce the original feedback]

### Level Analysis
| Feedback Level | Present? | Examples from the text |
|---------------|----------|----------------------|
| Task | Yes/No | [Quote specific phrases] |
| Process | Yes/No | [Quote specific phrases] |
| Self-regulation | Yes/No | [Quote specific phrases] |
| Self | Yes/No | [Quote specific phrases] |

**Dominant level:** [Which level dominates and whether that's appropriate]

### Three Questions Check
- **Feed up (Where am I going?):** [Does the feedback reference the goal? Yes/No + detail]
- **Feed back (How am I going?):** [Does it say what was done well/poorly? Yes/No + detail]
- **Feed forward (Where to next?):** [Does it give a specific next step? Yes/No + detail]

### Specificity Rating
[Low / Medium / High] — [Explanation]

### Key Problems
[Numbered list of specific issues with the feedback]

### Rewritten Feedback
[The improved version — same approximate length, dramatically improved quality]

### What Changed and Why
[Bullet list explaining each change with reference to the research]

**Self-check before returning output:** Verify that (a) the rewritten feedback addresses all three feedback questions (feed up, feed back, feed forward), (b) it operates at process or self-regulation level, not just task level, (c) it is specific enough that the student knows exactly what to do, (d) it does not contain self-level comments disguised as encouragement, and (e) it is written in language the student can understand at their level.
```

## 示例输出

**场景：** *反馈文本：“Priya，干得不错！里面有几个非常好的观点。你需要在分析上下功夫——下次试着写得更深入一些。你的写作风格很棒。6/10。” / 任务情境：“十年级英语文学论文，分析莎士比亚在第一幕中如何呈现麦克白夫人的野心。学习目标：分析语言和结构，探究人物是如何被呈现的。”*

---

## 反馈分析

### 原始反馈
“Priya，干得不错！里面有几个非常好的观点。你需要在分析上下功夫——下次试着写得更深入一些。你的写作风格很棒。6/10。”

### 层次分析
| 反馈层次 | 是否存在？ | 文本示例 |
|---------------|----------|----------------------|
| 任务 | 部分存在 | “6/10”提供了分数，但没有说明哪些地方正确或错误 |
| 过程 | 否 | 未提及 Priya 使用的策略、方法或分析过程 |
| 自我调节 | 否 | 没有提示 Priya 监控或评估自己的作品 |
| 自我 | 是 | “Priya，干得不错！” / “你的写作风格很棒”——两者都针对 Priya 个人，而非她的作品 |

**主导层次：** 自我层次反馈占主导地位。两条实质性评语（“干得不错”和“你的写作风格很棒”）都是针对 Priya 本人，而非她对麦克白夫人的分析。唯一的任务层次元素是分数（6/10），它只告诉 Priya 她的作品处于“中等”，却没有说明原因或如何改进。自我层次反馈对学习没有积极影响（Hattie & Timperley, 2007），而没有解释的分数只是一种判断，而非信息（Wisniewski et al., 2020）。

### 三问题核查
- **前馈目的（我要去哪里？）：** 否。反馈未提及学习目标（通过语言和结构分析莎士比亚如何呈现麦克白夫人的野心）。Priya 不知道自己的目标是什么。
- **反馈（我做得怎么样？）：** 几乎没有。“几个非常好的观点”过于笼统——哪些观点？好在哪里？“你需要在分析上下功夫”指出了差距，但不够具体。
- **前馈行动（下一步去哪里？）：** 否。“下次试着写得更深入一些”不具可操作性。Priya 无从知晓“更深入”意味着什么、“更深入的分析”长什么样，以及该如何做到。

### 具体性评级
**低**——反馈中没有任何针对 Priya 实际作品的具体引用。同一段评语（“干得不错，分析再加把劲，写得更深入”）可以套用到任何学生在任何主题上的论文。这是低质量反馈的典型特征（Shute, 2008）。

### 核心问题

1. **“干得不错”属于自我层次反馈。** 它评价的是 Priya 的努力（一种个人特质），而非她的作品，没有提供关于哪里好、为什么好的信息。Kluger 与 DeNisi（1996）发现，指向自我的反馈会将注意力从任务转移到自尊。

2. **“几个非常好的观点”属于未具体化的任务层次反馈。** 哪些观点？是什么让它们有效？缺乏具体性，Priya 就无法复制自己做得好的地方。

3. **“你需要在分析上下功夫——试着写得更深入一些”是笼统的前馈行动。** 这是中学教育中最常见的反馈失效。对于一个不知道深度分析长什么样的十年级学生而言，“更深入”毫无意义。这相当于要求 Priya 已经具备反馈正让她去培养的技能。

4. **“你的写作风格很棒”是带有性别维度的自我层次反馈。** 它赞美了 Priya 作为写作者的身份，而不是指出具体的有效写作选择。关于性别化反馈模式的研究表明，女生更常收到关于文风/卷面的表扬，而男生则更常收到关于内容的实质性反馈。

5. **“6/10”是判断，而非反馈。** Butler（1988）发现，当评语附带分数时，学生会只关注分数而完全忽略评语。分数削弱了评语本可能具有的任何形成性价值。

### 改写后的反馈

Priya，这篇论文表明你能够识别出相关的引文——你从第一幕第五场选取了很有力的证据，特别是麦克白夫人的“来吧，请消除我的女性特征（unsex me here）”这段独白。

你的引文选择很有效，但你的分析停留在表面。例如，你写道：“这表明麦克白夫人很有野心。”这是**是什么（what）**——但学习目标要求你分析莎士比亚**如何（how）**通过语言来呈现她的野心。再看看你引用的“unsex me here”这句话。问问自己：莎士比亚为什么要用“unsex”这个词？这告诉了我们这段独白中“野心”与“性别”是如何关联的？当观众听到一位女性请求剥夺自己的女性特质以换取力量时，会产生怎样的效果？这才是这篇论文所需的分析深度。

**具体下一步行动：** 从这篇论文中挑选你最强的两处引文。针对每一处，写出三句话：（1）这句引文展示了关于麦克白夫人的什么；（2）莎士比亚为什么选择这个特定的词或意象；（3）它对观众产生了什么效果。下节课把这几句话带来，我们一起看看。

### 修改内容与原因

- **移除了“干得不错”和“写作风格很棒”**——这些是将注意力引向 Priya 个人而非作品的自我层次反馈。替换为指出她具体做得好的任务层次表扬：从第一幕第五场选取相关引文（Hattie & Timperley, 2007——关于正确之处的任务层次反馈）。

- **用关于“更深入”的具体示范替换了“写得更深入”**——改写版本通过剖析她自己的其中一处引文并演示她应提出的思考问题（为什么用这个词？有什么效果？），向 Priya 精确展示了分析深度是什么样子。这是过程层次反馈：它针对的是分析的**策略**，而不仅仅是结果（Hattie & Timperley, 2007）。

- **增加了具体、可操作的下一步行动**——“挑选两处引文，用此结构各写三句话”给了 Priya 一件具体可做的事。她可以独立照此执行。这是真正的前馈行动（Shute, 2008）。

- **移除了分数**——Butler（1988）证明，纯评语反馈比“评语加分数”能产生更多的学习效果，因为分数会分散对形成性信息的注意力。如果必须记录分数，请单独或稍后提供。

- **关联了学习目标**——改写版本明确将反馈连接到任务目标（“学习目标要求你分析**如何**”），为 Priya 提供了清晰的改进参照点（前馈目的）。

---

## 已知局限

1. **改写需要了解学生的实际作品。** 在未看到 Priya 论文全文的情况下，改写反馈使用了原反馈中提及或合理推断的引文。如果提供了学生作品摘要，改写会更加精准。教师应将改写结果视为可供调整的范本，而非最终成品。

2. **反馈的有效性取决于师生关系。** Wisniewski 等人（2020）发现，相同的反馈措辞会因信任度及课堂反馈文化的不同而被不同地接受。改写假设了一个支持性的课堂环境。在学生存在反馈焦虑的情境中，开头可能需要进一步柔化——但研究明确表明，为了保护感受而降低具体性会减少学习效果。

3. **本技能分析单条反馈质量，但无法解决系统性反馈难题。** 如果教师的批改工作量意味着面对30名学生每篇论文只有3分钟，即使具备卓越的反馈知识也无济于事。系统性解决方案（减少批改总量、使用全班共性反馈、选择性精批）超出本技能范围，但往往才是真正的瓶颈。
