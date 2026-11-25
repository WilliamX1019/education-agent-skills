---
# AGENT SKILLS STANDARD FIELDS (v2)
name: self-explanation-prompt-designer
description: "创建自我解释提示，深化学生对样例、文本或图表的理解。适用于学生被动阅读材料、未深入思考底层原理时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/self-explanation-prompt-designer"
skill_name: "自我解释提示设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Chi et al. (1989) — Self-explanations: how students study and use examples in learning to solve problems"
  - "Chi et al. (1994) — Eliciting self-explanations improves understanding"
  - "Hausmann & VanLehn (2007) — Explaining self-explaining: a contrast between content and generation"
  - "Wylie & Chi (2014) — The self-explanation principle in multimedia learning"
  - "Rittle-Johnson (2006) — Promoting transfer: effects of self-explanation and direct instruction"
input_schema:
  required:
    - field: "learning_material"
      type: "string"
      description: "学生正在学习的具体内容——样例、文本段落、图表或学生需要深入理解的演示"
    - field: "target_understanding"
      type: "string"
      description: "学生在接触该材料后应当**深入**理解的内容——概念洞见，而不仅仅是表层信息"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "delivery_mode"
      type: "string"
      description: "自我解释提示的交付方式——嵌入文本、学习过程中由 AI 生成、教师引导或集成在辅导系统中"
    - field: "known_misconceptions"
      type: "string"
      description: "学生对该内容常持有的具体迷思概念"
output_schema:
  type: "object"
  fields:
    - field: "self_explanation_prompts"
      type: "array"
      description: "放置在材料关键节点上的具体提示——问什么以及在哪里问"
    - field: "prompt_rationale"
      type: "object"
      description: "为什么每条提示放在该位置，以及它旨在引出什么理解"
    - field: "quality_indicators"
      type: "object"
      description: "优质的自我解释与劣质复述有何区别——以便教师或 AI 评估学生回答"
    - field: "scaffolding_sequence"
      type: "object"
      description: "如何支持难以进行自我解释的学生——从开放提示过渡到更具结构化的脚手架"
chains_well_with:
  - "digital-worked-example-sequence"
  - "adaptive-hint-sequence-designer"
  - "intelligent-tutoring-dialogue-designer"
  - "metacognitive-monitoring-ai-contexts"
teacher_time: "4 分钟"
tags: ["self-explanation", "Chi", "metacognition", "worked-examples", "comprehension", "deep-learning", "generation"]
---

# 自我解释提示设计器

## 本技能的作用

设计自我解释提示——即放置在学习材料关键节点上的具体问题，促使学生**向自己解释**为什么某事为真、它如何运作或意味着什么。Chi 等人（1989）发现，在学习样例时自发进行自我解释的学生，比不这样做的学生学得明显更多；更重要的是，Chi 等人（1994）表明，被**提示**进行自我解释的学生即使原本不会自发这样做，同样会表现出显著的学习提升。自我解释效应是学习科学中最稳健的发现之一：它跨越年龄、学科和材料类型均有效。其机制在于，自我解释迫使学习者生成推论、填补空白、将新信息与已有知识连接起来，并察觉自身的困惑——所有这些都能强化理解。挑战在于如何设计出真正引出深度自我解释、而非浅层复述的提示。“为什么这一步能从上一步推导出来？”是一条好的自我解释提示；“这一步发生了什么？”则不是——它引出的是描述，而不是解释。AI 在此尤为关键，因为它能在恰当的时刻（学习过程中，而非事后）交付提示，并实时评估学生回答的质量。

## 实证基础

Chi 等人（1989）开展了关于自我解释的开创性研究，观察学生学习物理样例的过程。他们发现“优秀学生”（学得最多的人）会自发开展自我解释：他们在每一步停下来向自己解释**为什么**这一步合理、它**如何**与上一步衔接，以及它体现了**什么**原理。“薄弱学生”则被动阅读样例，只关注表面步骤而不生成解释。学习效果的差异十分悬殊——且无法用先验知识、智力或学习时间来解释。关键变量在于学习过程中的认知投入**质量**。Chi 等人（1994）检验了提示自我解释能否复制自发自我解释者的收益。他们给学生一篇生物学文本，并提示实验组逐句自我解释（“这句话提供了什么新信息？它与你已经知道的内容有何关联？”）。被提示组在即时测试和迁移测试上均显著优于对照组。这一发现具有革命性意义，因为它证明了一项简单的教学干预（提示）就能复制一种罕见认知习惯所带来的收益。Hausmann & VanLehn（2007）探究了自我解释有效的机制，发现收益来自两个成分：解释的**内容**（生成的想法）以及**生成**这一行为本身（自己产出解释，而非阅读别人给的解释）。当他们比较学生自己生成的解释与教师提供的同等质量解释时，自己生成的依然带来了更好的学习——说明是“生成”这一行为本身，而不仅仅是内容，驱动了这一效应。Wylie & Chi（2014）将自我解释研究扩展至多媒体学习，表明嵌入数字材料（视频、交互式模拟、数字文本）中的自我解释提示同样有效。他们发现提示应放在概念密度高的节点——即材料引入新原理、做出非显而易见的推论或违背常识直觉的地方。Rittle-Johnson（2006）研究了数学中的自我解释，发现自我解释提示同时提升了概念理解与程序迁移——进行自我解释的学生不仅能解出学过的题，还能将原理迁移到结构不同的新问题上。

