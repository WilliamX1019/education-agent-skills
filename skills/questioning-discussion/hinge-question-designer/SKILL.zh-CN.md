---
# AGENT SKILLS STANDARD FIELDS (v2)
name: hinge-question-designer
description: "设计诊断性关键转折问题（hinge question），揭示学生是否已充分理解核心概念从而可以继续推进课程。适用于显性教学或直接教学过程中规划课中关键检查点。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "questioning-discussion/hinge-question-designer"
skill_name: "关键转折问题设计器"
domain: "questioning-discussion"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Wiliam (2011) — Embedded Formative Assessment: hinge questions as real-time diagnostic tools"
  - "Christodoulou (2017) — Making Good Progress? The future of Assessment for Learning"
  - "Black & Wiliam (1998) — Assessment and classroom learning"
  - "Sadler (1989) — Formative assessment and the design of instructional systems"
  - "Haladyna et al. (2002) — A review of multiple-choice item-writing guidelines for classroom assessment"
input_schema:
  required:
    - field: "concept_being_taught"
      type: "string"
      description: "关键转折问题所要诊断理解程度的具体概念或技能"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "lesson_context"
      type: "string"
      description: "本节课到目前为止已教授的内容——关键转折问题用于在继续推进前检查学生是否已理解"
  optional:
    - field: "known_misconceptions"
      type: "array"
      description: "教师希望干扰项重点针对的特定迷思概念"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：先前评估数据、常见知识缺口"
    - field: "response_method"
      type: "string"
      description: "学生的作答方式——如迷你白板、手指比划（A/B/C/D）、答题器、举手"
    - field: "time_constraint"
      type: "string"
      description: "学生作答的最长时间——关键转折问题应能在 2 分钟内作答"
output_schema:
  type: "object"
  fields:
    - field: "hinge_question"
      type: "object"
      description: "题干、选项及正确答案"
    - field: "diagnostic_key"
      type: "object"
      description: "每个选项所揭示的学生理解情况——每个干扰项针对的迷思概念"
    - field: "decision_guide"
      type: "string"
      description: "基于全班作答分布的决策指南——何时继续推进、重教或分层教学"
    - field: "design_rationale"
      type: "string"
      description: "问题与干扰项如此设计的原因"
chains_well_with:
  - "checking-for-understanding-protocol-designer"
  - "explicit-instruction-sequence-builder"
  - "practice-problem-sequence-designer"
  - "retrieval-practice-generator"
teacher_time: "3 分钟"
tags: ["hinge-question", "formative-assessment", "misconceptions", "diagnostic", "checking-understanding"]
---

# 关键转折问题设计器（Hinge Question Designer）

## 本技能的功能

设计一道经过精密打磨的选择题形式的关键转折问题（hinge question）——即在课堂关键节点（“转折点”）提出的一道诊断性问题，用以判断学生对核心概念的理解是否足以支持教师继续推进。与普通选择题不同，关键转折问题中的每一个错误选项都是针对特定已知迷思概念而精心设计的干扰项——因此教师不仅能知道**谁**没听懂，还能知道他们**哪里**没懂以及**为什么**没懂。输出内容包括题目本身、诊断解析键（每个选项揭示的信息）以及决策指南（根据全班作答分布采取的后续行动）。AI 在此具有独特价值，因为设计高效的关键转折问题需要同时完成多项高难度工作：识别核心概念、预测最常见的迷思概念、构建能吸引持有特定迷思的学生但**不会**误导已理解学生的干扰项，并确保正确答案无法通过错误推理蒙对。这是教学中最具挑战性的评估设计任务之一。

## 循证依据

Wiliam（2011）提出了“关键转折问题”概念，将其视为课中形成性评估最高效的形式——在课堂的“转折点”（教师必须决定继续推进还是重新讲授的时刻）提出一道精心设计的问题，使每一个作答都能提供诊断信息。其核心设计原则是：每一个错误选项都应当是持有某种特定迷思的学生会选出的答案，从而使作答分布具有可解释性。Christodoulou（2017）拓展了这一研究，指出有效的形成性评估需要那些“错误答案具有诊断价值、而不仅仅是错”的题目——“一道错误答案能告诉你原因的题目，远比一道错误答案什么也说明不了的题目更有用”。Black 与 Wiliam（1998）确立了形成性评估是教育中杠杆率最高的干预措施之一（效应量 0.4–0.7），但前提是教师必须根据评估信息采取行动——关键转折问题的格式正是为即时行动而设计的，因为作答分布能直接告诉教师下一步该做什么。Sadler（1989）指出，有效的形成性评估要求教师理解学生当前理解与目标理解之间的差距——关键转折问题让这一差距实时可见。Haladyna 等（2002）提供了编写高质量选择题的技术框架，强调决定题目诊断价值的不是题目难度，而是干扰项的质量。

