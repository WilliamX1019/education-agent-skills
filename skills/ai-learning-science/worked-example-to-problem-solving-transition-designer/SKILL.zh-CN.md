---
# AGENT SKILLS STANDARD FIELDS (v2)
name: worked-example-to-problem-solving-transition-designer
description: "运用专业逆转效应原理，设计从样例学习向独立解题的过渡序列。适用于学生能看懂例题但无法独立解题时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/worked-example-to-problem-solving-transition-designer"
skill_name: "样例向独立解题过渡设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Kalyuga et al. (2003) — The expertise reversal effect (seminal paper)"
  - "Kalyuga (2007) — Expertise reversal effect and its implications for learner-tailored instruction"
  - "Renkl & Atkinson (2003) — Structuring the transition from example study to problem solving"
  - "Sweller et al. (2011) — Cognitive load theory (chapter on expertise reversal)"
  - "Van Merriënboer & Kirschner (2018) — Ten steps to complex learning (4C/ID model)"
input_schema:
  required:
    - field: "skill_being_taught"
      type: "string"
      description: "学生正在学习的具体技能或程序——序列结束时他们需要能独立完成的内容"
    - field: "current_student_state"
      type: "string"
      description: "学生目前所处的状态——他们已经知道什么，以及你有哪些证据证明他们当前的能力水平"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "number_of_practice_problems"
      type: "integer"
      description: "可用或现实可安排的练习题数量"
    - field: "time_available"
      type: "string"
      description: "可用于过渡序列的时间"
    - field: "assessment_format"
      type: "string"
      description: "如何评估能力——限时测试、项目、实操或其他"
output_schema:
  type: "object"
  fields:
    - field: "transition_sequence"
      type: "object"
      description: "从样例到独立解题的完整序列——包含渐隐阶段、过渡触发条件与选题逻辑"
    - field: "expertise_reversal_checkpoints"
      type: "array"
      description: "系统检查持续脚手架究竟是在帮忙还是在阻碍的具体节点"
    - field: "fading_schedule"
      type: "object"
      description: "如何逐步撤除脚手架——哪些元素先渐隐及其原因"
    - field: "independent_practice_design"
      type: "object"
      description: "独立练习阶段的设计——题型、难度递进以及学生卡住时的应对方案"
chains_well_with:
  - "digital-worked-example-sequence"
  - "adaptive-hint-sequence-designer"
  - "cognitive-tutoring-architecture-designer"
  - "productive-failure-desirable-difficulty-designer"
teacher_time: "5 分钟"
tags: ["expertise-reversal", "Kalyuga", "fading", "worked-examples", "Renkl", "transition", "scaffolding", "cognitive-load"]
---

# 样例向独立解题过渡设计器

## 本技能的作用

设计从学习样例（worked examples）向独立解题过渡的序列——即逐步撤除脚手架、由学生接管认知工作的关键阶段。这解决了认知负荷理论中最重要的发现之一：专业逆转效应（expertise reversal effect，Kalyuga et al., 2003）。当学生是初学者时，样例非常有效——它们能降低外在认知负荷，让学生建构图式。但随着学生能力提升，同样的样例会变得**冗余**，甚至实际**损害**学习——曾经帮助初学者的脚手架，如今反而阻碍了进阶学生投入推动进一步学习的主动加工。最佳教学不是固定不变的，而是**自适应的**：随着学生专业度增长，应当从样例转向独立解题。Renkl & Atkinson（2003）提出了“渐隐（fading）”方法：不搞从例题到习题的生硬切换，而是逐步从样例中移除步骤，让学生渐进地接管越来越多工作。本技能设计完整的渐隐序列，包括何时渐隐的触发条件（基于学生表现）、渐隐顺序（先移除哪些步骤），以及随后的独立练习阶段设计。

## 实证基础

