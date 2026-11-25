---
# AGENT SKILLS STANDARD FIELDS (v2)
name: error-analysis-protocol
description: "设计错误分析规范，用于诊断学生错误与迷思概念的根本原因。适用于学生作业中出现错误模式且需要针对性反馈的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "self-regulated-learning/error-analysis-protocol"
skill_name: "错误分析规范"
domain: "self-regulated-learning"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Borasi (1994) — Capitalizing on errors as 'springboards for inquiry': a teaching experiment"
  - "Black & Wiliam (1998) — Assessment and classroom learning (formative assessment and error use)"
  - "Metcalfe (2017) — Learning from errors: benefits of errors in the classroom"
  - "Siegler (2002) — Microgenetic studies of self-explanation: how children develop mathematical understanding"
  - "Tulis et al. (2016) — Learning from errors: a model of individual processes"
input_schema:
  required:
    - field: "student_work_sample"
      type: "string"
      description: "包含错误的学生作业描述或抄录"
    - field: "task_description"
      type: "string"
      description: "要求学生完成的任务内容及学习目标"
    - field: "subject_area"
      type: "string"
      description: "学科与年级"
  optional:
    - field: "correct_response"
      type: "string"
      description: "用于对比的正确作答示例"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：先备学业水平、已知学习困难、错误历史"
    - field: "rubric"
      type: "string"
      description: "来自情境引擎：该任务的评分量规或成功标准"
    - field: "error_frequency"
      type: "string"
      description: "该错误是偶发还是重复出现的模式"
output_schema:
  type: "object"
  fields:
    - field: "error_classification"
      type: "array"
      description: "将每处错误归类为程序性、概念性或粗心失误——并附带归类依据"
    - field: "root_cause_analysis"
      type: "string"
      description: "对每处错误根因的假设，以及用于确认的诊断性问题"
    - field: "targeted_response"
      type: "array"
      description: "针对每种错误类型的具体跟进措施"
    - field: "student_self_analysis_guide"
      type: "string"
      description: "供学生分析自身错误的脚手架提示"
chains_well_with:
  - "feedback-quality-analyser"
  - "gap-analysis-from-student-work"
  - "metacognitive-prompt-library"
  - "worked-example-fading-designer"
teacher_time: "4 分钟"
tags: ["error-analysis", "formative-assessment", "misconceptions", "diagnosis", "feedback"]
---

# 错误分析规范（Error Analysis Protocol）

## 本技能的功能

对学生错误进行结构化分析，区分程序性错误（错误地套用方法或方法本身有误）、概念性误解（由根本性迷思概念驱动的错误）以及粗心失误（理解正确但执行出错）——随后生成与每种错误类型相匹配的针对性跟进措施。关键在于，本技能还会产出一份学生自我分析脚手架，使学习者能够逐步培养自己的错误检测能力。AI 在此具有独特价值，因为大多数教师对所有错误都采取相同的回应方式（“再试一次”或“正确答案是……”），而研究表明，每种错误类型需要截然不同的应对方式——概念性错误需要重新讲授，程序性错误需要示范与练习，粗心失误则需要元认知监控。

## 循证依据

Borasi（1994）证明，当错误得到恰当分析而非仅仅被纠正时，它们会成为强有力的学习契机——“探究的跳板”，能够揭示学生思维并为教学创造切入点。Black 与 Wiliam（1998）将错误分析确立为有效形成性评估的核心组成部分，指出对错误的诊断性使用正是区分形成性评估与总结性评估的关键。Metcalfe（2017）综述了从错误中学习的益处，发现“犯错后获得纠正性反馈”比“无错学习”能产生更强的学习效果，因为错误制造了“预测违背”（prediction violation），从而加深了记忆编码——但前提是错误必须经过分析，而不仅仅是改正。Siegler（2002）运用微发生法证明，儿童数学能力的发展不仅取决于学习正确策略，更取决于理解**为什么**错误策略会失败。Tulis 等（2016）构建了个体错误加工模型，指出富有成效的错误学习需要：错误检测（注意到错误）、错误归因（识别原因）以及纠错策略（知道下次该如何不同地做）——且这三者均可通过显性教学习得。

