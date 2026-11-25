---
# AGENT SKILLS STANDARD FIELDS (v2)
name: central-historical-question-evaluator
description: "评估教师起草的核心历史问题是否具备驱动真正历史探究的能力。适用于判断一个问题能否引发基于证据的权衡，还是只会导致浅层回答。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS
skill_id: "historical-thinking/central-historical-question-evaluator"
skill_name: "核心历史问题评估器"
domain: "historical-thinking"
version: "1.0"
contributor: "Sean Hu"
evidence_strength: "strong"
evidence_sources:
  - "Reisman (2012) — Reading like a historian: a document-based history curriculum intervention in urban high schools"
  - "Wineburg, Martin & Monte-Sano (2011) — Reading like a historian: teaching literacy in middle and high school history classrooms"
  - "Wineburg & Martin (2004) — Reading and rewriting history"
  - "Wineburg (2007) — Unnatural and essential: the nature of historical thinking"
  - "Wineburg (2016) — Why historical thinking is not about history"
input_schema:
  required:
    - field: "draft_question"
      type: "string"
      description: "教师起草的核心历史问题——旨在驱动一节基于文献的课程或单元的问题"
    - field: "available_sources"
      type: "string"
      description: "学生将用于调查该问题的一手与二手史料描述——数量、类型以及所代表的关键张力或视角"
    - field: "student_level"
      type: "string"
      description: "年龄/年级以及当前开展基于文献探究的经验水平"
  optional:
    - field: "historical_topic"
      type: "string"
      description: "该问题所处的更广泛主题或单元"
    - field: "learning_objectives"
      type: "string"
      description: "教师希望学生通过调查该问题学到或能够做到什么"
    - field: "previous_questions"
      type: "string"
      description: "早期课程中的核心问题——用于检查问题类型的多样性并在学生已练习基础上递进"
    - field: "curriculum_framework"
      type: "string"
      description: "来自上下文引擎：正在使用的相关课程标准或历史思维框架"
output_schema:
  type: "object"
  fields:
    - field: "question_evaluation"
      type: "object"
      description: "对照富有成效的历史探究标准对草稿问题进行分析——是否需要证据、是否允许多个可辩护的答案、是否要求运用历史思维技能，以及是否避开了可直接检索答案或纯主观观点的陷阱"
    - field: "strengths"
      type: "array"
      description: "草稿问题做得好的地方——能够驱动有效探究的具体特征"
    - field: "threats"
      type: "array"
      description: "草稿问题中可能导致浅层、可预测或非历史性回答的具体问题——附每项威胁的解释"
    - field: "revised_question"
      type: "string"
      description: "如果草稿问题需要修改，提供修改版并解释改动内容与原因——如果草稿问题本身很强，则确认无需修改"
    - field: "question_type_analysis"
      type: "string"
      description: "问题类型分类及关于它将要求何种历史思维的指导"
chains_well_with:
  - "document-based-lesson-designer"
  - "historical-document-set-curator"
  - "historical-source-adapter"
  - "sourcing-skill-builder"
  - "corroboration-skill-builder"
  - "backwards-design-unit-planner"
  - "hinge-question-designer"
teacher_time: "2 分钟"
tags: ["historical-questions", "inquiry", "document-based-lessons", "historical-thinking", "lesson-design", "DIG"]
---

# 核心历史问题评估器

## 本技能的作用

对照富有成效的历史探究标准评估教师起草的核心历史问题，并在需要时提出修改建议。输出包括该问题能否驱动真正的基于文献调查的分析、具体优势与潜在威胁的识别、问题类型分类，以及——当草稿存在问题时——修改后的问题及改动内容与原因的说明。

核心历史问题是基于文献的历史课的引擎。在“像历史学家一样阅读（Reading Like a Historian）”课程（Reisman, 2012; Wineburg, Martin & Monte-Sano, 2011）中，每一节课都围绕一个要求学生调查一手史料的问题组织："Did Pocahontas rescue John Smith?"、"Was Abraham Lincoln a racist?"、"What caused the Dust Bowl?" 这些问题具有将其与课本复习题或开放式讨论提示区分开来的特定特征：它们必须通过证据回答（而不仅仅是个人观点）、允许多个可辩护的答案（而非单一标准答案）、要求运用历史思维技能（溯源、精读、语境化、互证），并且存在真实的争议（历史学家对此意见不一）。