Kalyuga 等人（2003）通过一系列实验证明了专业逆转效应：对初学者高度有效的教学技术，对更熟练的学习者会变得无效甚至有害。在样例语境下：学习样例的初学者显著优于直接解题的初学者（样例效应），但随着学生获得专业度，这一优势发生了逆转——更熟练的学生从独立解题中学到的比从研读样例中学到的更多。认知负荷理论对此的解释是：对初学者而言，样例减少了“手段-目的分析（试图摸索该怎么做）”的外在负荷，释放出认知资源用于图式建构。对进阶学生而言，样例制造了**冗余**——学生已经拥有图式，样例成了不必要的信息，与他们已有知识争夺加工资源。Kalyuga（2007）拓展了这项工作，指出量身定制的教学必须持续评估学习者的专业水平并相应调整教学形式。实践启示在于：不存在单一的“最佳”教学法——最佳方法取决于学习者**此时此刻**所处的位置。Renkl & Atkinson（2003）提出将渐隐作为例题到习题过渡的解决方案。他们没有在“看例题”和“做习题”之间生硬切换，而是设计了渐进过渡：先是完整样例；然后是移除一步的样例（由学生补全该步）；再是移除两步的样例；以此类推，直到学生独立解决完整问题。他们发现渐隐比固定样例或固定解题都能产生更好的学习效果，因为它持续将认知需求校准到学生不断增长的专业度上。Sweller 等人（2011）将专业逆转效应整合进更广泛的认知负荷理论框架，指出所有教学设计都必须考虑学习者当前知识与教学形式之间的**交互作用**。在学习某一阶段最优的技术，在另一阶段可能适得其反。Van Merriënboer & Kirschner（2018）开发了面向复杂学习的 4C/ID 模型，通过一系列支持度递减的任务类别，系统化设计从重度脚手架任务表现向独立表现的过渡。

## 输入规范

教师必须提供：
- **教授技能（Skill being taught）：** 学生需要独立完成的内容。*例如：“用因式分解解一元二次方程——找出因数、令每个因式等于零、解出两个根” / “撰写平衡论证议论文——带中心论点的引言、带证据的支持段、反方论证段、带权衡立场的结论” / “从频数表计算平均数、中位数和众数，并判断哪种平均数最合适”*
- **当前学生状态（Current student state）：** 学生现在处于什么水平。*例如：“学生看过教师在黑板上演示的两道样例。他们看的时候能跟上步骤，但还没有独立尝试过任何题目。部分学生仍不清楚**为什么**令每个因式等于零就能得到解” / “学生会写说服性作文（单方论证），但从未组织过平衡论证” / “学生会从原始数据算平均数，但没处理过频数表”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **练习题数量（Number of practice problems）：** 可用的题目数量
- **可用时间（Time available）：** 过渡序列的可用时长
- **评估形式（Assessment format）：** 如何检验能力

## 提示词（Prompt）

```
You are an expert in the expertise reversal effect and the transition from worked examples to problem solving, with deep knowledge of Kalyuga et al.'s (2003) expertise reversal research, Kalyuga's (2007) learner-tailored instruction principles, Renkl & Atkinson's (2003) fading approach, Sweller et al.'s (2011) cognitive load theory, and Van Merriënboer & Kirschner's (2018) 4C/ID model. You understand that the most common instructional error is using a FIXED approach (always examples, or always problems) when the optimal approach is ADAPTIVE — shifting from scaffolded examples to independent problem solving as the student's expertise grows.

CRITICAL PRINCIPLES:
- **The expertise reversal effect is real and consequential.** Continuing to provide worked examples after students have built adequate schemas REDUCES learning. The scaffolding becomes cognitive clutter that the brain must process and suppress. This is not about student preference (students often prefer continued scaffolding because it feels easier) — it's about cognitive science.
- **Fade gradually, don't switch abruptly.** Renkl & Atkinson (2003): the transition from examples to problems should be a GRADIENT, not a cliff. Remove one step at a time, starting with the LAST step (backward fading) so students complete the final step first, then the last two steps, and so on. This builds confidence and ensures each fading stage builds on the previous one.
- **Use performance to trigger fading.** The trigger for removing the next step should be PERFORMANCE-BASED: the student consistently completes the current step correctly. Do not fade on a fixed schedule — students learn at different rates. An AI system can personalise the fading; a teacher can use quick checks.
- **Independent practice must be DESIGNED, not just assigned.** Once fading is complete, the problem-solving phase needs its own design: problem difficulty should increase gradually, problems should be interleaved (not blocked by type), and students who get stuck should receive the MINIMUM help needed (not a return to full worked examples).
- **Watch for the "illusion of competence" during fading.** Students who successfully complete faded examples may FEEL more competent than they are, because the remaining worked steps are doing much of the cognitive work. True competence is demonstrated only in FULLY independent problem solving.

Your task is to design the transition sequence for:

**Skill being taught:** {{skill_being_taught}}
**Current student state:** {{current_student_state}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the skill.
**Number of practice problems:** {{number_of_practice_problems}} — if not provided, design for 8-12 problems across the full sequence.
**Time available:** {{time_available}} — if not provided, design for two 50-minute lessons.
**Assessment format:** {{assessment_format}} — if not provided, assume a timed test without scaffolding.

Return your output in this exact format:

## Worked Example to Problem Solving Transition: [Skill]

**Target skill:** [What students will do independently]
**Starting point:** [Where students are now]
**Transition approach:** [Fading method and rationale]

### Complete Transition Sequence

[The full sequence from worked example to independent problem solving, with each stage clearly defined]

**Stage [N]: [Name] — [Scaffolding level]**
- **What the student sees:** [The example/problem at this stage]
- **What the student does:** [Which steps the student completes]
- **Fading trigger:** [How to know the student is ready for the next stage]
- **Estimated problems at this stage:** [How many before moving on]

### Expertise Reversal Checkpoints

[The specific points where the system/teacher checks whether continued scaffolding is helping or hindering. Include the check method and the decision rule.]

### Fading Schedule

[Which steps are faded in which order, and why this order was chosen]

| Stage | Steps Shown | Steps Faded | Rationale |
|---|---|---|---|
| [Stage] | [Which steps the student can see] | [Which steps the student must complete] | [Why this order] |

### Independent Practice Design

[The design of the fully independent problem-solving phase — problem selection, difficulty progression, and stuck protocols]

### Common Pitfalls

[What can go wrong during the transition and how to address it]

**Self-check before returning output:** Verify that (a) fading is gradual not abrupt, (b) performance triggers the fading, (c) backward fading is used (last steps removed first), (d) expertise reversal checkpoints are included, and (e) independent practice is designed not just assigned.
```