## 输入规范

教师必须提供：
- **学生作业样本：** 包含错误的作业——描述或抄录。*例如：“学生写道：3/4 + 2/3 = 5/7。他们把分子和分母分别相加。” / “在一篇历史短文中，学生写道‘希特勒发动了一战，因为他入侵了波兰。’”*
- **任务描述：** 要求学生做什么。*例如：“计算异分母分数加法” / “解释第二次世界大战的起因”*
- **学科领域：** 学科与年级。*例如：“7 年级数学” / “10 年级历史”*

可选（如情境引擎可用，将自动注入）：
- **正确作答：** 正确作答的样子
- **学生档案：** 先备成绩、已知困难、错误历史
- **评分量规：** 该任务的成功标准
- **错误频率：** 偶发还是重复模式

## Prompt

```
You are an expert in formative assessment and error analysis, specialising in Borasi's (1994) work on errors as learning opportunities, Metcalfe's (2017) research on learning from errors, and Tulis et al.'s (2016) model of productive error processing. You understand that errors are diagnostic information, not failures to be corrected — they reveal student thinking and guide instruction.

Your task is to analyse the following student errors:

**Student work:** {{student_work_sample}}
**Task:** {{task_description}}
**Subject:** {{subject_area}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Correct response:** {{correct_response}} — if not provided, generate the correct response yourself and use it as the comparison baseline.
**Student profiles:** {{student_profiles}} — if not provided, analyse the errors at face value without individual history context.
**Rubric:** {{rubric}} — if not provided, evaluate against standard expectations for the stated year group and subject.
**Error frequency:** {{error_frequency}} — if not provided, treat each error as potentially either a one-off or a pattern and note what additional evidence would distinguish between them.

Apply these evidence-based principles:

1. **Classify each error (Siegler, 2002; Tulis et al., 2016):**
   - **Conceptual error:** The student holds a fundamental misconception that produces the error. The error is logical *given their incorrect mental model*. Correcting the surface error won't help — the underlying misconception needs addressing. Example: adding fractions by adding numerators and denominators (3/4 + 2/3 = 5/7) reveals a misconception about what fractions represent.
   - **Procedural error:** The student understands the concept but applies the wrong procedure or applies the right procedure incorrectly. They know *what* to do but not *how*. Example: correctly finding a common denominator but then forgetting to adjust the numerators.
   - **Careless/execution error:** The student understands the concept and procedure but makes an error in execution — arithmetic slip, missed negative sign, omitted word, misread question. These are inconsistent (the student gets similar problems right sometimes) and respond to metacognitive monitoring, not re-teaching.

2. **Look for the logic in the error (Borasi, 1994):** Errors are rarely random. Ask: "What would the student need to believe for this answer to make sense?" This reveals their mental model. A student who writes "5/7" for 3/4 + 2/3 is consistently applying a rule (add tops, add bottoms) — the error is logical within their incorrect schema. Understanding their logic is essential for correcting it.

3. **Match the response to the error type (Metcalfe, 2017):**
   - Conceptual errors → Re-teach the concept using a different representation. Directly confront the misconception. Use cognitive conflict (show the student why their answer can't be right).
   - Procedural errors → Provide a worked example of the correct procedure. Practice with feedback. The concept doesn't need re-teaching — just the method.
   - Careless errors → Don't re-teach. Instead, build metacognitive checking habits. Teach the student to estimate, check, and verify.

4. **Generate diagnostic questions:** For each error, generate 1–2 questions the teacher can ask the student to confirm the error classification. "Can you explain why you added the numerators?" distinguishes a conceptual error (the student has a reason based on a misconception) from a procedural error (the student says "I don't know, I thought that was the rule").

5. **Design student self-analysis:** Create scaffolded prompts that help the student analyse their own error. This builds the error-detection and attribution skills in Tulis et al.'s (2016) model.

Return your output in this exact format:

## Error Analysis: [Task/Subject]

### Error Identification
For each error found:
- **Error:** [What the student did]
- **Classification:** [Conceptual / Procedural / Careless]
- **Evidence for classification:** [Why this error is classified this way]
- **Hypothesised cause:** [What the student likely believes or is doing wrong]

### Diagnostic Questions
[Questions the teacher can ask the student to confirm the error classification and uncover the student's thinking]

### Targeted Response Plan
For each error:
- **Error type → Response type**
- **Specific action:** [Exactly what to do — not "re-teach" but how to re-teach]

### Student Self-Analysis Guide
[Scaffolded prompts for the student to analyse their own work]

### Prevention Strategy
[How to prevent this error in future instruction — what to emphasise, what examples to use]

**Self-check before returning output:** Verify that (a) each error is classified with evidence, not assumption, (b) diagnostic questions are included to confirm classifications, (c) responses are matched to error type (re-teach for conceptual, practice for procedural, metacognition for careless), (d) the student self-analysis guide scaffolds genuine reflection rather than just asking "what did you do wrong?", and (e) prevention strategies address the root cause, not just the surface error.
```

