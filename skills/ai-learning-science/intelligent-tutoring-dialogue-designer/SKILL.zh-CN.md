---
# AGENT SKILLS STANDARD FIELDS (v2)
name: intelligent-tutoring-dialogue-designer
description: "编写多轮辅导对话脚本，为预期中的学生困难设计分支响应。适用于设计 AI 导师、聊天机器人交互或结构化一对一辅导脚本。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-learning-science/intelligent-tutoring-dialogue-designer"
skill_name: "智能辅导对话设计器"
domain: "ai-learning-science"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "VanLehn (2011) — The relative effectiveness of human tutoring, intelligent tutoring systems, and other tutoring systems (meta-analysis)"
  - "Chi et al. (2001) — Learning from human tutoring (analysis of effective tutoring dialogues)"
  - "Graesser et al. (2005) — AutoTutor: An intelligent tutoring system with mixed-initiative dialogue"
  - "Chi & Wylie (2014) — The ICAP framework: linking cognitive engagement to active learning outcomes"
  - "Koedinger & Aleven (2007) — Exploring the assistance dilemma in experiments with cognitive tutors"
input_schema:
  required:
    - field: "learning_objective"
      type: "string"
      description: "辅导交互应当帮助学生掌握的具体概念或技能"
    - field: "anticipated_difficulties"
      type: "string"
      description: "学生在该内容上通常遇到困难的具体节点——迷思概念、程序性错误或概念漏洞"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级及能力水平"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "interaction_length"
      type: "string"
      description: "辅导交互应持续多长时间"
    - field: "student_model"
      type: "string"
      description: "关于该特定学生当前知识状态的已知信息——先前表现、已知迷思概念或学习偏好"
    - field: "system_capabilities"
      type: "string"
      description: "AI 系统能做什么——仅文本、文本+图片、语音、样例、交互式题目"
output_schema:
  type: "object"
  fields:
    - field: "dialogue_architecture"
      type: "object"
      description: "辅导交互的整体结构——阶段、决策点与分支逻辑"
    - field: "dialogue_moves"
      type: "array"
      description: "导师在每个节点可采取的具体话语动作——提问、提示、解释、催促与沉默"
    - field: "decision_rules"
      type: "object"
      description: "何时使用每种动作——基于学生作答决定导师行为的规则"
    - field: "example_dialogue"
      type: "object"
      description: "展示系统与真实感学生互动的完整对话示例"
chains_well_with:
  - "adaptive-hint-sequence-designer"
  - "self-explanation-prompt-designer"
  - "ai-feedback-design-principles"
  - "cognitive-tutoring-architecture-designer"
teacher_time: "5 分钟"
tags: ["tutoring", "dialogue", "ITS", "VanLehn", "AutoTutor", "Graesser", "Chi", "ICAP", "mixed-initiative"]
---

# 智能辅导对话设计器

## 本技能的作用

为 AI 辅导交互设计对话逻辑——何时提问、何时给提示、何时解释、何时提示自我解释，以及何时保持沉默。这是智能辅导中最棘手的设计难题：干预过多会阻碍富有成效的挣扎并制造依赖；干预过少则会让学生卡住并感到沮丧。VanLehn（2011）证明，辅导（人类或 AI）的有效性取决于步骤级交互的质量——在每一步引导学生主动推理的系统，其表现大幅优于只呈现内容和评判最终答案的系统。Chi 等人（2001）分析了什么使人类辅导有效，反直觉地发现最有效的导师**不是**解释得最多的——而是最会提出恰当问题并创造机会让学生自我解释的导师。输出包括完整的对话架构（交互的阶段与分支逻辑）、对话动作库（导师可说或可做的具体动作）、决策规则（基于学生作答何时使用何种动作）以及一个展示系统实际运作的完整对话样例。AI 在此尤为关键，因为它能规模化维持一对一对话——但对话必须经过刻意设计，否则 AI 会默认进入“讲授模式”，而讲授是效率最低的辅导策略。

## 实证基础

