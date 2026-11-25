---
# AGENT SKILLS STANDARD FIELDS (v2)
name: formative-assessment-technique-selector
description: "为特定的学习时刻、评估目的和年龄段选择恰当的形成性评估技术。适用于决定在课中、课间或课后如何检查理解。"
disable-model-invocation: true
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "curriculum-assessment/formative-assessment-technique-selector"
skill_name: "形成性评估技术选择器"
domain: "curriculum-assessment"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Black & Wiliam (1998) — Assessment and Classroom Learning"
  - "Wiliam (2011) — Embedded Formative Assessment"
  - "Leahy et al. (2005) — Classroom Assessment: minute by minute, day by day"
  - "Heritage (2010) — Formative Assessment: making it happen in the classroom"
  - "Wiliam & Leahy (2015) — Embedding Formative Assessment: practical techniques for K–12 classrooms"
input_schema:
  required:
    - field: "learning_moment"
      type: "string"
      description: "评估在课堂/教学序列中发生的时间点——例如教师讲解期间、引导练习后、课末、两节课之间、下节课开始时"
    - field: "what_to_assess"
      type: "string"
      description: "需要核查的具体理解、技能或知识"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "class_size"
      type: "integer"
      description: "学生人数——影响技术的实操可行性"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：EAL 学生、信心水平、特殊需求"
    - field: "available_resources"
      type: "string"
      description: "小型白板、技术设备、离堂小测纸条等"
output_schema:
  type: "object"
  fields:
    - field: "recommended_techniques"
      type: "array"
      description: "按适配度排序的 2–3 项技术，每项均附带实施指南"
    - field: "technique_rationale"
      type: "string"
      description: "为何每项技术适合这一特定时刻与目的"
    - field: "response_interpretation"
      type: "object"
      description: "如何解读作答——不同模式意味着什么以及下一步该做什么"
    - field: "common_mistakes"
      type: "string"
      description: "该技术容易如何出错以及如何避免"
chains_well_with:
  - "hinge-question-designer"
  - "checking-for-understanding-protocol-designer"
  - "exit-ticket-designer"
  - "explicit-instruction-sequence-builder"
  - "kud-knowledge-type-mapper"
teacher_time: "2 分钟"
tags: ["formative-assessment", "checking-understanding", "AfL", "feedback", "responsive-teaching"]
---

# 形成性评估技术选择器

## 本技能的作用

为特定的学习时刻——讲解过程中、引导练习后、课末或两节课之间——挑选最恰当的形成性评估技术，并提供完整的实施指南，包括如何解读作答以及根据数据结果下一步该做什么。不同于泛泛罗列形成性评估点子的清单，本技能将技术精准匹配到具体时刻、评估目的和现实约束。在课末极好用的技术（离堂小测）在教师讲解中途毫无用处；适合核查事实回忆的技术（小型白板快答）也不适合核查深层理解（后者需要解释而非单一答案）。AI 在此尤为关键，因为选择正确技术需要同时匹配评估目的（我在查什么？）、时机（在课上的哪个节点？）、作答形式（需要全班快速数据，还是少数人的深度数据？）以及现实约束（班级规模、资源、时间）。

## 实证基础

Black & Wiliam（1998）确立了形成性评估作为教育中最高杠杆干预手段之一的地位（效应量 0.4–0.7），但关键在于它是由其**功能**而非**形式**界定的：只有当收集到的证据被用来调整教学时，评估才是形成性的。发一张离堂小测却直到第二天才看，那不是形成性评估——那是延迟的终结性评估。Wiliam（2011）将形成性评估操作化为五项核心策略：明确学习意图、设计有效讨论、提供反馈、激活学生成为彼此资源，以及激活学生成为自己学习的主人。Leahy 等人（2005）将这些策略转化为实用课堂技术，强调形成性评估必须嵌入教学之中，而非外挂附加。Heritage（2010）区分了计划内形成性评估（预先设计进教案）与互动式形成性评估（课堂即兴响应），指出两者都不可或缺但服务于不同目的。Wiliam & Leahy（2015）提供了全面的实施指南，强调最好的技术能从**所有**学生收集证据，而不仅仅是举手自愿发言的学生。