设计不当的核心问题会破坏一节原本结构良好的课。只有一个正确答案的问题（"When did the Battle of Lexington take place?"）只需要信息检索，而不是探究。纯属道德观点的问题（"Was slavery wrong?"）会引出道德宣示，而不是基于证据的论证。过于宽泛的问题（"What happened in the American Revolution?"）则缺乏分析焦点。本技能帮助教师在问题进入课堂之前识别这些问题。

本技能是评估器，而非生成器。教师才是了解自己学生、课程和史料的专家。教师先起草问题；本技能对其进行评估，并在必要时提出修改建议。这保留了教师对探究的所有权，同时提供了他们独自备课时未必能生成的分析性反馈。

## 循证基础

Reisman (2012) 围绕核心历史问题构建了“像历史学家一样阅读”课程，将课堂模式描述为四部分“活动结构”：背景知识、核心历史问题、附带引导问题和策略指导的历史文献，以及全班讨论。核心问题是组织核心——它决定了选择哪些文献、突出哪些策略，以及什么才算成功的学生回答。Reisman 的干预在历史思维、事实知识和阅读理解方面均产生了显著提升，表明“问题-文献-讨论”结构在教学上非常有效。

Wineburg, Martin & Monte-Sano (2011) 在其课程文本中提供了八个完整开发的核心历史问题示例。对这些问题的分析揭示了一致的设计特征：它们被框定为真实的问题（"Did Pocahontas rescue John Smith?" 而非 "Describe the Jamestown colony"）、使用传递争议感的语言（"Did...?"、"Was...?"、"Who really benefited?"）、范围足够聚焦使学生能用少量文献（2–5 份史料）进行调查，并且锚定在具体证据上而非依赖泛泛的通识。

Wineburg & Martin (2004) 通过宝嘉康蒂（Pocahontas）单元展示了精心设计的历史问题的教学力量。"Did Pocahontas rescue John Smith?" 之所以有效，恰恰因为它看起来简单，实则真正复杂——答案取决于你如何权衡史密斯自相矛盾的叙述、如何解读历史学家相互竞争的分析，以及你认为什么才算充分证据。这个问题邀请学生进入一场真实的史学争论，而不是复述一个盖棺定论的叙事。

Wineburg (2007) 指出，富有成效的历史探究始于真实的困惑。“无知的明确化（specification of ignorance）”——即专家利用文献清晰界定自己未知之处的实践——需要一个真正容许不确定性的问题。如果答案早已预设或极易检索，就没有什么可界定为未知的。核心问题的质量决定了学生是投入真正的探究，还是在表演一场答案早已注定的研究模拟。

## 输入模式

教师必须提供：
- **Draft question（草稿问题）：** 目前拟定的核心问题。*例如："Did Pocahontas rescue John Smith?" / "Was the dropping of the atomic bomb on Hiroshima justified?" / "What were the causes of World War I?" / "Why did people support the Nazi Party?"*
- **Available sources（可用史料）：** 学生将使用的文献。*例如："Smith's 1608 and 1624 accounts, plus interpretations by Adams, Lemay, Lewis, and Barbour" / "Three propaganda posters from different countries, 1914–1916" / "Two eyewitness accounts of the bombing and a excerpt from Truman's diary"*
- **Student level（学生水平）：** *例如："Year 8, new to document-based inquiry" / "Year 11 IB History, experienced with source analysis"*

可选：
- **Historical topic（历史主题）：** 更广泛的单元背景
- **Learning objectives（学习目标）：** 学生应当学到什么
- **Previous questions（先前问题）：** 单元中早先的核心问题——用于检查多样性
- **Curriculum framework（课程框架）：** DIG、Seixas、国家课程等

## Prompt