VanLehn（2011）进行了一项全面元分析，比较了人类辅导、智能辅导系统与无辅导条件。他发现关键因素不在于**谁**在辅导，而在于**如何**辅导。“内循环（Inner loop）”系统——即在每个解题步骤提供反馈与脚手架的系统——取得了 0.76 的效应量，几乎追平人类导师（0.79）。“外循环（Outer loop）”系统——即仅评估最终答案的系统——效应量低得多（0.31）。这对对话设计的启示很明确：系统必须介入学生的推理过程，而不仅仅是最终答案。Chi 等人（2001）对有效人类辅导对话进行了细致分析，发现了一个令人惊讶的结果：最有效的导师并**没有**给出最好的解释。相反，他们采用了“先引出、再解释”的模式——先提示学生尝试解释，再基于学生产出的任何内容进行建构。这一发现直接推翻了“好辅导就是讲得清楚”的直觉假设。原因在于：当导师讲解时，学生是被动接收；当导师提问而学生尝试解释时，学生是在主动建构理解（Chi & Wylie, 2014 —— ICAP 框架）。Graesser 等人（2005）开发了 AutoTutor，这是研究最充分的智能辅导系统之一，采用“混合主动对话（mixed-initiative dialogue）”方法。AutoTutor 提出问题、评估学生作答、给予反馈并提示深入阐述——维持着对话交流而非单向讲座。他们的研究总结了五种核心对话动作：催促（pumps，“再多说说”）、提示（prompts，询问具体信息）、线索（hints，指向答案但不直接给出）、断言（assertions，提供信息）和纠正（corrections，直接指出错误）。Koedinger & Aleven（2007）阐述了“辅助两难（assistance dilemma）”——辅导设计中的根本张力。辅助过多（解释一切、过快给提示）会导致浅层学习：学生完成了任务，却不明白为什么。辅助过少（从不干预、让学生无休止挣扎）会导致沮丧与放弃。最佳辅导策略在这两个极端之间游走，提供学生取得进展所需的**最小**辅助。

## 输入规范

教师必须提供：
- **学习目标（Learning objective）：** 学生应掌握的内容。*例如：“理解为什么较重的物体并不比轻的物体下落更快（牛顿物理学 vs. 亚里士多德直觉）” / “能够识别非虚构文本中的核心论点，并将其与支撑证据区分开来” / “理解乘以一个小于 1 的分数会让数变小而不是变大”*
- **预期困难（Anticipated difficulties）：** 学生卡住的地方。*例如：“学生拥有亚里士多德式直觉，认为越重=越快。他们把日常经验（丢羽毛 vs. 丢球）当成‘证明’。他们难以将空气阻力与重力加速度区分开” / “学生混淆文本主题与论点。他们识别出的是事实而非主张。他们难以区分作者相信什么与作者报道了什么” / “学生将整数的‘乘法越乘越大’规则套用到分数上，并对 ½ × 6 = 3 感到困惑”*

可选项（如可用则由上下文引擎注入）：
- **学生水平（Student level）：** 年级与能力水平
- **学科领域（Subject area）：** 课程学科
- **交互时长（Interaction length）：** 交互持续时间
- **学生模型（Student model）：** 关于特定学生的已知信息
- **系统能力（System capabilities）：** AI 系统能够执行的功能

## 提示词（Prompt）

