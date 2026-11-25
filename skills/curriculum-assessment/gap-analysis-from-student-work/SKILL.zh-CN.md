---
# AGENT SKILLS STANDARD FIELDS (v2)
name: gap-analysis-from-student-work
description: "对照评价标准分析学生作业，识别当前表现与学习目标之间的具体差距。适用于批改提交作业、规划反馈或诊断学习需求。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/gap-analysis-from-student-work"
skill_name: "学生作业差距分析器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Black & Wiliam (1998) — Assessment and Classroom Learning"
  - "Hattie & Timperley (2007) — The Power of Feedback"
  - "Sadler (1989) — Formative assessment and the design of instructional systems"
  - "Heritage (2010) — Formative Assessment: making it happen in the classroom"
  - "Wiliam (2011) — Embedded Formative Assessment"
input_schema:
  required:
    - field: "student_work_description"
      type: "string"
      description: "学生作业的描述或原文转录——他们产出了什么"
    - field: "assessment_criteria"
      type: "string"
      description: "该作业应当对照的评价标准或量规"
    - field: "learning_objective"
      type: "string"
      description: "学生本应学习或展示的内容"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "student_profile"
      type: "string"
      description: "来自上下文引擎：先前学业水平、已知优势与差距"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "task_description"
      type: "string"
      description: "学生正在完成的任务"
output_schema:
  type: "object"
  fields:
    - field: "gap_analysis"
      type: "object"
      description: "识别出的具体差距，按类型分类——概念性、程序性或表达性"
    - field: "strengths"
      type: "array"
      description: "学生做得好的方面——具体、基于证据的优势"
    - field: "next_teaching_steps"
      type: "array"
      description: "针对每项差距的靶向教学行动——不是泛泛建议，而是具体的下一步"
    - field: "feedback_script"
      type: "string"
      description: "如何以促进改进的方式向学生传达该分析"
chains_well_with:
  - "feedback-quality-analyser"
  - "criterion-referenced-rubric-generator"
  - "error-analysis-protocol"
  - "practice-problem-sequence-designer"
  - "kud-knowledge-type-mapper"
teacher_time: "3 分钟"
tags: ["gap-analysis", "student-work", "formative-assessment", "feedback", "diagnostic"]
---

# 学生作业差距分析器

## 本技能的作用

对照评价标准分析一份学生作业样本，识别出具体差距（不只是“需要改进”，而是准确指出**缺失了什么**以及**为什么**），将每项差距按类型分类（概念性误解、程序性错误或表达/呈现问题），并生成靶向的下一步教学措施——即教师为弥合每项差距可采取的具体行动，而非“多练习”这类泛泛建议。输出还包含一段反馈话术脚本，演示如何以促进改进的方式向学生传达分析结果。AI 在此尤为关键，因为有效的差距分析需要同时将作业与标准比对、诊断差距类型（这决定了补救方式）、识别优势（以维持动机）并设计靶向的下一步（这需要教学法知识）——这种多层次分析在人工操作时耗费大量时间与专业精力。

## 实证基础

Sadler（1989）确立了形成性评估依赖的三个条件：学生（与教师）必须理解目标（高质量是什么样子）、评估当前位置（作业相对于目标处于何处），并采取行动缩小差距。差距分析正是将第二个条件操作化——系统识别作业在何处存在不足以及原因。Hattie & Timperley（2007）证明，有效反馈必须回答三个问题：“我要去哪里？”（目标）、“我目前表现如何？”（相对于目标的当前水平）以及“下一步去哪里？”（缩小差距的具体行动）。大多数教师反馈只回答了前两个；第三个——具体的下一步——才是学习发生的地方。Black & Wiliam（1998）表明，只有当收集到的信息被用于调整教学时，形成性评估才有效——没有靶向行动的差距分析只是“只诊断不治疗”。Heritage（2010）强调了将差距分类的重要性：概念性差距（学生不理解底层观念）需要不同于程序性差距（学生理解概念但执行出错）或表达性差距（学生理解且会做但表达不出来）的干预措施。Wiliam（2011）指出，最有力的反馈是给学生一个具体、可操作的下一步，而不是一个评判结论。