```
You are an expert in historical thinking pedagogy and document-based lesson design, with deep knowledge of the Reading Like a Historian curriculum structure (Reisman, 2012; Wineburg, Martin & Monte-Sano, 2011) and the role of central historical questions in driving genuine inquiry. You understand that a well-designed central question is the engine of a document-based lesson — it determines whether students engage in genuine historical thinking or merely retrieve answers, recite opinions, or perform research simulations.

Your task is to evaluate a teacher-drafted central historical question:

**Draft question:** {{draft_question}}
**Available sources:** {{available_sources}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available.

**Historical topic:** {{historical_topic}}
**Learning objectives:** {{learning_objectives}}
**Previous questions:** {{previous_questions}} — if provided, check that the draft question offers variety in question type.
**Curriculum framework:** {{curriculum_framework}}

Evaluate the draft question against these criteria:

1. **Evidence-dependent:** Does answering this question REQUIRE engagement with the available sources? Or could a student answer it from general knowledge or personal opinion without reading any documents?

2. **Genuinely contested:** Does the question permit multiple defensible answers? Could two students examine the same evidence and reach different but equally well-supported conclusions? If the question has a single correct answer, it is a retrieval task, not an inquiry.

3. **Historically specific:** Is the question anchored to specific evidence, events, and actors? Or is it so broad that it becomes an essay prompt rather than an investigation? A question that can only be answered with a book is too broad for a document-based lesson.

4. **Skill-demanding:** Does answering the question require students to use historical thinking skills — sourcing, close reading, contextualisation, corroboration — or could it be answered without any of these? The best questions make one or more skills essential to reaching a defensible answer.

5. **Appropriately scoped:** Is the question answerable with the available document set? Too few sources and the question can't be investigated; too many or too complex and the question overwhelms the students.

6. **Engaging and accessible:** Will this question interest students at this level? Does its language make the task clear? Questions that use jargon, assume prior knowledge students don't have, or sound like essay prompts rather than genuine puzzles will fail to motivate inquiry.

Classify the question type:
- **Factual-investigative:** "Did X happen?" — requires weighing evidence for and against a factual claim
- **Causal-analytical:** "What caused X?" or "Why did X happen?" — requires identifying and weighing causal factors
- **Evaluative-interpretive:** "Was X justified?" or "Was X a turning point?" — requires evaluating significance or making a judgement grounded in evidence
- **Perspective-analytical:** "How did different groups see X?" — requires reconstructing multiple viewpoints
- **Comparative:** "How was X different from Y?" — requires structured comparison

Return your output in this exact format:

## Question Evaluation

**Draft question:** [The question as submitted]
**Question type:** [Classification]
**Overall verdict:** [Strong / Needs modification / Needs substantial revision]

### Strengths

[What the question does well — be specific about which criteria it meets and why]

### Threats

[Specific problems, each with an explanation of why it threatens the quality of inquiry. Number each threat.]

### Source-Question Fit

[Does the available document set support investigation of this question? Are there gaps — sources that would strengthen the investigation — or mismatches — sources that don't connect to the question?]

### Revised Question

[If the question needs modification: the revised version with a brief explanation of what changed and why. If the question is strong: "No revision needed" with a brief explanation of why the question works as drafted.]

### Teaching Notes

[1–2 practical notes for the teacher: what historical thinking skills this question will foreground, what student responses to anticipate, and any potential pitfalls to watch for during the lesson.]

**Self-check before returning output:** Verify that (a) the evaluation addresses all six criteria, (b) the strengths and threats are specific to this question, not generic, (c) the source-question fit analysis considers the actual available sources, (d) any revised question preserves the teacher's intent while addressing the identified threats, and (e) the teaching notes are practical and actionable.
```

## 示例输出

**场景：** *Draft question: "What were the causes of World War I?" / Available sources: "An excerpt from the Treaty of Versailles (Article 231 — the 'war guilt' clause), a political cartoon from 1914 showing European alliances as a chain of dominoes, and a letter from a British soldier written in August 1914 expressing enthusiasm for the war" / Student level: "Year 9, have done two previous document-based lessons with simpler questions" / Previous questions: "Did Pocahontas rescue John Smith? (factual-investigative); Was the execution of Charles I justified? (evaluative-interpretive)"*

---

## 问题评估

**草稿问题：** "What were the causes of World War I?"
**问题类型：** 因果分析型（Causal-analytical）
**总体结论：** 需要修改

### 优势

该问题聚焦于一个实质性的历史主题，并被框定为因果探究，这对在早期基于文献学习基础上进阶的九年级学生是合适的。因果型问题适合这一阶段，因为它们推动学生超越事实检索走向分析推理。此外，该问题类型与前两节课（事实调查型与评价阐释型）形成了良好的多样性递进。

### 潜在威胁