## 输入规范

教师必须提供：
- **学习时刻（Learning moment）：** 位于教学序列的哪个节点。*例如：“我刚讲完如何做异分母分数加法——继续往下讲前需要检查” / “学生独立完成 5 道练习题后” / “课末——我需要知道谁懂了谁没懂” / “下节课开始——检查昨天内容的保持情况”*
- **评估内容（What to assess）：** 需要核查的具体内容。*例如：“学生能找出公分母吗？” / “学生理解为什么人物做出那个决定吗？” / “学生能把公式应用到新情境吗？”*
- **学生水平（Student level）：** 年级。*例如：“七年级”*

可选项（如可用则由上下文引擎注入）：
- **班级规模（Class size）：** 学生人数
- **学科领域（Subject area）：** 课程学科
- **学生画像（Student profiles）：** EAL、信心水平、特定需求
- **可用资源（Available resources）：** 现有教具设备

## 提示词（Prompt）

```
You are an expert in formative assessment and responsive teaching, with deep knowledge of Black & Wiliam's (1998) research on assessment for learning, Wiliam's (2011) five key strategies, Leahy et al.'s (2005) practical techniques, and Heritage's (2010) distinction between planned and interactive formative assessment. You understand that formative assessment is defined by its FUNCTION (using evidence to adapt teaching), not its FORM (any particular technique) — and that the right technique depends on the specific learning moment, the type of understanding being assessed, and the practical constraints.

Your task is to select formative assessment techniques for:

**Learning moment:** {{learning_moment}}
**What to assess:** {{what_to_assess}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Class size:** {{class_size}} — if not provided, assume 25–30 students.
**Subject area:** {{subject_area}} — if not provided, infer from the assessment focus.
**Student profiles:** {{student_profiles}} — if not provided, assume a mixed-ability class with some EAL students and some reluctant participants.
**Available resources:** {{available_resources}} — if not provided, assume mini-whiteboards are available but no technology.

Apply these evidence-based principles:

1. **Every student, not just volunteers (Wiliam, 2011):**
   - The technique must collect evidence from ALL students, not just those who raise their hands.
   - "Hands up" is NOT formative assessment — it only tells you about the 5–6 students who volunteer. It tells you nothing about the other 20–25.
   - Techniques that collect data from every student: mini-whiteboards, exit tickets, finger voting, all-student response systems, think-pair-share with reporting.

2. **Match technique to purpose (Heritage, 2010):**
   - **Checking factual knowledge:** Quick-response techniques — mini-whiteboards, finger voting, true/false cards. Speed matters; depth doesn't.
   - **Checking understanding:** Explanation-based techniques — think-pair-share, exit tickets with reasoning, hinge questions with diagnostic distractors. Depth matters; speed is secondary.
   - **Checking application:** Task-based techniques — practice problems with monitoring, worked examples with a gap, mini-tasks. Observation of process matters.
   - **Checking misconceptions:** Diagnostic techniques — hinge questions with misconception-targeted distractors, deliberate error identification tasks.

3. **Match technique to timing (Leahy et al., 2005):**
   - **During instruction (real-time):** Must be fast (under 60 seconds), non-disruptive, and provide immediate data. Mini-whiteboards, finger voting, traffic lights.
   - **After guided practice:** Must reveal whether students can apply independently. Quick practice problem, show-me task, partner explanation.
   - **End of lesson:** Must capture what students are leaving with. Exit ticket (3–5 minutes), summary task, one-sentence explanation.
   - **Between lessons:** Must check retention and inform the next lesson. Retrieval quiz at start of next lesson, homework analysis.

4. **Interpret and act (Black & Wiliam, 1998):**
   - The technique is only formative if the teacher USES the data to adapt teaching.
   - For each technique, provide: what response patterns mean, and what to DO based on each pattern.
   - 80%+ correct → proceed. 50–80% → brief re-teach. Below 50% → significant reteach needed.

5. **Avoid pseudo-formative assessment:**
   - "Thumbs up if you understand" is NOT formative assessment — students cannot accurately self-assess understanding in the moment, and social pressure ensures most thumbs go up.
   - "Any questions?" is NOT formative assessment — students who don't understand often don't know what to ask.
   - The technique must require students to DEMONSTRATE understanding, not just claim it.

Return your output in this exact format:

## Formative Assessment: [What's being assessed]

**Moment:** [When in the lesson]
**Assessing:** [Specific understanding/skill]
**For:** [Student level]

### Recommended Techniques

For each technique (2–3, ranked):

**Technique [N]: [Name]**
**How it works:** [Step-by-step implementation]
**Time required:** [Minutes]
**Why this technique for this moment:** [Specific rationale]
**What to look for:** [Specific responses that indicate understanding vs. confusion]

### Response Interpretation Guide

**If 80%+ demonstrate understanding:** [What to do]
**If 50–80% demonstrate understanding:** [What to do]
**If below 50%:** [What to do]
**If you see [specific common error]:** [What it means and what to do]

### Common Mistakes with These Techniques

[2–3 ways the technique can fail and how to prevent it]

**Self-check before returning output:** Verify that (a) the recommended technique collects data from ALL students, (b) the technique is matched to the specific learning moment and purpose, (c) the implementation guide is specific enough for a teacher to use immediately, (d) the response interpretation includes specific actions, and (e) no recommended technique relies on volunteers or self-report.
```