## 示例输出

**场景：** *学生作业：“题目：化简 4x + 3 + 2x - 5。学生答案：6x - 15。演算过程：4x + 2x = 6x（到此正确），然后 3 - 5 = -15。” / 任务：“通过合并同类项化简代数式” / 学科：“8 年级数学”*

---

## 错误分析：化简代数式——8 年级数学

### 错误识别

**错误 1：**
- **错误表现：** 学生算出 3 - 5 = -15（而非 -2）
- **归类：** 待定——需要诊断性提问确认。这可能是：
  - (a) **粗心/执行失误**——学生知道如何做减法，但一时疏忽（把减法当成了乘法），或者
  - (b) **概念性错误**——学生可能误以为合并同类项时要把常数相乘而不是相加减，可能是因为把合并同类项与其他运算混淆了
- **归类依据：** 学生正确合并了 x 项（4x + 2x = 6x），说明他们理解代数项合并的基本概念。常数项的出错可能是一次性笔误（3 × 5 = 15，并保留了减号带来的负号），也可能是系统性的混淆。过程写着“3 - 5 = -15”，看起来学生是把 3 × 5 算出来并保留了负号。如果这种模式反复出现（把减法算成乘法），则属于程序性错误。
- **原因假设：** 最可能的假设是学生混淆了两种运算。当他们看到“3”和“5”中间有个减号时，误做了乘法而不是减法。这可能是做题中途切换运算的程序性错误，也可能是单纯算错的粗心失误。

**错误 2（隐含信息）：**
- **表现：** 学生正确合并了 x 项，表明他们**确实**理解合并同类项的核心概念——代数部分没有问题。
- **归类：** 非错误——概念应用正确。
- **意义：** 这很关键，因为它缩小了诊断范围。学生的问题不在于“合并同类项”这个概念本身，而具体出在常数项的四则运算上，这更指向程序性或粗心失误，而非概念性错误。

### 诊断性问题

向学生提出以下问题以确认错误归类：

1. **“你能跟我讲讲你是怎么从 3 - 5 算出 -15 的吗？”**
   - 如果学生说“哎呀！我把减法算成乘法了” → **粗心失误**（他们懂程序，只是失手，提示后能自我纠正）
   - 如果学生说“合并的时候就是把数字乘起来呀” → **程序性错误**（对所需运算存在系统性误解）
   - 如果学生一脸茫然、说不出原因 → 需要进一步排查

2. **“如果先不管代数，只看纯数字计算，3 - 5 等于多少？”**
   - 如果学生说“-2” → **粗心失误**（会算，只是在代数情境中没用对）
   - 如果学生犹豫或算错 → 可能是**算术基础缺口**（问题出在负数运算上，根本不是代数问题）

3. **“帮我试做这一题：化简 5x + 7 + 3x - 2。把每一步说给我听。”**
   - 观察他们是否犯同样的错误。如果能正确算出 7 - 2 = 5 → 偶发粗心。如果再次相乘 → 系统性程序性错误。

### 针对性应对方案

**如果是粗心失误（经诊断性问题确认）：**
- **不要**重教合并同类项——学生已经会了。
- **具体行动：** 建立元认知检查习惯。每次化简后，学生应：
  1. 在原式中圈出所有常数项
  2. 把它们单独写成一道算术题（3 - 5 = ?）
  3. **先**算出算术结果，再与代数项结果合并
  4. 检查：最终答案的项数对不对？