## 输入规范

教师必须提供：
- **正在教授的概念：** 关键转折问题所要测试的具体概念或技能。*例如：“平均数与中位数的区别” / “心脏为什么有四个腔室” / “所有格撇号与缩写撇号的用法区分”*
- **学生水平：** 年级。*例如：“8 年级”*
- **课程情境：** 本节课到目前为止已教授的内容。*例如：“我刚刚讲解并示范了如何计算一组数据的平均数，包括两个样例。学生尚未开始独立练习。”*

可选（如情境引擎可用，将自动注入）：
- **已知迷思概念：** 教师希望重点针对的特定迷思
- **学生档案：** 先前评估数据、常见缺口
- **作答方式：** 学生如何作答（迷你白板、手指比划、答题器）
- **时间限制：** 最长作答时间（默认：2 分钟以内）

## Prompt

```
You are an expert in formative assessment design and diagnostic question construction, with deep knowledge of Wiliam's (2011) hinge question methodology, Christodoulou's (2017) work on diagnostic assessment, and Haladyna et al.'s (2002) item-writing guidelines. You understand that a hinge question is NOT just a multiple-choice quiz question — it is a precision diagnostic tool where every answer option reveals specific information about student understanding.

Your task is to design a hinge question for:

**Concept:** {{concept_being_taught}}
**Student level:** {{student_level}}
**Lesson context:** {{lesson_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Known misconceptions:** {{known_misconceptions}} — if not provided, identify the 3–4 most common misconceptions for this concept at this level and design distractors around them.
**Student profiles:** {{student_profiles}} — if not provided, design for a typical mixed-ability class.
**Response method:** {{response_method}} — if not provided, design for mini-whiteboards or finger voting (A/B/C/D).
**Time constraint:** {{time_constraint}} — if not provided, ensure the question is answerable in under 2 minutes by a student who understands the concept.

Apply these evidence-based design principles:

1. **One concept, one question (Wiliam, 2011):**
   - The question tests ONE specific concept — the one the teacher needs students to understand before moving on.
   - The question should be answerable in under 2 minutes. If it takes longer, it's testing procedure or stamina, not understanding.
   - The teacher should be able to scan all responses in under 30 seconds (this rules out open-ended responses for whole-class hinge points).

2. **Every distractor targets a specific misconception (Christodoulou, 2017):**
   - Each wrong answer must be the answer a student WOULD give if they held a particular misconception.
   - Distractors should be plausible — they should "attract" students with that misconception.
   - Random wrong answers are useless. If a student picks option C, the teacher must be able to say: "That student thinks X" — not just "That student got it wrong."
   - The correct answer should NOT be reachable through flawed reasoning. A student who holds a misconception should be attracted to a distractor, not accidentally arrive at the right answer for the wrong reason.

3. **The question must discriminate (Haladyna et al., 2002):**
   - Students who understand the concept should reliably choose the correct answer.
   - Students who don't understand should reliably choose the distractor that matches their specific misconception.
   - If the correct answer can be guessed through elimination, pattern recognition, or test-wiseness (e.g., "the longest answer is usually right"), the question fails.

4. **Design for immediate action (Black & Wiliam, 1998):**
   - The response pattern should tell the teacher exactly what to do next:
     - 80%+ correct → proceed to practice.
     - 50–80% correct → brief re-teach targeting the most common misconception, then re-check.
     - Below 50% → significant re-teach needed before proceeding.
   - Include specific guidance for each response pattern.

5. **Technical quality (Haladyna et al., 2002):**
   - The stem (question) should be clear, concise, and contain all necessary information.
   - All options should be parallel in structure, length, and grammar.
   - Avoid "all of the above" and "none of the above" — these don't provide diagnostic information.
   - Avoid negative stems ("Which is NOT...") — they test reading comprehension, not subject understanding.
   - Options should be in a logical order (numerical, alphabetical, or conceptual).

Return your output in this exact format:

## Hinge Question: [Concept]

**For:** [Student level]
**Ask this after:** [What should have been taught before asking this question]
**Estimated answer time:** [Time]

### The Question

[Question stem]

A) [Option A]
B) [Option B]
C) [Option C]
D) [Option D]

**Correct answer:** [Letter]

### Diagnostic Key

For each option:
- **[Letter]) [Option text]** — [What choosing this answer reveals about the student's understanding. For the correct answer: what understanding it confirms. For each distractor: the specific misconception it targets.]

### Decision Guide

**If 80%+ choose [correct answer]:** [What to do — typically proceed to practice]
**If many choose [distractor]:** [What specific re-teaching to do — targeting the misconception that distractor reveals]
**If responses are split across multiple distractors:** [What to do — typically a more fundamental re-teach is needed]

### Design Rationale

[Why this question tests the concept effectively. Why each distractor was chosen. Any subtleties in the design — e.g., "Option B gives the answer students get if they add instead of multiply, which is the most common procedural error at this stage."]

**Self-check before returning output:** Verify that (a) the question tests one specific concept, (b) every distractor targets a known misconception (no random wrong answers), (c) the correct answer cannot be reached through flawed reasoning, (d) the diagnostic key explains what each response reveals, (e) the question is answerable in under 2 minutes, (f) options are parallel in structure and length, and (g) the decision guide gives actionable next steps for each response pattern.
```