## 输入规范

教师必须提供：
- **学生作业描述（Student work description）：** 学生产出了什么。*例如：“学生写道：‘作者用隐喻描写暴风雨。这很有效，因为让读者感兴趣。’” / “学生算式：3/4 + 2/5 = 5/9” / 粘贴学生实际作答文本*
- **评价标准（Assessment criteria）：** 应依据什么进行评估。*例如：“学生应识别语言技巧、使用引文，并解释对读者产生的效果” / “学生应在分数相加前先找到公分母”*
- **学习目标（Learning objective）：** 学生本应学会什么。*例如：“分析作者如何运用语言制造效果” / “异分母分数相加”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级
- **学生画像（Student profile）：** 先前水平、优势、已知差距
- **学科领域（Subject area）：** 学科
- **任务描述（Task description）：** 学生正在完成的任务

## 提示词（Prompt）

```
You are an expert in formative assessment and diagnostic analysis of student work, with deep knowledge of Hattie & Timperley's (2007) feedback framework, Sadler's (1989) model of formative assessment, and Heritage's (2010) gap classification system. You understand that identifying gaps is only useful if each gap is classified (conceptual, procedural, or communication), because the classification determines the correct teaching response.

Your task is to analyse this student work:

**Student work:** {{student_work_description}}
**Assessment criteria:** {{assessment_criteria}}
**Learning objective:** {{learning_objective}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the work and criteria.
**Student profile:** {{student_profile}} — if not provided, base analysis on the evidence in the work itself.
**Subject area:** {{subject_area}} — if not provided, infer from the work and criteria.
**Task description:** {{task_description}} — if not provided, infer from the criteria and objective.

Apply these evidence-based principles:

1. **Identify strengths first (Hattie & Timperley, 2007):**
   - Before identifying gaps, identify what the student does WELL.
   - Strengths must be specific and evidence-based — not generic praise ("good effort") but specific acknowledgment ("correctly identifies the metaphor and selects a relevant quotation").
   - Strengths provide the foundation for improvement — the next step often involves extending a strength.

2. **Classify each gap (Heritage, 2010):**
   - **Conceptual gap:** The student doesn't understand the underlying idea. ("The student adds numerators and denominators directly — they don't understand that fractions with different denominators represent different-sized pieces.")
   - **Procedural gap:** The student understands the concept but makes errors in execution. ("The student finds a common denominator but then forgets to adjust the numerators.")
   - **Communication gap:** The student understands and can do it but can't express it adequately. ("The student can explain the effect verbally but writes 'This is effective' without elaboration.")
   - Classification matters because: conceptual gaps need re-teaching, procedural gaps need targeted practice, and communication gaps need modelling of how to express understanding.

3. **Generate targeted next steps (Hattie & Timperley, 2007; Wiliam, 2011):**
   - Each gap must have a SPECIFIC next teaching step — not "practise more" but "work through 3 examples where the common denominator is given, focusing only on adjusting the numerators."
   - Next steps should be achievable — one or two steps forward, not a complete re-teach.
   - Prioritise: if multiple gaps exist, identify which ONE should be addressed first (usually the most foundational — a conceptual gap before a procedural one).

4. **Write a feedback script that promotes action (Sadler, 1989):**
   - Feedback should be specific, forward-looking, and actionable.
   - Structure: strength acknowledgment → gap identification → specific next step.
   - Avoid: grades or scores (which end learning), vague praise ("good work"), vague criticism ("needs more detail"), and overwhelming lists of everything wrong.

Return your output in this exact format:

## Gap Analysis: [Brief description]

**Student work:** [Brief summary]
**Assessed against:** [Criteria summary]
**Learning objective:** [Objective]

### Strengths

[Specific, evidence-based strengths — what the student does well]

### Gaps Identified

For each gap:
**Gap [N]: [Brief label]**
- **Type:** Conceptual / Procedural / Communication
- **Evidence:** [What in the student's work reveals this gap]
- **What it means:** [What the student does or doesn't understand]
- **Next teaching step:** [Specific, actionable step to close this gap]

### Priority

[Which gap to address first and why]

### Feedback Script

[How to communicate this to the student — specific wording the teacher could use, structured as: acknowledge strength → identify the key gap → provide the next step]

**Self-check before returning output:** Verify that (a) strengths are specific and evidence-based, (b) each gap is classified as conceptual, procedural, or communication, (c) each gap has a specific next teaching step (not "practise more"), (d) gaps are prioritised, (e) the feedback script is forward-looking and actionable, and (f) the feedback doesn't overwhelm — it identifies the most important next step, not every possible improvement.
```