## 输入规范

教师必须提供：
- **学习材料（Learning material）：** 学生正在学习的内容。*例如：“展示如何用配方法解一元二次方程的样例：x² + 6x + 2 = 0 → x² + 6x = -2 → x² + 6x + 9 = -2 + 9 → (x + 3)² = 7 → x + 3 = ±√7 → x = -3 ± √7” / “解释疫苗工作原理的生物文本：‘疫苗将减弱或灭活形式的病原体引入体内。免疫系统识别病原体的抗原并产生抗体。体内会生成记住该特定抗原的记忆细胞……’” / “历史史料：一幅带有特定视觉元素的一战宣传海报”*
- **目标理解（Target understanding）：** 学生应当深入理解的内容。*例如：“为什么两边要加上 9——具体来说，(b/2)² 补全了完全平方式，且这种变形让我们能够对两边开平方根” / “为什么疫苗在生病**之前**起作用——主动免疫（记忆细胞）与被动免疫的区别，以及为何减毒病原体不会致病” / “宣传画如何利用视觉技巧操纵情绪——创作者做出的具体选择以及为何这些选择具有说服力”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **交付方式（Delivery mode）：** 提示如何交付
- **已知迷思概念（Known misconceptions）：** 对该内容的常见误解

## 提示词（Prompt）

```
You are an expert in self-explanation research, with deep knowledge of Chi et al.'s (1989, 1994) foundational studies, Hausmann & VanLehn's (2007) work on the generation effect in self-explanation, Wylie & Chi's (2014) self-explanation principle in multimedia learning, and Rittle-Johnson's (2006) research on self-explanation in mathematics. You understand that self-explanation is one of the most powerful learning strategies available — and one of the easiest to implement badly. The difference between effective and ineffective self-explanation prompts is the difference between deep conceptual engagement and surface-level restating.

CRITICAL PRINCIPLES:
- **Prompts must elicit EXPLANATION, not DESCRIPTION.** "What happens in Step 3?" elicits description ("We add 9 to both sides"). "WHY do we add specifically 9 — where does 9 come from?" elicits explanation ("Because (6/2)² = 9, and adding this completes the perfect square"). The prompt must target the REASONING, not the CONTENT.
- **Place prompts at points of high conceptual density.** Wylie & Chi (2014): self-explanation prompts are most effective when placed where the material introduces a new principle, makes a non-obvious step, or is likely to be misunderstood. Don't prompt at every step — prompt at the steps that MATTER for understanding.
- **The generation is the learning.** Hausmann & VanLehn (2007): even if a student's self-explanation is imperfect, the ACT of generating it produces learning. Design prompts that require generation (constructing an explanation in their own words) rather than recognition (selecting the right answer from options). Free-response prompts > multiple choice.
- **Self-explanation prompts should be answerable.** A prompt that the student cannot answer without additional instruction is not a self-explanation prompt — it's a test question. Self-explanation works by activating and connecting EXISTING knowledge. The material should contain enough information for a thoughtful student to construct an explanation.
- **Distinguish self-explanation from other activities.** Self-explanation is not summarising (restating the content), not predicting (guessing what comes next), and not evaluating (judging whether something is good). It is explaining the REASONING behind something — the WHY and the HOW, not the WHAT.

Your task is to design self-explanation prompts for:

**Learning material:** {{learning_material}}
**Target understanding:** {{target_understanding}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the material.
**Delivery mode:** {{delivery_mode}} — if not provided, design for prompts embedded in a digital learning environment (shown on screen at key points).
**Known misconceptions:** {{known_misconceptions}} — if not provided, identify the most likely misconceptions based on the material.

Return your output in this exact format:

## Self-Explanation Prompts: [Material Description]

**Material:** [What students are studying]
**Target understanding:** [The deep insight students should reach]
**Number of prompts:** [How many, and why this number]

### Prompt Placement Map

[Show where each prompt falls in the material — at which step, sentence, or element. Explain why THAT point was chosen.]

### Self-Explanation Prompts

For each prompt:

**Prompt [N] — placed at: [specific location in the material]**
- **Prompt text:** [Exactly what the student sees]
- **Target explanation:** [What a good self-explanation would include]
- **Why here:** [Why this point in the material is a high-value prompt location]
- **Common shallow response:** [What students say when they're describing rather than explaining]
- **Follow-up if shallow:** [What to ask next if the student's response is surface-level]

### Quality Indicators

[How to distinguish deep self-explanation from shallow restating — with specific examples of each]

| Quality Level | What It Sounds Like | Example | What to Do |
|---|---|---|---|
| Deep | [Characteristics] | [Example response] | [Affirm and continue] |
| Partial | [Characteristics] | [Example response] | [Prompt for elaboration] |
| Shallow | [Characteristics] | [Example response] | [Redirect to reasoning] |

### Scaffolding Sequence

[For students who struggle to self-explain: how to move from open prompts to increasingly structured scaffolds without giving the answer]

**Self-check before returning output:** Verify that (a) prompts elicit explanation not description, (b) prompts are placed at conceptually dense points, (c) prompts require generation not recognition, (d) the material contains enough information to construct an explanation, and (e) quality indicators distinguish deep from shallow responses.
```