- 给出 3 道类似练习题，要求学生在每道题上都使用这一检查流程。

**如果是程序性错误（学生说“合并时要相乘”）：**
- **具体行动：** 直接对比“合并同类项”与“乘法”。
  - “合并同类项的意思是把前面的数字**相加或相减**。4x + 2x 意思是 4 个 x 加上 2 个 x = 6 个 x。同理，+3 和 -5 意思是正 3 加上负 5 = -2。你是做加减，永远不是相乘。”
  - 给出生活类比：“如果你有 3 个苹果，别人拿走 5 个，你不会有 -15 个苹果，而是 -2 个苹果（欠 2 个）。”
  - 紧接着练习 5 道只含常数的合并题（不含 x 项），以隔离并强化正确运算。

**如果是算术缺口（学生算不出 3 - 5）：**
- **具体行动：** 问题出在负数运算，而不是代数。回到整数加减法。
  - 使用数轴：从 3 出发，向左移动 5 格，停在哪里？（-2）
  - 先练习 10 道整数减法题，再回到代数。
  - 然后回到原题，检验代数部分是否顺利通过。

### 学生自我分析指南

给学生提供以下脚手架：

---

**查找我的错误**

看看你的答案：6x - 15

**第一步：定位错误**
正确答案是 6x - 2。你的 x 项（6x）是对的，数字项（-15）不对。
看看你数字项的过程：3 - 5 = -15。

**第二步：弄清原因**
你刚才实际上做了什么计算？（圈出一项）
- 我做了减法：3 - 5 = ?
- 我做了乘法：3 × 5 = 15，然后加了负号
- 我不确定自己做了什么

**第三步：修正错误**
用数轴或这样想来计算 3 - 5：“我一开始有 3，然后拿走 5。”
3 - 5 = ___

**第四步：改正答案**
把 -15 换成你的新答案：6x + ___

**第五步：下次预防**
下一题你会采取什么不同的做法来避免这个错误？
写下一件具体的事：_______________________________________________

---

### 预防策略

**在今后教授合并同类项时：**
- 在教师示范时，明确将“合并代数项”和“常数算术计算”拆分成两个独立步骤，不要写在同一行过程里。展示如下：
  - 第一步：合并 x 项：4x + 2x = 6x
  - 第二步：合并数字项：3 - 5 = -2
  - 第三步：组合结果：6x - 2
- 练习题中要包含常数计算结果为负数的题目（这正是错误高发区）——不要只出常数相加为正数的题目。
- 讲授结束后，使用诊断性出门卡（exit ticket）：“化简 2x + 8 - 3x - 3。”该题同时测查负 x 系数和负常数结果（注：此处常数 8 - 3 = +5，x 项为 -x，即 -x + 5）。常见错误包括：5x + 5（把所有系数相加）、-x + 24（把常数相乘）、1x + 11（各种混淆）。

---

## 已知局限性

1. **错误归类需要看到学生的演算过程，而不仅仅是最终答案。** 3/4 + 2/3 得出“5/7”可能是概念性错误（对分数的错误心理模型）、程序性错误（套用了错误算法），甚至可能是抄写笔误。若无过程或诊断对话，归类只能是假设性的。诊断性问题环节至关重要——必须使用，不可跳过。

2. **本技能分析单个学生的错误，不处理全班共性错误模式。** 如果全班 80% 的学生犯了同样的错误，问题很可能出在教学上，而非学生身上。对于全班性错误模式，应对措施应当是面向全班重新讲授，而非逐个做错误分析。如需班级层面分析，请串联使用“基于学生作业的差距分析”（Gap Analysis from Student Work）。

3. **错误分析耗时较多，而时间是教学中最稀缺的资源。** 对 30 人班级里每位学生的每处错误都做详尽分析并不现实。请有选择地使用本技能——针对顽固性错误、令人意外的错误或多名学生共有的错误。若要快速识别全班作业中的常见错误，全班诊断工具（出门卡、关键转折问题）比个体错误分析更高效。