## 示例输出

**情景：** *学习时刻：“我刚讲完如何计算三角形面积（底 × 高 ÷ 2），并演示了两道样例。在布置练习题之前，我需要检查学生是否足够理解该方法，可以开始独立尝试。” / 评估内容：“在给定底和高的情况下，学生能否正确计算三角形面积？” / 学生水平：“七年级” / 学科领域：“数学” / 可用资源：“有小型白板”*

---

## 形成性评估：三角形面积计算

**时刻：** 教师讲解与样例演示之后、独立练习之前
**评估目标：** 给定底和高时，学生能否正确计算三角形面积？
**适用对象：** 七年级数学

### 推荐技术

**技术 1：小型白板同步亮牌（推荐）**
**操作步骤：**
1. 在黑板上展示一个底 = 8cm、高 = 5cm 的三角形。
2. 指示：“计算这个三角形的面积。在白板上写出你的计算过程。时间 60 秒。”
3. 60 秒后喊：“3、2、1，亮牌！”全班学生同时举起白板。
4. 环视全班。查看正确答案（20cm²）以及计算过程。
5. 如果时间允许，用第二个三角形（不同数字）再测一次以确认。

**所需时间：** 2–3 分钟（含跟进题）
**为何此时用此技术：** 这是一次程序性核查——学生能否正确应用公式？小型白板之所以理想，是因为它能同时收集全班每位学生的数据、展示**过程**（而不仅仅是答案），并提供即时反馈。“3、2、1，亮牌”协议能防止学生偷看抄袭——所有人同时揭示答案。
**观察重点：**
- 答案正确且过程正确（20cm²：8 × 5 = 40，40 ÷ 2 = 20）→ 学生已准备好进入练习
- 答案 40cm² → 学生做了乘法但忘了除以 2
- 答案 13cm² → 学生做了加法而非乘法（8 + 5 = 13）
- 空白白板或乱填数字 → 学生不知从何下手——没听懂样例

**技术 2：关键节点选择题的手指投票**
**操作步骤：**
1. 展示题目：“一个三角形底为 6cm，高为 4cm。它的面积是多少？”
   A) 10cm²    B) 12cm²    C) 24cm²    D) 20cm²
2. 指示：“自己思考。不要出声。我说开始时，伸出手指：1 代表 A，2 代表 B，3 代表 C，4 代表 D。”
3. “3、2、1，出！”环视全班。

**所需时间：** 1–2 分钟
**为何此时用此技术：** 比白板更快。干扰项具有诊断性：A（10）= 该乘却加；B（12）= 正确；C（24）= 乘完忘了除以 2；D（20）= 常见似是而非的错误答案。每个错误选项都暴露了一种特定错误。
**观察重点：**
- 伸出 2 根手指（B，正确：12cm²）→ 学生理解该方法
- 伸出 3 根手指（C，24cm²）→ 学生乘法做对了但忘了折半——最常见错误
- 伸出 1 根手指（A，10cm²）→ 学生把底和高相加而不是相乘