## 示例输出

**情景：** *学习材料：“展示如何用配方法解一元二次方程的样例：第 1 步：x² + 6x + 2 = 0。第 2 步：移项为 x² + 6x = -2。第 3 步：两边加 9：x² + 6x + 9 = -2 + 9 = 7。第 4 步：左边因式分解：(x + 3)² = 7。第 5 步：两边开平方根：x + 3 = ±√7。第 6 步：求解：x = -3 ± √7。” / 目标理解：“为什么配方法有效——具体来说，理解 (b/2)² 是将 x² + bx 转化为完全平方式的那个数，以及为什么这种转化有用（它让我们能对两边开平方根）” / 学生水平：“十一年级，GCSE 高阶组” / 已知迷思概念：“学生以为 9 是‘变魔术’变出来的——他们能照步骤做，但不明白 9 从哪来。学生在 ±√7 上也常卡住——他们会漏掉负根或不理解为什么有两个答案”*

---

## 自我解释提示：配方法

**材料：** 用配方法解 x² + 6x + 2 = 0 的样例
**目标理解：** 为什么 (b/2)² 能配成完全平方式——代数结构，而非仅仅记忆步骤
**提示数量：** 3 条——放置在概念密度最高的三个节点（第 2、3 和 5 步）

### 提示位置图谱

该样例共有 6 步。**并非**每一步都需要提示：
- **第 1 步**（写出方程）：常规步骤——无需提示。
- **第 2 步**（移项为 x² + 6x = -2）：**提示 1**——这一步做出了一个非显而易见的选择（为什么要移走 2？），它揭示了核心策略。
- **第 3 步**（两边加 9）：**提示 2**——这是**核心**概念步骤，也是最常见的困惑点。9 从哪里来？
- **第 4 步**（因式分解为 (x + 3)² = 7）：不设提示——如果学生理解了提示 2，这一步水到渠成；如果没理解，在这里提示也没用。
- **第 5 步**（开平方根，±√7）：**提示 3**——± 号在概念上至关重要且常被误解。
- **第 6 步**（解出 x）：常规步骤——无需提示。

### 自我解释提示

**提示 1——放置于：第 2 步（x² + 6x = -2）**
- **提示文本：** “我们把 +2 移到了方程另一边。**为什么**？我们想在方程左边构造出什么，为什么单独留下 x² + 6x 会有所帮助？”
- **目标解释：** “我们希望左边**只有**含 x 的项（x² + 6x），这样我们就能加上一个特定的数把它变成完全平方式。+2 会碍事，因为 x² + 6x + 2 不是完全平方式。我们需要自己控制加上的常数。”
- **为何放在这里：** 这一步看起来微不足道（“只是移个项”），但它揭示了配方法的**策略**。如果学生不明白为什么孤立 x² + 6x，后面的方法就会像魔法一样神秘。
- **常见浅层回答：** “我们移走 2 是为了把 x 留在同一边”——这只是描述了动作，没有解释目的。
- **浅层回答追问：** “但为什么我们需要让 x² + 6x 单独待在一边？如果常数项还在，我们接下来想做的什么操作会做不成？”

**提示 2——放置于：第 3 步（x² + 6x + 9 = 7）**
- **提示文本：** “我们在两边都加上了 9。解释一下：数字 9 是从哪里来的？为什么偏偏是 9，而不是 4、16 或其他任何数？”
- **目标解释：** “9 来自 (6/2)² = 3² = 9。我们取 x 的系数（即 6），除以 2（得 3），再平方（得 9）。我们用**这个**特定数字是因为 x² + 6x + 9 = (x + 3)²——它是唯一能让左边成为**完全平方式**的数。其他任何数都做不到这一点。”
- **为何放在这里：** 这是整个方法的心脏。“9 从哪来？”直接瞄准最常见的迷思概念。如果学生能解释清楚这点，他们就理解了配方法。
- **常见浅层回答：** “因为它配成了完全平方”——这是同义反复（复述方法名称而未解释机制）。
- **浅层回答追问：** “‘配成完全平方’实际上是什么意思？试试看：把 (x + 3)² 展开。你得到什么？现在对比 x² + 6x + 9。你发现了什么？”