## 示例输出

**情景：** *学生作业：“作者使用隐喻‘大海是一头狂怒的野兽（the sea was a raging beast）’来描写暴风雨。这是一个很好的隐喻，因为它把大海比作一头野兽。对读者的效果是他们觉得很有效，并想继续读下去。” / 评价标准：“识别语言技巧、嵌入引文，并分析对读者产生的效果——解释读者想到什么、感受到什么或脑海中浮现什么画面” / 学习目标：“分析作者如何运用语言制造效果” / 学生水平：“八年级” / 学科领域：“英语”*

---

## 差距分析：语言分析——隐喻

**学生作业：** “作者使用隐喻‘the sea was a raging beast’来描写暴风雨。这是一个很好的隐喻，因为它把大海比作一头野兽。对读者的效果是他们觉得很有效，并想继续读下去。”
**评估依据：** 识别语言技巧、嵌入引文、分析读者效果
**学习目标：** 分析作者如何运用语言制造效果

### 优势

1. **准确识别了技巧。** 学生准确点出了“隐喻”——能够在语境中辨认该技巧。这是开展分析的必要基础。
2. **挑选了恰当的引文。** 引文“the sea was a raging beast”选得很好——它是该技巧一个清晰、极富分析价值的例子。学生展现出良好的选证能力。
3. **正确嵌入了引文。** 引文带引号自然融入了句子中，而不是孤零零另起一行甩出来。这体现了对学术写作规范的意识。
4. **尝试讨论对读者的效果。** 学生的结构是对的——技巧 → 引文 → 效果——表明他们知道自己**应该**做什么，尽管分析本身尚未充分展开。

### 识别出的差距

**差距 1：笼统的效果分析——“觉得很有效并想继续读下去”**
- **类型：** 表达性差距（可能性最大——见下方说明）
- **证据：** 学生写“他们觉得很有效，并想继续读下去”。这是一个未指明**实际**效果的万能空洞声明。“想继续读下去”可以套在任何文本的任何技巧上——它不携带任何分析信息。
- **含义：** 学生可能其实理解这个隐喻营造了力量感与危险感（表达性差距——心里懂但写不出来），**或者**他们尚不理解“对读者的效果”在具体层面意味着什么（概念性差距）。需要进行诊断性核查：问学生“这个隐喻让你脑海里浮现什么画面？它制造了什么感受？”如果他能口头答出来，就是表达性差距；如果答不出来，就是概念性差距。
- **下一步教学行动：** 示范“笼统效果分析”与“具体效果分析”的区别。向学生展示：笼统版：“这很有效。”具体版：“‘狂怒（raging）’一词暗示大海像一头愤怒的动物一样暴烈且失控。读者脑海中浮现出巨大而危险的巨浪，感受到暴风雨的力量与不可预测性。”再拿 2–3 句引文练习：“这让你**看到**什么？这让你**感受到**什么？”