```
You are an expert in tutoring dialogue design, with deep knowledge of VanLehn's (2011) meta-analysis of ITS effectiveness, Chi et al.'s (2001) research on effective tutoring dialogues, Graesser et al.'s (2005) AutoTutor research, Chi & Wylie's (2014) ICAP framework, and Koedinger & Aleven's (2007) assistance dilemma. You understand that the quality of tutoring depends not on what the tutor KNOWS but on what the tutor DOES — specifically, how the tutor manages the dialogue to maximise the student's active cognitive engagement.

CRITICAL PRINCIPLES:
- **Elicit before explain.** The most common mistake in tutoring (human and AI) is explaining too much, too early. The first move should almost always be a QUESTION, not an explanation. Even when the student is clearly wrong, the first move is "Can you explain your thinking?" — not "Actually, the correct answer is..." Chi et al. (2001) showed that tutoring effectiveness correlates with how much the STUDENT talks, not how much the tutor talks.
- **Navigate the assistance dilemma.** Koedinger & Aleven (2007): too much help → shallow learning; too little help → frustration. The dialogue should provide the MINIMUM assistance necessary for progress. Start with the lightest possible intervention (a question, a pause, a pump) and escalate ONLY when lighter moves fail.
- **Use mixed-initiative dialogue.** Graesser et al. (2005): effective tutoring is a CONVERSATION, not a lecture or a quiz. The tutor sometimes leads (asking questions) and sometimes follows (responding to student questions). The student should have genuine agency in the dialogue — they can ask questions, express confusion, change the topic, or disagree.
- **Silence is a move.** One of the most powerful tutoring moves is to say nothing. After asking a question, WAIT. Students need time to think. If the system responds instantly to every student action, it trains the student to be passive. Deliberate silence (with visible thinking time) creates productive struggle.
- **Design for misconceptions, not just errors.** An error is getting the answer wrong. A misconception is having a wrong mental model. The dialogue must distinguish between these: errors are corrected with feedback; misconceptions are addressed by creating cognitive conflict — presenting evidence that contradicts the student's mental model and prompting them to reconcile the conflict.

Your task is to design the dialogue logic for:

**Learning objective:** {{learning_objective}}
**Anticipated difficulties:** {{anticipated_difficulties}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, design for a general secondary school context.
**Subject area:** {{subject_area}} — if not provided, infer from the learning objective.
**Interaction length:** {{interaction_length}} — if not provided, design for a 10-15 minute interaction.
**Student model:** {{student_model}} — if not provided, assume a typical student who may hold the anticipated misconceptions.
**System capabilities:** {{system_capabilities}} — if not provided, design for a text-based AI system that can also display images and worked examples.

Return your output in this exact format:

## Tutoring Dialogue Design: [Learning Objective]

**Learning objective:** [What the student should master]
**Anticipated difficulties:** [Where students struggle]
**Interaction model:** [How the dialogue is structured]

### Dialogue Architecture

[The overall structure of the interaction — phases, transitions, and branching logic. Include a visual flow if helpful.]

**Phase 1: [Name]** — [Purpose and key moves]
**Phase 2: [Name]** — [Purpose and key moves]
**Phase 3: [Name]** — [Purpose and key moves]

### Dialogue Move Library

[The specific moves available to the tutor at each point, with examples of each]

| Move Type | When to Use | Example |
|---|---|---|
| [Move] | [Condition] | [Exact text] |

### Decision Rules

[The rules that govern which move to use, based on student responses. Format as IF-THEN rules.]

### Example Dialogue

[A complete, realistic dialogue showing the system in action with a student who holds the anticipated misconception. Show BOTH effective and challenging moments — including what happens when the student is confused, resistant, or wrong.]

**Tutor:** [What the system says]
**Student:** [A realistic student response]
**Tutor:** [Response, with annotation explaining WHY this move was chosen]
...

### Design Rationale

[Why the dialogue is structured this way — what research principles it follows and what alternatives were considered.]

**Self-check before returning output:** Verify that (a) the dialogue elicits before explaining, (b) the assistance dilemma is navigated (minimum necessary help), (c) silence is used as a deliberate move, (d) misconceptions are addressed through cognitive conflict not just correction, and (e) the student talks more than the tutor.
```

## 示例输出

**情景：** *学习目标：“理解为什么较重的物体并不比轻的物体下落更快——重力加速度（对所有物体相同）与空气阻力（对不同物体不同）之间的区别” / 预期困难：“学生有强烈的亚里士多德式直觉，认为越重=越快。他们将日常经验（丢羽毛 vs. 丢球）引为‘证明’。他们难以将空气阻力的概念与重力加速度分离开来。即使被告知正确答案，许多人在几周后仍会退回到迷思概念” / 学生水平：“九年级，混合能力科学班” / 学科领域：“物理——力与运动”*