## 示例输出

**情景：** *教授技能：“用因式分解解一元二次方程——在 x² + bx + c = 0 中找出乘积为 c 且和为 b 的两个数，写出因式形式 (x + p)(x + q) = 0，令每个因式等于零，并解出两个根” / 当前学生状态：“学生在黑板上看过两道教师示范的样例。他们能识别方程需要因式分解，也理解‘两个数乘积为 c、和为 b’的概念，但尚未独立尝试任何题目。部分学生仍不清楚**为什么**令每个因式等于零就能得到解” / 学生水平：“十年级，GCSE 高阶组” / 学科领域：“数学” / 可用时间：“一节 60 分钟的课加家庭作业” / 评估形式：“单元末测验，无脚手架，25 分钟内解 8 道一元二次方程”*

---

## 样例向独立解题过渡：因式分解解一元二次方程

**目标技能：** 独立用因式分解解 x² + bx + c = 0 形式的一元二次方程
**起点：** 学生看过 2 道样例；能跟上方法但未独立尝试；对因式分解为何能得出解存在一定困惑
**过渡方法：** 逆向渐隐（Renkl & Atkinson, 2003）——先从末尾移除步骤，让学生在接管前面步骤前先在最后阶段建立信心

### 完整过渡序列

该程序包含 4 个关键步骤：
1. **识别：** 将方程写为标准形式（x² + bx + c = 0）
2. **找因数：** 找出乘积为 c 且和为 b 的两个数
3. **写因式：** 写出因式分解形式 (x + p)(x + q) = 0
4. **求解：** 令每个因式等于零并解出 x

**第 1 阶段：带自我解释的完整样例（1 题）**

- **学生看到的内容：** 完整解答：x² + 5x + 6 = 0 → “需要乘积为 6 且和为 5 的两个数” → 2 和 3 → (x + 2)(x + 3) = 0 → x + 2 = 0 或 x + 3 = 0 → x = -2 或 x = -3
- **学生做什么：** 研读样例。在第 4 步，回答自我解释提示：“**为什么** (x + 2)(x + 3) = 0 意味着 x + 2 = 0 **或** x + 3 = 0？是什么数学规则让它成立？”（目标：若乘积为零，至少有一个因式必须为零。）
- **渐隐触发条件：** 学生能用自己的话清晰表述“零乘积性质”
- **本阶段预计题量：** 1 题

**第 2 阶段：渐隐第 4 步——学生从因式形式开始求解（2 题）**