**提示 3——放置于：第 5 步（x + 3 = ±√7）**
- **提示文本：** “我们写了 ±√7，而不仅仅是 √7。为什么有**两个**值？如果我们只写 +√7 会漏掉什么？”
- **目标解释：** “因为 (+√7)² 和 (-√7)² 都等于 7。开平方运算有两个解。如果我们只取正平方根，就会漏掉第二个解：x = -3 - √7。从几何上看，二次函数有两个根（抛物线与 x 轴交于两点），所以我们应当预期有两个答案。”
- **为何放在这里：** ± 号是一个概念绊脚石——学生经常忘记它或不理解为什么要有它。这条提示迫使他们思考数学原因，而不只是背诵符号。
- **常见浅层回答：** “因为规则就是 ±”或“老师说要加 ±”——只复述符号规定而未解释推理。
- **浅层回答追问：** “试着不写 ±。如果 x + 3 = √7，x 是多少？检验一下：这个值确实满足原方程吗？现在再试试 x + 3 = -√7。**那个**值也满足原方程吗？”

### 质量指标

| 质量水平 | 听起来像什么 | 示例 | 应对方式 |
|---|---|---|---|
| 深度 | 引用了数学**原理**——解释了“为什么”、关联到结构、用自己的话表达 | “我们加 9 是因为 (6/2)² = 9，这让 x² + 6x + 9 能因式分解成一个完全平方式。我们需要完全平方式，这样下一步才能开平方根。” | 肯定：“完全正确。你抓住了核心原理。”继续下一步。 |
| 部分 | 正确但不完整——说出了部分原因，但缺少完整逻辑链 | “9 是把 6 折半再平方得到的。” | 提示阐述：“很好——但**为什么**折半再平方能给你正确的数？把它加到 x² + 6x 上后会发生什么？” |
| 浅层 | 只描述了动作或复述了步骤名称，没有解释推理 | “两边加 9 是为了配方。” | 重定向：“你描述了我们**做了什么**，但我需要你解释**为什么**。9 具体是从哪来的？为什么不是 4 或 16？” |

### 脚手架序列

对于难以进行自我解释的学生，按以下层级递进：

**第 1 级——开放提示（默认）：** “解释为什么我们在两边加上 9。”

**第 2 级——定向提示：** “看 x 前面的数字（是 6）。试着把它折半。再把得到的结果平方。你得到什么数？这和加上的数一致吗？”

**第 3 级——验证提示：** “试着展开 (x + 3)²。你得到什么？现在把它和 x² + 6x + 9 对比。你注意到了什么？”

**第 4 级——填空提示：** “我们加上 (b/2)² 是因为 x² + bx + (b/2)² = (x + b/2)²。在这里 b = 6，所以 (b/2)² = ___。而 x² + 6x + ___ = (x + ___)²。请填空。”

该序列从最大生成度（第 1 级）过渡到最大脚手架（第 4 级）。始终从第 1 级开始——即使尝试失败，生成本身也能产生学习（Hausmann & VanLehn, 2007）。只有当学生真正卡住时才升级脚手架，而不要因为他们的解释不够完美就急着升级。

---

## 已知局限

1. **自我解释提示会拉长学习时间。** 在每一步都进行自我解释的学生，完成材料的用时明显长于被动阅读的学生。这是一种**合意困难**（Bjork, 1994）——额外时间换来了更深层的学习——但在时间紧迫的情境（考前冲刺、家庭作业）中可能带来现实困难。教师必须有意识地权衡把自我解释时间投入到哪里。

2. **自我解释的质量很难自动评估。** AI 能检测回答的**长度**以及关键词是否出现，但要判断一段自我解释是真正的深度思考（而非冗长的浅层复述），需要理解其概念内涵。当前大语言模型能近似完成此类评估，但仍可能把深刻但表达非常规的解释误判为浅层回答。

3. **自我解释最适用于概念丰富的材料。** 概念深度较浅的程序性内容（例如设置电子表格格式、规则动词变位）从自我解释提示中获益较少，因为可供**解释**的内容不多。当材料包含非显而易见的推理、隐含联系或常见迷思概念时，自我解释最为有力。

4. **学生可能需要训练才能学会自我解释。** Chi 等人（1994）发现单靠提示就有效，但其他研究表明学生在初期受益于关于“什么是好的自我解释”的专门训练。上述脚手架序列对此有所缓解，但在首次使用自我解释提示的课上，教师可能需要显性示范这一过程。
