---
# AGENT SKILLS STANDARD FIELDS (v2)
name: checking-for-understanding-protocol-designer
description: "为课堂每个阶段设计包含具体技术的理解检查（CFU）规程。适用于在显性或直接教学过程中规划系统性的理解检测时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "explicit-instruction/checking-for-understanding-protocol-designer"
skill_name: "理解检查规程设计师"
domain: "explicit-instruction"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Rosenshine (2012) — Principles of Instruction, Principle 3: ask a large number of questions and check all student responses"
  - "Wiliam (2011) — Embedded Formative Assessment: practical strategies for checking understanding"
  - "Lemov (2015) — Teach Like a Champion 2.0: cold call, show call, and other CFU techniques"
  - "Black & Wiliam (1998) — Assessment and classroom learning: formative assessment effect size ~0.66"
  - "Christodoulou (2017) — Making Good Progress?: hinge questions and diagnostic assessment"
input_schema:
  required:
    - field: "lesson_content"
      type: "string"
      description: "本节课正在教授的内容"
    - field: "lesson_stage"
      type: "string"
      description: "何时需要理解检查：讲授过程中、引导练习后、课末或全阶段"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及班级特征"
  optional:
    - field: "class_size"
      type: "integer"
      description: "学生人数——影响技术选择"
    - field: "common_misconceptions"
      type: "array"
      description: "需要重点探测的已知常见误区"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：需要重点关注的学生、自信度模式"
    - field: "available_resources"
      type: "string"
      description: "迷你白板、电子设备、反馈卡——教室里可用的工具"
output_schema:
  type: "object"
  fields:
    - field: "cfu_techniques"
      type: "array"
      description: "为每个课堂阶段选定的技术及实施脚本"
    - field: "hinge_question"
      type: "object"
      description: "附带干扰项分析的诊断性关键节点题（hinge question）"
    - field: "cold_call_plan"
      type: "object"
      description: "附带提问句干的结构化随机点名序列"
    - field: "response_decision_tree"
      type: "string"
      description: "根据检查结果采取的行动：继续推进、重教或调整"
chains_well_with:
  - "explicit-instruction-sequence-builder"
  - "hinge-question-designer"
  - "formative-assessment-technique-selector"
  - "retrieval-practice-generator"
teacher_time: "3 分钟"
tags: ["formative-assessment", "checking-understanding", "questioning", "cold-calling", "feedback"]
---

# 理解检查规程设计师

## 本技能的作用

为特定课堂阶段生成一套适切的理解检查（CFU）技术，包括随机点名（cold-calling）脚本、迷你白板提示、离堂小测（exit tickets）以及关键节点题（hinge questions）——每项均附带实施细节以及基于结果的决策树。输出不仅告诉教师“如何”检查，更告诉教师“拿到信息后如何行动”。AI 在此尤为有价值，因为有效的理解检查需要在恰当的时机匹配恰当的技术（你不会在讲解中途使用离堂小测），并设计出能真正揭示理解而非仅仅确认学生是否在听讲的问题。实践中绝大多数理解检查只是“有问题吗？”或“大家都明白了吗？”——这什么也检查不出来。

## 循证基础

Rosenshine (2012) 将频繁检查理解列为有效教学原则第 3 条：“成功的教师会提出大量问题，检查所有学生的回答，并提供系统的反馈与纠正。” Black & Wiliam (1998) 证明，形成性评估——利用评估信息调整教学——能产生约 0.66 的效应量，但前提是教师必须根据结果采取行动。Wiliam (2011) 将形成性评估操作化为五大核心策略，其中“设计有效的课堂讨论、活动和学习任务以引出学习证据”居于核心。Lemov (2015) 提供了实用的课堂技术，包括随机点名（向未举手的学生提问，并留出思考时间）、展示点评（show call，挑选学生作业供全班分析）以及便于快速扫视全班回答的标准化作答格式。Christodoulou (2017) 深化了关键节点题（hinge questions）的概念——即通过一道诊断性问题的回答，判断学生是否已充分理解核心概念从而可以继续推进。

## 输入模式

教师必须提供：
- **Lesson content（教学内容）：** 正在教授的内容。*例如："How to calculate the area of a circle using πr²" / "The causes of the English Civil War" / "Writing a balanced argument with counter-claims"*
- **Lesson stage（课堂阶段）：** 何时需要理解检查。*例如："During instruction — I want to check before moving on" / "End of lesson — exit ticket" / "All stages — give me a full protocol"*
- **Student level（学生水平）：** 年级及班级特征。*例如："Year 7, enthusiastic but often overconfident — they say they understand when they don't"*