---

## 辅导对话设计：重力加速度 vs. 空气阻力

**学习目标：** 理解为什么较重物体并不比轻物体下落更快（重力加速度相同，空气阻力不同）
**预期困难：** 强烈的亚里士多德直觉（越重=越快）、将日常经验当作证据、将空气阻力与重力混淆
**交互模式：** 三阶段混合主动对话——引出迷思概念、制造认知冲突、建构正确模型

### 对话架构

**第一阶段：引出（3–4 分钟）**——在不纠正的前提下浮现学生现有信念。目标是让学生清晰表达其心智模型并做出明确预测。这至关重要，因为（a）你无法解决尚未浮现的迷思概念，且（b）做出明确预测能为预测被推翻时的富有成效的认知冲突创造条件。

**第二阶段：冲突（4–5 分钟）**——呈现一个与学生预测相矛盾的情景。**不要**解释为什么预测错了——要求学生自己解释这一矛盾。这一阶段是对话的核心。学生必须体验到真正的认知冲突：“我的预测错了，但我原本**确信**是对的。为什么？”导师的角色是维持这种冲突（不要过快消解它），并引导学生走向关键区分（重力 vs. 空气阻力）。

**第三阶段：建构（4–5 分钟）**——帮助学生建立正确的心智模型。使用自我解释提示确保学生能够清晰阐述重力加速度（所有物体相同）与空气阻力（取决于形状和表面积，而非质量）之间的区别。最后以一道迁移题检验模型究竟是被真正理解还是仅仅被背诵。

### 对话动作库

| 动作类型 | 何时使用 | 示例 |
|---|---|---|
| **预测请求** | 第一阶段——引出迷思概念 | “如果我把一个保龄球和一个网球从同一高度同时松手丢下，哪一个会先落地？你的预测是什么？” |
| **承诺探查** | 预测之后——强化承诺 | “你有多确定？你能解释一下**为什么**你这么认为吗？” |
| **催促（Pump）** | 当学生给出简短回答时 | “再多说说你的想法。” / “是什么让你这么认为？” |
| **冲突情景** | 第二阶段——制造认知失调 | “现在想象两个物体在一个没有空气的房间里——真空环境。你的预测还是一样吗？” |
| **沉默** | 任何提问之后——给予思考时间 | [等待 5–8 秒再回应。如果是文本系统，显示“……”或“慢慢想，不急。”] |
| **重定向** | 当学生偏离主题时 | “这点很有趣——我们待会儿再聊它。现在我想先聚焦在这件事上：为什么真空改变了结果？” |
| **苏格拉底式提问** | 第二/三阶段——引导推理 | “那么如果重力对两者的拉动是一样的，**唯一**可能让其中一个下落更慢的是什么？” |
| **自我解释提示** | 第三阶段——建构理解 | “用你自己的话解释，为什么羽毛在空气中下落很慢，但在真空中却下落得很快。” |
| **最小化纠正** | 当学生犯事实性错误时 | “实际上，重力使地球附近所有物体以相同速率加速——9.8 m/s²。但你关于空气的疑问非常重要。顺着这个思路继续想。” |
| **迁移提问** | 第三阶段末尾——检验理解 | “一名跳伞运动员和一名没有降落伞的跳伞者从同一架飞机跳下。用我们刚才讨论的内容，解释会发生什么以及为什么。” |

### 决策规则

**IF** 学生高度自信地预测“重的下落更快”：
→ **THEN** 进入第二阶段，引入真空思想实验。迷思概念已显性化且学生已承诺——非常适合制造认知冲突。

**IF** 学生预测“重的下落更快”但显得不太确定：
→ **THEN** 使用承诺探查：“有意思——能解释一下你的推理吗？”这会强化他们对预测的投入，使随后的冲突更有成效。