- **学生看到的内容：** 第 1–3 步已完成：x² + 7x + 12 = 0 → 两个数是 3 和 4 → (x + 3)(x + 4) = 0 → [学生从此处接手完成]
- **学生做什么：** 令每个因式等于零并求解：x = -3 或 x = -4。这是最简单的一步——只涉及一步算术。
- **渐隐触发条件：** 学生在此阶段连续正确解出 2 题（两个因式都令为零，两个根的符号都正确）
- **本阶段预计题量：** 2–3 题

**第 3 阶段：渐隐第 3–4 步——学生写出因式形式并求解（2 题）**

- **学生看到的内容：** 第 1–2 步已完成：x² + 8x + 15 = 0 → “这两个数是 3 和 5” → [学生从此处接手完成]
- **学生做什么：** 写出 (x + 3)(x + 5) = 0，然后令每个因式等于零并求解：x = -3 或 x = -5
- **渐隐触发条件：** 学生连续 2 题正确写出因式形式**并**求解正确
- **本阶段预计题量：** 2–3 题

**第 4 阶段：渐隐第 2–4 步——学生找因数、写因式并求解（2–3 题）**

- **学生看到的内容：** 仅展示第 1 步：x² + 9x + 20 = 0 → [学生从此处接手完成]
- **学生做什么：** 找出两个数（4 和 5），写出 (x + 4)(x + 5) = 0，解得 x = -4 或 x = -5。除了识别标准形式外，学生现在完成其余全部步骤。
- **渐隐触发条件：** 学生连续 2 题正确完成包括找因数对在内的全部步骤
- **本阶段预计题量：** 2–4 题

**第 5 阶段：完全独立解题（4–6 题）**

- **学生看到的内容：** 只有方程本身：x² + 11x + 24 = 0。无脚手架。
- **学生做什么：** 从头到尾完成整个程序
- **渐隐触发条件：** 不适用——这已是目标表现。掌握标准：连续 3 题正确解答
- **本阶段预计题量：** 4–6 题（包含逐步提升的难度——见“独立练习设计”）

### 专业逆转检查点

**检查点 1（第 2 阶段后）：** 如果学生瞬间完成第 2 阶段题目且显得无聊，**跳过**第 3 阶段直接进入第 4 阶段。脚手架正在变得冗余。专业逆转的信号：学生说“这部分我早就会了”，或在读完展示步骤前就写完了渐隐步骤。

**检查点 2（第 3 阶段后）：** 如果学生第 2–3 阶段做对了但速度较慢（每题超过 2 分钟），他们可能需要再多做 1 题第 3 阶段再晋级。如果他们在 1 分钟内轻松完成，立即晋级第 4 阶段。

**检查点 3（第 5 阶段期间）：** 如果在第 3–4 阶段表现良好的学生在第 5 阶段突然卡住，**不要**把他们退回完整样例。相反，退回第 4 阶段（展示一步）做 1–2 题，然后再试第 5 阶段。遇到挫折时的恰当响应是**回退一个阶段**，而不是从头再来。

**检查点 4（第 5 阶段期间，针对不同学生）：** 对于 15 分钟内就冲到第 5 阶段的最快学生，引入**变式**：a ≠ 1 的方程（如 2x² + 7x + 3 = 0）、需要先移项整理的方程（x² + 5x = -6），或带负系数的方程。这能防止专业逆转效应：一旦掌握了简单因式分解，继续练简单题的效果不如推进到更难变式。

### 渐隐计划表

| 阶段 | 展示步骤 | 渐隐步骤（学生补全） | 理据 |
|---|---|---|---|
| 1（完整） | 全部 4 步 | 无（仅自我解释） | 学生通过研读完整程序建构图式 |
| 2 | 第 1、2、3 步 | 第 4 步（从因式求解） | 最后一步最先渐隐——认知需求最低，建立信心 |
| 3 | 第 1、2 步 | 第 3、4 步（写因式 + 求解） | 学生接管“输出”阶段，同时保留“输入”（找因数）展示 |
| 4 | 仅第 1 步 | 第 2、3、4 步（找因数 + 写因式 + 求解） | 学生承担大部分工作；仅给出标准形式 |
| 5（独立） | 无 | 全部 4 步 | 完全独立——目标状态 |

**为什么采用逆向渐隐？** 先移除**最后**一步意味着学生每次都能完成整道题——他们在每个阶段都能体验到成功（写出最终答案）。这能建立信心和动机。正向渐隐（先移除第 1 步）意味着学生开了个头却看到后面的解答——这感觉像是“被告知答案”，而不是“自己解出题目”。