## 示例输出

**场景：** *概念：“计算一组数据的平均数（mean）” / 学生水平：“7 年级” / 课程情境：“我刚刚解释了平均数是通过将所有数值相加再除以数值个数来计算的。我演示了两个样例：求 3、5、7 的平均数（答案：5）以及求 10、12、8、6 的平均数（答案：9）。学生尚未独立练习。”*

---

## 关键转折问题：计算平均数

**适用对象：** 7 年级数学
**提问时机：** 教师讲解并演示平均数计算样例之后
**预计作答时间：** 60–90 秒

### 题目

五名学生在一次测验中的得分如下：

**6, 4, 8, 3, 9**

平均分是多少？

A) 5
B) 6
C) 8
D) 30

**正确答案：** B) 6

### 诊断解析键

- **A) 5** — 这是**中位数**（排序后的中间值：3, 4, 6, 8, 9）。选择此项的学生混淆了平均数与中位数——他们可能把数字排了序并选了中间的数，或者对两种“平均”概念存在总体混淆。这是平均数与中位数相近授课时最常见的错误之一。

- **B) 6** — **正确。** 学生将所有数值相加（6 + 4 + 8 + 3 + 9 = 30）并除以数值个数（30 ÷ 5 = 6）。这确认了他们掌握了两个步骤：求和**以及**除以个数。

- **C) 8** — 这是**极差**（9 – 3 = 6……等一下，不对，这是一个刻意设置的干扰项）。实际上，8 是学生**除以 4 而非除以 5** 时得到的答案——即他们数错了数值个数或漏算了一个（30 ÷ 4 = 7.5……让我重新核算）。

我需要重新设计。原数据集为 **6, 4, 8, 3, 9**。
- 总和 = 30。平均数 = 30 ÷ 5 = 6。✓
- 中位数 = 6（3, 4, 6, 8, 9 的中间值）。这会与正确答案重叠。

我需要调整数据集，使平均数与中位数不同。

**修订后的数据集：2, 3, 5, 8, 12**
- 总和 = 30。平均数 = 30 ÷ 5 = 6。
- 中位数 = 5（2, 3, 5, 8, 12 的中间值）。
- 极差 = 10（12 – 2）。

### 题目（修订版）

五名学生在一次测验中的得分如下：

**2, 3, 5, 8, 12**

平均分是多少？

A) 5
B) 6
C) 10
D) 30

**正确答案：** B) 6

### 诊断解析键

- **A) 5** — 这是**中位数**（数据排序后的中间值）。选择此项的学生混淆了平均数与中位数。他们可能理解“平均”涉及寻找一个中心值，但用错了方法——直接挑选中间的数而不是进行计算。这是学生在近期同时学过两种集中趋势度量时最常见的迷思。

- **B) 6** — **正确。** 学生将全部五个数值相加（2 + 3 + 5 + 8 + 12 = 30）并除以数值个数（30 ÷ 5 = 6）。这确认了他们对平均数计算两个组成部分的理解：全部数值求和**以及**除以个数。

- **C) 10** — 这是**极差**（12 – 2 = 10）。选择此项的学生混淆了平均数与极差——他们用最大值减去了最小值，而没有计算平均数。这种错误在知道有几种“统计量”但把名称与算法搞混的学生中很常见。这也可能表明学生只听了半节课，套用了近期学过但并不正确的步骤。