可选（如上下文引擎可用则自动注入）：
- **Class size（班级规模）：** 学生人数
- **Common misconceptions（常见误区）：** 需要专门探测的误区
- **Student profiles（学生档案）：** 需关注的学生、自信度-准确度模式
- **Available resources（可用资源）：** 迷你白板、电子设备、反馈卡

## Prompt

```
You are an expert in formative assessment and checking for understanding, with deep knowledge of Rosenshine's (2012) Principles of Instruction, Wiliam's (2011) formative assessment strategies, Lemov's (2015) practical CFU techniques, and Christodoulou's (2017) work on hinge questions. You understand that the purpose of CFU is not to confirm that students are paying attention — it is to gather diagnostic evidence that determines whether to proceed, re-teach, or adjust.

Your task is to design a CFU protocol for the following:

**Lesson content:** {{lesson_content}}
**Lesson stage:** {{lesson_stage}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Class size:** {{class_size}} — if not provided, design for a class of 25–30 students.
**Common misconceptions:** {{common_misconceptions}} — if not provided, identify the 2–3 most likely misconceptions for this content and design probes that surface them.
**Student profiles:** {{student_profiles}} — if not provided, assume a typical mixed-ability class with some students who overestimate their understanding.
**Available resources:** {{available_resources}} — if not provided, assume mini-whiteboards are available (the single most effective CFU resource) and no devices.

Apply these evidence-based principles:

1. **Check ALL students, not just volunteers (Rosenshine, 2012; Lemov, 2015):**
   - Hands-up questioning checks only the students who already know. It tells you nothing about the other 80%.
   - Use techniques that require ALL students to respond simultaneously: mini-whiteboards, response cards, finger voting, or written responses.
   - Cold calling (calling on students who haven't volunteered) is essential — but always give thinking time first (Wiliam, 2011). "Think for 10 seconds... [pause]... Jordan, what's your answer?"

2. **Design questions that reveal understanding, not recall (Christodoulou, 2017):**
   - "What is the formula for the area of a circle?" checks recall.
   - "The area of a circle is 50 cm². What can you tell me about the radius?" checks understanding — students must work backward and reason with the formula.
   - The best CFU questions require students to APPLY, not REPEAT.

3. **Include a hinge question (Wiliam, 2011; Christodoulou, 2017):**
   - A hinge question is a single multiple-choice question where each wrong answer reveals a specific misconception.
   - The teacher should be able to scan responses in under 30 seconds.
   - The hinge point is the decision: if 80%+ correct, proceed. If 50–80%, address the specific misconception revealed by the most common wrong answer. If below 50%, re-teach.

4. **Plan what to do with the results (Black & Wiliam, 1998):**
   - CFU without a response plan is pointless. For every check, specify:
     - What 80%+ correct means → proceed
     - What common errors mean → which misconception, and how to address it
     - What widespread confusion means → re-teach using a different approach

5. **Match technique to moment:**
   - During instruction: quick checks (cold call, finger vote, mini-whiteboard flash)
   - After guided practice: show call (project one student's work for class analysis)
   - End of lesson: exit ticket (5-minute written task that diagnoses readiness for next lesson)
   - Between lessons: review of exit ticket data to plan the following lesson

Return your output in this exact format:

## CFU Protocol: [Lesson Content]

**For:** [Student level]
**Stage:** [When checks will occur]

### During-Instruction Checks
[2–3 quick-fire checks to use while teaching, with exact questions and technique]

### Hinge Question
[A single diagnostic multiple-choice question with distractor analysis — what each wrong answer reveals]

### Cold-Call Sequence
[A scripted sequence of 3–4 cold-call questions with thinking time built in]

### End-of-Lesson Check (Exit Ticket)
[A 5-minute exit ticket with 2–3 questions that diagnose readiness for the next lesson]

### Response Decision Tree
[What to do based on CFU results — proceed, re-teach, or adjust]

**Self-check before returning output:** Verify that (a) all techniques check ALL students, not just volunteers, (b) the hinge question has distractors that map to specific misconceptions, (c) cold calls include thinking time before naming the student, (d) a response decision tree is included for every check, and (e) questions test understanding and application, not just recall.
```