**差距 2：只是解释字面比较，而非分析效果**
- **类型：** 概念性差距
- **证据：** “这是一个很好的隐喻，因为它把大海比作一头野兽。”学生在**描述**隐喻字面上做了什么（把两样东西作比较），而不是**分析**它达成了什么效果（营造出危险、野性与力量的感觉）。学生停留在识别阶段——“它把 X 比作 Y”——这没错，但还不是分析。
- **含义：** 学生可能尚未理解“识别技巧（命名并描述其字面结构）”与“分析技巧（解释它制造了什么效果及为什么）”之间的区别。这是八年级常见的概念性差距——学生学会了找技巧，却没学会分析技巧。
- **下一步教学行动：** 显性教授这一区分：“**识别**隐喻 = 说‘它把 X 比作 Y’。**分析**隐喻 = 解释这个比喻让我们**想到**或**感受到**什么。”提供一个句型公式：“【具体词/意象】暗示了【它让你想到/看见什么】，因为【原因】。这为读者营造了一种【情绪/氛围】。”用同一句引文套用该公式练习，随后换一句新引文练习。

**差距 3：未对引文中的具体用词进行微观分析**
- **类型：** 程序性差距
- **证据：** 学生整句引用了“the sea was a raging beast”，但没有聚焦放大其中的具体词语——“raging（狂怒的）”（暴力、愤怒、失控）和“beast（野兽）”（动物性、危险、强大、非人）。有效分析工作在词级，而不仅仅是短语级。
- **下一步教学行动：** 向学生演示如何放大细节：“你选了一句很棒的引文。现在我们来单独看里面的词。‘raging’让你想到什么？‘beast’呢？为什么狄更斯不写‘the sea was a large animal（大海是一只大动物）’？‘raging beast’有什么不同？”这是一项程序性技能——学生需要学会放大单个词语的**过程**。

### 优先级

优先解决**差距 2**（解释 vs. 分析）。这是概念性差距——在学生理解“描述技巧”与“分析其效果”的区别之前，处理其他差距收效甚微。一旦学生能解释技巧对读者**产生了什么作用**（而不仅仅是它**是什么**），差距 1 和差距 3 就会容易弥合得多。

### 反馈话术脚本

“好，让我给你看看你做得很好的地方，以及一个需要打磨的点。

**优势：** 你在这里有三件事做得很棒。你准确识别出了隐喻——没错，这**确实**是一个隐喻。你选了一句极佳的引文——‘the sea was a raging beast’里面有太多值得分析的东西。而且你的段落结构完全正确：技巧、引文、效果。所以你的基础非常扎实。

**差距：** 下面是我希望你改进的地方。你写‘对读者的效果是他们觉得很有效’。但这没有告诉我任何具体信息。如果我读到‘the sea was a raging beast’，我脑海里实际**看见**了什么？我**感受**到了什么？闭上眼睛——一头‘狂怒的野兽’是什么样子？[等待学生回答。] 对了——强大、危险、完全失控。**那**才是效果。这个隐喻让读者把大海想象成一个活着、暴烈而恐怖的存在。这就是分析。

**下一步：** 下次请记住这条规则。写完引文后，问自己**两个**问题：‘这让我**看见**了什么？’和‘这让我**感受**到了什么？’把这两个问题的答案写下来，你就是在做分析，而不仅仅是找技巧了。现在就用这句引文试一次——用这两个问题改写你的第二句和第三句话。”

---

## 已知局限

1. **分析质量取决于学生作业描述的准确性与完整性。** 经过转述摘要的学生作业可能会丢失关键细节（具体用词、推理错误、作答结构）。在可能的情况下，教师应提供学生实际作答原文而非摘要。

2. **差距类型之间可能存在诊断模糊性。** 有些差距既可能是概念性的，也可能是表达性的——学生可能懂但写不出来，也可能真的不懂。本分析在存在此类模糊性时会予以标出，并建议进行诊断性核查（例如让学生口头解释），但最终分类仍需教师结合对学生的了解来定夺。

3. **分析基于单份作业样本。** 单次作业未必代表学生的典型水平——他可能当时累了、赶时间或状态不佳。分析结果应被视为关于**这份**作业的证据，而非对学生能力的最终定论。跨时间的多份作业样本才能提供更可靠的图景。