- **D) 30** — 这是**未做除法的总和**（2 + 3 + 5 + 8 + 12 = 30）。选择此项的学生完成了第一步（将所有数值相加），但忘记了或没理解第二步（除以个数）。这属于部分理解——他们知道求平均数需要相加，但不知道拿到总和后该怎么办。这是最容易干预的错误：学生需要简短重教**为什么**要除以个数（为了把总量平均分配）。

### 决策指南

**如果 80% 以上选择 B（正确）：** 进入独立练习。学生已掌握该程序。推进到改变数值个数且答案包含小数的练习题。

**如果多人选择 A（混淆中位数）：** 停下来澄清区别。“你们中有几位找出了中间的那个数——那是中位数，不是平均数。平均数是把所有数**加起来**再**平均分**。中位数是把它们排好队找**最中间**。不同的问题，不同的方法。让我把这两种并排算给你们看。”用同一组数重新演示计算两者，并清晰标注。然后换一组新数据重新提问。

**如果多人选择 D（只求和不除法）：** 简短重教第二步。“有几位同学算出了 30——你们的第一步完全正确。但平均数不是总分。这样想：如果这五名学生得分**一样高**，每人会得多少分？你们是在把 30 分平均分给 5 名学生。这就是除法的作用。”换一个更简单的例子重新提问。

**如果多人选择 C（混淆极差）：** 这表明存在标签混淆问题——学生搞混了不同统计量的名称。“有几位同学用最大的数减去了最小的数——那算出来的是极差，不是平均数。我们来把哪个词对应哪个算法彻底理清楚。”建立快速对照：平均数 = 加起来再除；中位数 = 最中间的数；极差 = 最大减最小。

**如果作答分散在 A、C 和 D：** 需要更基础的重教。学生不仅没掌握怎么算，而且对平均数“是什么”都不稳固。回到概念解释：“平均数就是如果把所有东西平均分，每个人能分到的数值。”在回到数字运算之前，先使用实物模型（在小组间平均分配圆片）进行演示。

### 设计理据

这道题作为关键转折问题之所以有效，原因在于：

1. **数字足够简单，可以心算完成**（总和 = 30，除以 5 = 6），因此题目测试的是对概念的理解，而非算术能力。理解方法的学生应在 60 秒内得出答案。

2. **每一个干扰项都是关于同一组数据的另一个问题的正确答案**——中位数（A）、极差（C）和总和（D）。这意味着每一个错误选项都能揭示学生具体混淆了哪两个统计量，或者停在了程序的哪一步。

3. **正确答案（6）并不是数据集中“显眼”或最容易记住的数字。** 它必须通过计算才能得出，不像中位数（5，就明晃晃地列在数据里）或总和（30，学生算出的第一个数）。如果不完整执行计算步骤，学生无法蒙对正确答案。

4. **数据集经过刻意挑选**，使得平均数（6）与中位数（5）不相等——如果两者相等，题目就无法区分正确计算的学生与误算成中位数的学生。

---

## 已知局限性

1. **关键转折问题只有在教师根据作答数据采取行动时才有效。** 如果教师提出了这道设计精妙的问题，看到 40% 的学生选错了，却依然按原计划往下讲，那这道题就毫无价值。决策指南为每种作答分布提供了具体行动方案，但教师必须愿意实时调整教案。这既需要灵活性，也需要教学自信——有些教师即使在数据表明应当停下来时，也很难偏离预设教案。

2. **选择题形式限制了可测查的内容。** 关键转折问题最适合那些可以通过单一选择揭示理解情况的概念——通常是事实性知识、程序性理解或概念区分。对于测试复杂推理、长篇论证或创造性应用，选择题的效果较差，因为有价值的信息在于学生的思考过程而非最终答案。对于这些技能，其他检查理解的方法（展示演算过程的迷你白板、思考-配对-分享）更为合适。

3. **干扰项设计需要对学生迷思概念的深入了解。** 关键转折问题的质量完全取决于干扰项是否精准命中了**真实学生**实际持有的**真实迷思**——而不仅仅是看起来像那么回事的错误答案。生成器利用研究文献与教学经验中的常见迷思，但特定的学生群体可能持有不同的迷思。教师应审查干扰项，并根据对自己学生典型错误的了解进行修改。如果某个干扰项并不对应班里的真实迷思，它就无法提供任何诊断信息——而只是“一个错误答案”而已。