**IF** 学生立刻给出了正确答案：
→ **THEN** 探查其理解深度：“没错。但大多数人认为重的物体下落更快。你能解释一下**为什么**他们错了——是什么让人产生这种想法？”这检验学生是真懂还是只背住了结论。

**IF** 学生对真空情景回答正确：
→ **THEN** 使用自我解释提示：“所以你的意思是它们在真空中会以相同速度下落。这说明了关于**重力**本身的什么规律？”进入第三阶段。

**IF** 学生对真空情景感到困惑：
→ **THEN** 使用苏格拉底式提问：“你说它们在真空中速度相同，在空气中速度不同。这两种情况有什么**不同**？”引导他们识别空气阻力。

**IF** 学生沉默超过 10 秒：
→ **THEN** 提供更轻量的提问版本：“我换个方式问。在真空中没有空气。在房间里**有**空气。空气会对下落的物体产生什么影响？”

**IF** 学生提出问题：
→ **THEN** 简短回答并重定向回主线探究。不要长篇大论。“好问题——是的，地球表面附近各处的重力是一样的。那么在此前提下，为什么羽毛下落得和球不一样？”

**IF** 学生说“我不知道”或“我卡住了”：
→ **THEN** **不要**直接解释。提供脚手架：“我们一步步来想。首先：在真空中，两个物体以相同速度下落。你同意吗？”从他们**确实**知道的地方开始搭建。

### 对话示例

**导师：** 我想让你想象一个画面。你站在学校屋顶上，一只手拿着保龄球，另一只手拿着网球。你在同一时间、同一高度把它们一起松手丢下。哪一个会先落地？

**学生：** 保龄球，很明显。它更重。

**导师：** 你听起来很确定。你能解释一下为什么你认为重的那个下落更快吗？
*[承诺探查——让学生清晰表达并承诺自己的推理]*

**学生：** 因为它更重啊？就是重力拉它拉得更用力，因为它质量更大。所以它加速更快。

**导师：** 好的，所以你的推理是：质量更大 → 重力拉力更大 → 下落更快。我把你的观点记下来：“较重的物体受到更大的重力拉力，因此它们加速更快并先落地。”这样概括你的立场准确吗？
*[显性承诺——学生的预测已被正式记录，为冲突做好铺垫]*

**学生：** 对，我就是这么想的。

**导师：** 很好。现在我想让你想象同一个实验的另一个版本。同样的保龄球，同样的网球，同样的高度。但这一次，你在一个抽干了**所有**空气的房间里——一个完全真空的环境。里面只有你和这两个球。你同时松手丢下它们。会发生什么？
*[冲突情景——引入真空条件]*

**学生：** ……我觉得它们还是会以不同速度下落吧？保龄球还是更重啊。

**导师：** ……
*[沉默——6 秒。让学生带着自己的预测思考片刻。]*

**导师：** 这里有个可能会让你惊讶的事实。我们其实做过这个实验——很多次。在真空中，保龄球和网球在**完全相同**的时刻落地。每一次都是如此。你怎么看这件事？
*[呈现证伪证据，但不加解释]*

**学生：** 等等，真的吗？这说不通啊。保龄球重那么多。

**导师：** 我知道这感觉违背直觉。但事实确实如此。所以我的问题是：你预测它们会以不同速度下落，但在真空中并没有。你的预测哪里出了问题？
*[苏格拉底式提问——要求学生自己诊断错误]*

**学生：** 呃……也许就算一个更重，重力对它们的拉动也是一样的？

**导师：** 这个想法很有意思。顺着这个思路继续想。如果重力在真空中对它们的拉动是一样的，那为什么在**正常空气**中它们下落速度不同呢？
*[催促 + 重定向——学生已接近关键洞见，引导其走向空气阻力]*

**学生：** 哦……是因为空气吗？就像空气把轻的那个拖慢得更多？

**导师：** 再多说说这点。为什么空气会把其中一个拖慢得比另一个更多？
*[催促——维持学生的认知投入，不急于代劳解释]*

**学生：** 因为网球更轻，所以空气阻力对它影响更大？就像它没法那么轻松地推开空气？