## 示例输出

**场景：** *Lesson content: "Calculating the area of a circle using πr², including problems where the diameter is given instead of the radius" / Lesson stage: "All stages — full protocol" / Student level: "Year 8 Mathematics, mid-ability, tend to be overconfident — often rush and make errors with radius vs diameter"*

---

## 理解检查规程：圆的面积（πr²）

**适用对象：** 八年级数学，中等水平
**阶段：** 全阶段——完整规程

### 讲授过程中的检查

**检查 1——引入公式后（第 2 分钟）：**
*技术：迷你白板*
"Write the formula for the area of a circle on your whiteboard. Hold it up in 3... 2... 1... Show me."
- **观察重点：** A = πr²。警惕：A = πd²（用直径代替半径——核心误区）、A = 2πr（将周长与面积混淆）、A = πr（漏掉平方）。
- **如果普遍出错：** 不要直接报出正确答案。提问："I can see some boards say πd². Who can explain why the formula uses r, not d? What is the relationship between radius and diameter?" 在黑板上画出两者的区别。

**检查 2——第一道例题后（第 8 分钟）：**
*技术：手指投票*
"A circle has a diameter of 10 cm. I need to calculate the area. What is the first thing I should do? Show me: hold up 1 finger if 'multiply 10 by π', 2 fingers if 'divide 10 by 2 to get the radius', 3 fingers if 'square the 10'."
- **正确答案：** 2（先求出半径）。
- **如果多人比出 1 或 3：** 学生在直接把直径代入公式。停下来处理："If the question gives you the diameter, what must you do BEFORE you use the formula? Why?" 这是本主题中最常见的错误来源。

**检查 3——引导练习后（第 20 分钟）：**
*技术：展示点评（Show call）*
挑选两名学生在白板上的同一道题解答（一份正确，一份犯了直径/半径错误）。并排投影展示（匿名或征得同意后）。
"Which solution is correct? How do you know? Where did the error occur in the other one?"
这让常见错误对全班可见，同时不会让任何学生感到被点名批评。

### 关键节点题（Hinge Question）

**展示在黑板或屏幕上（30 秒作答）：**

一个圆的半径是 5 cm。它的面积是多少？

(A) 78.5 cm²
(B) 31.4 cm²
(C) 15.7 cm²
(D) 314 cm²

*学生用手指（或白板）举起 A、B、C 或 D。*

**干扰项分析：**

| 选项 | 揭示的问题 | 学生的计算过程 |
|--------|----------------|---------------------------|
| **(A) 78.5 cm²** | **正确** —— π × 5² = π × 25 = 78.5 | 正确应用 A = πr² |
| (B) 31.4 cm² | **周长/面积混淆** —— 学生算成了 2πr 而非 πr² | 2 × π × 5 = 31.4 |
| (C) 15.7 cm² | **漏掉平方** —— 学生算成了 πr 而非 πr² | π × 5 = 15.7 |
| (D) 314 cm² | **用直径代替半径** —— 学生先将半径翻倍，再平方 | π × 10² = 314 |

**决策：**
- 80%+ 选 A → 进入独立练习。
- 多人选 B → 停下。"Some of you got 31.4. That's the circumference, not the area. What's the difference between 2πr and πr²? Area is the space INSIDE — we need the squared formula."
- 多人选 C → 停下。"Some of you got 15.7. You used πr but forgot to square the radius. Remember: r² means r times r, so 5² is 25, not 5."
- 多人选 D → 停下。"Some of you got 314. You used the diameter (10) instead of the radius (5). The formula uses r — always check: did the question give you radius or diameter?"

### 随机点名序列（Cold-Call Sequence）

所有随机点名均遵循统一模式：提出问题 → 留出思考时间 → 然后再点名。

**Q1：** "A circle has a radius of 3 cm. Without calculating, estimate — will the area be bigger or smaller than 30 cm²? Think for 5 seconds... [停顿]... Amira, what do you think and why?"
*（考查：数感与对公式的粗略理解。π × 9 ≈ 28，因此略小于 30。）*

**Q2：** "The area of a circle is 50 cm². Is the radius bigger or smaller than 5 cm? Think for 10 seconds... [停顿]... Jayden, what's your answer?"
*（考查：从公式逆向推理。如果 r = 5，面积 = 78.5，大于 50。所以 r 必须小于 5。这需要理解，而不仅仅是套用步骤。）*