### 独立练习设计

**第 5 阶段（完全独立）选题：**

| 题号 | 方程 | 新挑战 | 目的 |
|---|---|---|---|
| 1 | x² + 6x + 8 = 0 | 无——直接标准题 | 确认基础能力 |
| 2 | x² - 5x + 6 = 0 | x 项带负系数 | 检验因式分解中的符号理解 |
| 3 | x² + 2x - 15 = 0 | 常数项为负 | 需要异号因数 |
| 4 | x² - 9 = 0 | 平方差公式（无 bx 项） | 检验学生能否识别特殊情形 |
| 5 | x² + 3x = 10 | 需要先移项整理 | 检验学生能否处理非标准形式 |
| 6 | 2x² + 7x + 3 = 0 | 首项系数 ≠ 1（拓展） | 拔高——供快速掌握标准形式的学生使用 |

**卡住应对协议：** 如果学生在独立练习中卡住：
1. **首先：** 等待 60 秒。富有成效的挣扎是有价值的。
2. **如果仍卡住：** 问“你卡在了哪一步？”这个诊断问题帮助学生定位具体困难（找因数？写因式？求解？）。
3. **如果困难在第 2 步（找因数）：** 给一条**提示**，而不是例题：“哪几对数相乘等于 [c]？把它们全部写出来。现在检查哪一对相加等于 [b]。”
4. **如果是概念性困难（不懂方法）：** 退回第 4 阶段（展示一步）做 2 题，然后再试独立练习。
5. **不要退回完整样例**，除非学生明显陷入严重挫败且渐隐节奏确实过快。目标是**最小**脚手架。

### 常见陷阱

**陷阱 1：对较强学生渐隐过慢。** 如果学生在 5 分钟内轻松刷完第 1–3 阶段，他们不需要第 4 阶段——他们已经越过了专业逆转阈值。立即让他们进入第 5 阶段并引入变式。继续渐隐只会浪费他们的时间，甚至降低学习效果（Kalyuga et al., 2003）。

**陷阱 2：对挣扎学生渐隐过快。** 如果学生在第 3 阶段出错，**不要**晋级第 4 阶段。在第 3 阶段多加 1–2 题。渐隐的触发条件是**持续**正确表现，而不是“蒙对一次”。

**陷阱 3：学生死记因数组合而非方法。** 如果所有题目都用小而友好的数字（x² + 5x + 6, x² + 7x + 12），学生可能会靠目测一眼看出因数，而不理解系统方法。至少加入一道数字较大的题（x² + 17x + 72）来倒逼系统性求解。

**陷阱 4：把家庭作业和过渡混为一谈。** 家庭作业应当是**独立**练习（第 5 阶段题目），而不是更多渐隐样例。如果学生回家做渐隐样例，到考试时他们还从未独立解过一道完整题目。过渡必须在**课堂内**有支持时完成；家庭作业负责巩固独立能力。

---

## 已知局限

1. **专业逆转效应在 STEM 中已充分确立，但在其他领域研究较少。** Kalyuga 等人（2003）的研究主要在数学、科学和技术领域开展。原则可以迁移（帮助初学者的脚手架可能会阻碍专家），但在“步骤”界限不那么清晰的领域（议论文写作、历史分析、创意任务），具体的渐隐方式可能需要调适。

2. **渐隐速度的个体差异很大。** 在 30 人的班级中，有些学生 10 分钟就能到达第 5 阶段，而另一些学生在 30 分钟后仍停留在第 2 阶段。单一的全班统一渐隐进度表对一部分人会太快，对另一部分人又太慢。上述设计针对个人或小组节奏进行了优化；全班实施需要分层差异化。

3. **逆向渐隐并不总是最佳选择。** Renkl & Atkinson（2003）发现逆向渐隐对步骤序列清晰的程序性技能有效。对于线性结构不那么明显的任务（例如设计实验、组织论证），“最后一步”可能并不明确。在这些情况下，渐隐顺序需要根据具体任务结构进行调整。

4. **评估必须与目标匹配。** 如果单元末测验本身包含脚手架（公式表、步骤提示），专业逆转效应的相关性就会降低——因为评估中已经提供了脚手架。上述过渡设计假定的是**无脚手架**评估，学生必须独立完成整个程序。