1. **相对于文献组而言过于宽泛。** 第一次世界大战的起因是一个可以写满整本书的主题。三份文献无法支撑对这个问题的真正调查——学生要么退回到他们已有的课本知识，要么写出只点一下文献却不将其作为证据使用的肤浅回答。问题的范围超出了现有史料所能支撑的边界。

2. **按照当前措辞，缺乏真正的争议性。** "What were the causes?" 诱发的是清单罗列，而非论证。学生很可能会产出一份原因目录（同盟体系、军国主义、帝国主义、民族主义、刺杀事件），而不是一个需要用证据捍卫的论点。清单不是论证；一个设计良好的问题应当要求学生采取立场。

3. **不依赖证据。** 一名学过一战的九年级学生完全可以不读这三份文献就回答这个问题。问题并不要求使用史料——凭通识即可作答。这意味着文献沦为既有答案的插图，而非建构答案的证据。

4. **史料与当前框定的问题不够契合。** 《凡尔赛条约》（1919 年）是一份战后归责文件——它关乎战争起因在战后如何被“解读”，而不是起因本身。政治漫画展示了同盟体系，这只是“一个”原因。士兵信件展示了参战热情，关乎公众情绪——勉强算一个原因，但问题本身并未自然引导向它。这三份史料各自都很丰富，但围绕泛泛的“起因”一词并不能凝聚成一个连贯的史料集。

### 史料-问题契合度

这三份史料各自都很有价值，但对于当前起草的问题而言并未形成连贯的文献组合。它们更适合一个更聚焦的问题——具体而言，是一个关于“归责（BLAME）”或“责任（RESPONSIBILITY）”而非泛泛起因的问题。《凡尔赛条约》指责德国；政治漫画暗示同盟体系使战争不可避免（分散了责任）；士兵信件使归责变得更加复杂——如果士兵本身充满“热情”，我们还能单单指责政府吗？这组史料非常适合探讨战争责任如何被分配以及这种分配是否公平——但不适合泛泛的“战争是什么引起的？”。

### 修改后的问题

**"Who was most to blame for World War I?"（第一次世界大战最应该归咎于谁？）**

这一修改收窄了范围、使问题真正具有争议性（理智的人会在责任归属上产生分歧），并与现有史料高度对齐。《凡尔赛条约》把责任归于德国——学生必须评估这是否公平；政治漫画暗示同盟体系使战争不可避免——将责任分散到多个国家；士兵信件进一步使责任问题复杂化——如果连士兵都充满热情，政府是唯一的责任方吗？修改后的问题把文献从插图变成了证据，并要求学生相互比对权衡（互证 corroboration）、考虑每份文献何时以及为何产生（溯源 sourcing、语境化 contextualisation），并关注每份文献如何框定责任问题（精读 close reading）。

**改动说明：** 问题从宽泛的因果概览收窄为具体的评价阐释型问题，使三份现有史料能够真正支撑调查。"Who was most to blame?" 要求提出立场，而不仅仅是罗列清单。

### 教学说明

这个问题将突出**互证（corroboration）**——学生必须相互权衡三份史料来构建关于责任的论证。它还对《凡尔赛条约》提出了**溯源（sourcing）**要求：学生需要认识到第 231 条是由战胜国撰写的，这塑造了其对责任的分配。预期部分学生会习惯性地只罗列原因而不就责任提出论点——用这句话引导他们："You've told me several causes. But which country or factor do you think was MOST responsible, and what evidence from the documents supports your position?" 留意那些把《凡尔赛条约》当作中立历史事实而非带有政治动机文献来对待的学生——这正是进行溯源教学的契机。

---

## 已知局限性

1. **本技能评估的是“问题-史料”组合，而非孤立的问题本身。** 一个在某组文献下极佳的问题，在另一组文献下可能表现很差。评估始终是相对于可用史料而言的。如果教师在评估后更换了史料，分析结果可能不再适用。

2. **本技能无法评估问题是否能吸引特定班级的学生。** 投入度取决于地方语境——学生的先验知识、兴趣、文化背景以及教师与班级的默契。本技能可以评估问题在结构上是否具有吸引力（真困惑、表述清晰、范围适中），但无法判断是否能打动特定学生。

3. **本技能是评估器，而非生成器。** 它评估并在必要时修改教师起草的问题，而不从零生成问题。这是刻意的设计：教师比任何技能都更了解自己的学生、课程与史料。本技能针对教师已经打磨过的问题提供分析性反馈。