**Q3：** "I calculated the area of a circle with diameter 8 cm. I got 200.96 cm². My friend says I'm wrong. Without recalculating, can you tell me what mistake I might have made? Think for 10 seconds... [停顿]... Sophie, what do you think?"
*（考查：错误识别。200.96 = π × 8² = π × 64。错误在于使用了直径而非半径。当 r = 4 时，面积 = π × 16 = 50.27。）*

**Q4：** "Can you have a circle with an area of exactly 100 cm²? Think for 15 seconds — this is a hard one... [停顿]... Kian, what do you think?"
*（考查：深层理解。可以——r = √(100/π) ≈ 5.64 cm。如果学生在此卡壳，说明他们只能正向套用公式，尚不能灵活变形。）*

### 课末检查（离堂小测 Exit Ticket）

**5 分钟。写在纸条或练习本上。Q1–Q2 不允许使用计算器。**

**Q1.** A circle has a radius of 4 cm. Write the calculation you would do to find the area. You don't need to work out the final answer — just set up the calculation correctly.
*（考查：能否正确列出 πr²？将公式知识与算术计算剥离开。）*

**Q2.** A circle has a diameter of 12 cm. What is the radius? What calculation would you set up to find the area?
*（考查：直径转半径的换算，这是错误率最高的一步。两步设问精准定位错误发生的位置。）*

**Q3.** （允许使用计算器）A circular garden has a diameter of 6 metres. The gardener wants to buy grass seed. Each bag covers 10 m². How many bags does the gardener need?
*（考查：情境应用——必须先求面积，再向上取整为整袋数。这是考试中常见的题型。）*

**整理离堂小测：**
课后将小测纸条分为三摞：
- **已掌握（全对 3 题）：** 准备好进入下节课。给这些学生提供穿插练习（interleaved practice），将圆面积与其他图形面积计算混合。
- **部分掌握（Q1 对，Q2 或 Q3 错）：** 知道公式但在直径转换或情境应用上出错。下节课：先用 2 道快速例题练习直径转半径，再练习 Q3 类型题目。
- **尚未掌握（Q1 错）：** 尚未稳固掌握公式。下节课：在进入独立练习前，先用不同的例题简短重教。

### 响应决策树

```
理解检查结果 → 行动

讲授过程中（检查 1–3）：
├── 80%+ 正确 → 进入下一阶段
├── 50–80% 正确 → 针对最常见错误选项所揭示的具体错误进行处理（2–3 分钟重教）
└── 低于 50% → 停下。换用另一种表征方式重教（例如画出圆、涂色表示面积、实际数方格）

关键节点题：
├── 80%+ 选 A → 进入“你来做（You Do）”
├── 最常见错误为 B（周长） → 用图示重教面积与周长的区别
├── 最常见错误为 C（漏平方） → 用实物演示重教 r²（5 行每行 5 个 = 25，而不是 5）
└── 最常见错误为 D（直径） → 在黑板上画圆，测量直径和半径并重教两者关系

离堂小测（课后审阅）：
├── 80%+ 全对 → 下节课按原计划推进
├── Q2 集中出错 → 下节课开头安排 5 分钟直径转半径微课
└── Q1 集中出错 → 下节课在引入任何新内容前先重教公式
```

---

## 已知局限性

1. **理解检查技术反映的是学生“当下”能做什么，而不是他们“长期”能记住什么。** 今天答对关键节点题的学生，到下周可能已经忘记了公式。理解检查检测的是当前理解；必须与间隔提取练习（可串联使用“提取练习生成器”和“间隔练习调度器”）结合，才能确保长期保持。

2. **迷你白板和手指投票可能被学生“蒙混过关”。** 学生可能会偷看邻座答案、等看到别人举起后再亮出自己的答案，或把白板斜着举。Lemov (2015) 建议使用“听我倒数再举板——3、2、1、亮板”来减少抄袭，但没有任何技术能完全杜绝。随机点名个别学生是最有力的补充，因为它无法作弊。

3. **响应决策树需要教师在课堂上实时做出专业判断。** 决策树提供了指引，但教师必须快速决定是否重教、花多长时间重教以及何时继续推进。这是一项随着实践不断精进的专业技能——规程支持判断，但无法替代判断。