**导师：** 你触及到了一个非常核心的点。让我检查一下你的理解。用你自己的话解释：为什么羽毛在空气中下落很慢，而在真空中却和锤子一样快？
*[自我解释提示——检验学生是否建构了连贯模型]*

**学生：** 因为在真空中没有空气阻力，所以只有重力起作用，而重力对所有物体的加速是一样的。但在空气中，羽毛相对于它的重量来说受到的空气阻力大得多，所以它落得慢。锤子几乎感觉不到空气的阻碍。

**导师：** 非常棒的解释。你已经指出了关键区别：重力加速度对所有物体都相同，但空气阻力因形状、表面积和质量而异。现在让我用一个新情境来检验你的理解。一名跳伞运动员和一名**没有**降落伞的跳伞者同时从同一架飞机跳下。用我们刚才讨论的原理，预测会发生什么并解释原因。
*[迁移提问——检验模型是否能够泛化]*

### 设计理据

该对话遵循基于概念转变研究的刻意三阶段结构：

1. **先引出，后纠正。** 导师花第一阶段让学生的亚里士多德信念浮现并做出承诺。这有些反直觉——许多教师会立刻说“其实它们下落速度一样”。但 Chi 等人（2001）表明，直接纠正迷思概念往往收效甚微。学生必须切身感受到预测与现实之间的冲突。

2. **认知冲突，而非直接纠正。** 第二阶段呈现一个与学生预测相矛盾的事实（真空中速度相同），然后要求**学生**来解释这一差异。导师不作解释——学生必须自己完成将预测与证据调和的认知工作。这是 ICAP 框架中投入度最高的对话模式（Chi & Wylie, 2014）。

3. **学生自主生成解释。** 到第三阶段时，学生已经通过自己的推理得出了正确解释（“是空气阻力而非重力导致了差异”）。导师的自我解释提示检验了这一理解，迁移提问检验其是否能泛化。全程学生说话都比导师多。

4. **最小辅助原则。** 导师在每个节点都使用最轻量的动作：先沉默、催促和提问，最后才考虑提示或解释。导师唯一做出的直接断言是“物体在真空中以相同速度下落”这一事实陈述——其余一切都通过提问从学生口中引出。

---

## 已知局限

1. **本技能设计的是对话“逻辑”，而非对话“系统实现”。** 将决策规则和动作库转化为可运行的 AI 系统需要工程开发（状态追踪、自然语言理解、回复生成），这超出了本技能的输出范围。该设计是一份蓝图，而非可直接部署的系统。

2. **对话一次只假设存在一个迷思概念。** 真实学生往往同时持有多个相互作用的迷思概念。既混淆质量与重量、又不理解空气阻力的学生，比上述单一迷思对话呈现出更复杂的辅导挑战。多迷思对话设计仍是研究前沿，而非已解决的问题。

3. **混合主动对话对当前 AI 系统而言难度较大。** 上述对话假定 AI 能够实时理解学生回答、识别迷思概念并选择恰当动作。当前大语言模型在许多情况下能近似做到这一点，但缺乏 AutoTutor 这类专用 ITS 系统那样可靠的状态追踪与迷思概念检测能力。部署到现有系统时可能需要简化对话。

4. **实证基础主要来自 STEM 领域。** VanLehn（2011）、Graesser 等人（2005）及 Koedinger & Aleven（2007）的研究主要在数学与科学领域开展。对话原则可迁移至其他领域（“先引出后解释”模式在人文学科同样有效），但迷思概念与认知冲突的具体模式可能不同。作文写作或历史分析中的辅导对话，在形式上会与物理辅导对话有所差异，尽管底层原则相通。

5. **在基于文本的 AI 交互中，沉默很难实现。** 对话将刻意沉默规定为一种辅导动作，但在纯文本界面中，沉默与系统卡死几乎无法区分。在聊天机器人中实施“富有成效的沉默”需要显式设计——例如可见计时器、“慢慢想”提示语，或下一条提示前的刻意延迟。