**技术 3：同伴互讲（用于核查更深层理解）**
**操作步骤：**
1. “转向你的同伴。A 同学：向 B 同学解释如何计算三角形面积。不要只报答案——解释**方法**。B 同学：认真听并核对——TA 说得对吗？”
2. 60 秒后：“B 同学——如果 A 同学解释对了，请举手。”
3. 随机点名（cold-call）2–3 位 B 同学：“你的同伴是怎么说的？”

**所需时间：** 3–4 分钟
**为何此时用此技术：** 如果你想核查学生能否**解释**方法而不仅仅是套用公式，可以使用此法。向同伴讲解比算出数字更能揭示深层理解。但它比白板更慢，提供的数据精确度也较低。
**观察重点：** 学生能否清晰说出“底乘以高，再除以 2”——还是只说“我就是 8 乘 5 除以 2”却不明白原因？留意他们能否解释“除以 2”这一步：“因为三角形是长方形的一半。”

### 作答解读指南

**如果 80%+ 展现出理解（技术 1 或 2）：** 进入独立练习。学生已准备好。布置 6–8 道难度递增的题目（包括高不是从底边垂直向上画出的三角形——这是下一个常见难点）。

**如果 50–80% 展现出理解：** 识别最常见的错误。如果大多数错误是“忘了 ÷ 2”（答 40 或 24）：进行 2 分钟简短重讲。“我看到你们很多人乘法都做对了，但漏掉了一步。看——三角形是长方形的**一半**。所以面积是底乘高的**一半**。看我再做一道。”再示范一道强调 ÷ 2 的例题，然后用白板复查。

**如果低于 50% 展现出理解：** **不要**进入独立练习——否则学生会在练习中固化错误方法。回到讲解阶段。“我看到你们很多人还不确定。没关系——这确实容易绕晕。让我从头再演示一遍。”换一种表征方式重教（例如把一个长方形沿对角线剪成两半，直观展示三角形是长方形的一半）。然后再复查。

**如果看到“该乘却加”（答 13 或 10）：** 这名学生把面积公式与周长概念混淆了。他们需要澄清：“面积是图形**里面**有多大——我们用乘法算出里面能放多少个平方厘米。周长是**外面一圈**的长度——那时候才用加法。”

### 这些技术的常见失误

1. **允许学生先后不同步举白板。** 如果学生一个接一个亮牌，后举的就会抄先举的。必须严格执行“3、2、1，亮牌”同步展示——它能防止抄袭并给你全班的真实快照。

2. **只看答案，不看过程。** 写“20cm²”的学生答案是对的，但他是算了 8 × 5 ÷ 2，还是蒙的？查看过程能区分真正理解与碰巧猜对。使用白板时，务必明确要求写出计算过程。

3. **核查完后又问“大家都懂了吗？”。** 如果白板数据显示 85% 正确，直接推进即可。不要再问一个永远只会得到“懂了”的问题来削弱刚才收集到的真实证据。相信证据，而非自我报告。

---

## 已知局限

1. **快速形成性评估技术（白板、手指投票）最适合核查程序性知识与事实回忆。** 更深层的理解——公式为什么有效、何时使用它、它如何与其他概念相连——需要更耗时的评估方法（解释任务、拓展问题、讨论）。本技能针对特定时刻推荐最恰当的技术，但有些学习目标需要 2 分钟内无法完成的评估方式。

2. **作答解读阈值（80%、50–80%、低于 50%）是指南，而非死规定。** 78% 正确的班级如果那 22% 的人都犯了同一个容易纠正的小错，可能已经可以继续推进；而 82% 正确的班级如果错的那 18% 暴露了深层迷思概念，也可能需要暂停重讲。教师必须结合情境运用专业判断解读数据。

3. **只有当教师准备好据此调整教学时，形成性评估才有效。** 技术提供数据，但价值在于响应。如果教师看了白板发现只有 60% 正确，却因为“必须赶完教学进度”而照常往下讲，他做的只是形成性核查，而不是形成性评估。根据数据调整课堂的意愿是任何技术都无法替代的核心要素。
