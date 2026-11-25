---
# AGENT SKILLS STANDARD FIELDS (v2)
name: socratic-questioning-sequence-generator
description: "生成苏格拉底式提问序列，通过引导式探究发展概念理解。适用于组织哲学讨论、概念探索或批判性审视的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "questioning-discussion/socratic-questioning-sequence-generator"
skill_name: "苏格拉底式提问序列生成器"
domain: "questioning-discussion"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Paul & Elder (2008) — The Miniature Guide to Critical Thinking Concepts and Tools"
  - "Chin (2007) — Teacher questioning in science classrooms: approaches that stimulate productive thinking"
  - "Walsh & Sattes (2005) — Quality Questioning: research-based practice to engage every learner"
  - "Nystrand et al. (1997) — Opening Dialogue: authentic questions and their effects on student engagement"
  - "Dillon (1988) — Questioning and Teaching: a manual of practice"
input_schema:
  required:
    - field: "concept_to_develop"
      type: "string"
      description: "需要通过提问发展出来的概念、观点或理解"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及对该概念的熟悉程度"
    - field: "starting_point"
      type: "string"
      description: "学生目前对该概念的理解或认知起点"
  optional:
    - field: "target_understanding"
      type: "string"
      description: "提问序列应引导向的具体理解或顿悟"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：口头表达自信度、围绕提问的文化因素"
    - field: "time_available"
      type: "string"
      description: "可用于该提问序列的分钟数"
    - field: "subject_area"
      type: "string"
      description: "学科背景，以适配符合学科规范的提问方式"
output_schema:
  type: "object"
  fields:
    - field: "question_sequence"
      type: "array"
      description: "带有类型标签和预期回答的有序问题序列"
    - field: "follow_up_branches"
      type: "object"
      description: "基于可能的学生回答而设计的权变跟进问题"
    - field: "facilitation_notes"
      type: "string"
      description: "如何把控对话——候答时间、处理错误回答、保持讨论推进动力"
    - field: "socratic_vs_leading"
      type: "string"
      description: "区分本序列中苏格拉底式提问与诱导性提问的说明"
chains_well_with:
  - "discussion-protocol-selector"
  - "dialogic-teaching-move-generator"
  - "hinge-question-designer"
  - "elaborative-interrogation-generator"
  - "ai-socratic-dialogue-designer"
teacher_time: "4 分钟"
tags: ["questioning", "Socratic", "critical-thinking", "dialogue", "reasoning"]
---

# 苏格拉底式提问序列生成器（Socratic Questioning Sequence Generator）

## 本技能的功能

生成一套渐进式提问序列，旨在通过对话而非直接讲授来发展概念——使学生通过自身推理，从当前理解走向更深入或更细腻的立场。该序列严格区分真正的苏格拉底式提问（探究推理、揭示隐含假设、通过学生自主思考发展理解）与诱导性提问（通过不断收窄选项将学生引向预设的标准答案）。AI 在此具有独特价值，因为设计真正的苏格拉底式序列需要预判多种可能的学生回答，并为每种回答准备相应的权变跟进问题，从而构建出一棵大多数教师难以在课堂上即时搭建的分支对话树。

## 循证依据

Paul 与 Elder（2008）将苏格拉底式问题划分为六种类型：澄清类问题、探究假设类问题、探究理由与证据类问题、观点与视角类问题、探究推论与后果类问题，以及关于问题本身的问题。每种类型在深化思考中都发挥着独特作用。Chin（2007）研究了科学课堂中的教师提问，发现尽管高认知需求的问题能激发更多学生推理和更长、更详尽的回答，但大多数教师提问仍停留在低阶记忆回忆层面（占 60%–80%）。Nystrand 等（1997）识别出“真实性问题”（authentic questions）——即教师并没有预设唯一答案的问题——是预测学生参与度和对话式话语的最强指标。Walsh 与 Sattes（2005）证明，候答时间（wait time，提出问题后保持 3–5 秒的沉默）能显著提升学生回答的长度与质量。Dillon（1988）确立了一个核心规律：课堂对话的质量更多取决于教师回应学生回答的能力，而非初始问题本身——跟进策略才是苏格拉底式对话成败的关键。

## 输入规范

教师必须提供：
- **要发展的概念：** 通过提问来建构的观点或理解。*例如：“诗歌中的叙述者是否就是诗人本人” / “为什么不能靠多印钞票来消除贫困” / “科学实验是否‘公平’”*
- **学生水平：** 年级与熟悉程度。*例如：“9 年级，读过这首诗，但默认叙述者就是诗人” / “8 年级，知道货币存在，但未学过经济学”*
- **认知起点：** 学生目前的想法。*例如：“学生认为诗人在描述自己的亲身经历” / “学生认为多印钱就能解决贫困”*

可选（如情境引擎可用，将自动注入）：
- **目标理解：** 提问应引导向的方向
- **学生档案：** 口头表达自信度、围绕提问的文化因素
- **可用时间：** 提问序列的可用分钟数
- **学科领域：** 学科背景

## Prompt

```
You are an expert in Socratic questioning and dialogic pedagogy, with deep knowledge of Paul & Elder's (2008) six types of Socratic questions, Chin's (2007) research on productive questioning in classrooms, and Nystrand et al.'s (1997) work on authentic questions. You understand the critical distinction between Socratic questioning (which develops thinking through genuine inquiry) and leading questioning (which funnels students toward a predetermined answer through narrowing choices).

Your task is to generate a Socratic questioning sequence for:

**Concept:** {{concept_to_develop}}
**Student level:** {{student_level}}
**Starting point:** {{starting_point}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Target understanding:** {{target_understanding}} — if not provided, design the sequence to deepen and complicate students' current understanding rather than leading to a single "correct" conclusion. The sequence should surface complexity, not converge on one answer.
**Student profiles:** {{student_profiles}} — if not provided, assume a typical mixed-ability class where some students are verbally confident and others rarely speak in whole-class discussion.
**Time available:** {{time_available}} — if not provided, design for 12–15 minutes of questioning.
**Subject area:** {{subject_area}} — if not provided, infer from the concept and adapt questioning to discipline-appropriate reasoning.

Apply these evidence-based principles:

1. **Use Paul & Elder's (2008) six question types strategically:**
   - **Clarification:** "What do you mean by...?" / "Can you give an example?" — use early to establish shared understanding.
   - **Probing assumptions:** "What are you assuming when you say that?" / "Is that always true?" — use to surface unstated beliefs.
   - **Probing reasons and evidence:** "What evidence supports that?" / "How do you know?" — use to demand justification.
   - **Viewpoints and perspectives:** "How might someone who disagrees see this?" / "Is there another way to look at it?" — use to introduce complexity.
   - **Implications and consequences:** "If that's true, what follows?" / "What would happen if...?" — use to extend reasoning.
   - **Questions about the question:** "Why is this question important?" / "What makes this hard to answer?" — use to develop metacognitive awareness.

2. **Sequence from concrete to abstract:**
   - Start with questions about specific, concrete examples students can engage with.
   - Progress to questions that require generalisation, abstraction, or principle identification.
   - End with questions that apply the developed understanding to new situations or identify remaining uncertainties.

3. **Distinguish Socratic from leading (Nystrand et al., 1997):**
   - A Socratic question is one where the teacher is genuinely interested in the student's reasoning, even if the teacher has more knowledge. Multiple answers are possible and the teacher follows the student's thinking.
   - A leading question narrows options to funnel toward a single answer the teacher has in mind. "Don't you think that...?" and "Isn't it true that...?" are leading, not Socratic.
   - The sequence should be GENUINELY exploratory — students should feel they are thinking, not guessing what the teacher wants.

4. **Anticipate responses and branch (Dillon, 1988):**
   - For each question, anticipate 2–3 likely student responses.
   - For each response, provide a follow-up question that builds on what the student said rather than redirecting to the "correct" path.
   - The teacher's skill is in responding to WHAT STUDENTS ACTUALLY SAY, not in asking the next scripted question regardless.

5. **Build in wait time (Walsh & Sattes, 2005):**
   - After each question, wait 3–5 seconds minimum.
   - After a student responds, wait 3 seconds before responding — this often prompts them to elaborate or self-correct.
   - Silence is not awkward — it's thinking time.

6. **Use genuine follow-up, not evaluation (Chin, 2007):**
   - After a student answers, do NOT say "Good" or "Not quite." Instead, respond with another question that takes their answer seriously: "Interesting — so if that's true, then what about...?"
   - Evaluative responses shut down thinking. Curiosity-driven follow-ups extend it.

Return your output in this exact format:

## Socratic Questioning Sequence: [Concept]

**For:** [Student level]
**Starting point:** [What students currently think]
**Direction:** [Where the questioning sequence aims to lead — or what complexity it surfaces]

### Opening Question
[The first question — designed to surface current thinking, not challenge it yet]

### Question Sequence
For each question:
- **Q[N]:** [Question text]
- **Type:** [Paul & Elder category]
- **Purpose:** [What this question does in the sequence]
- **Anticipated responses:** [2–3 likely responses]
- **Follow-up for each response:** [Contingent follow-up questions]

### Facilitation Notes
[Wait time reminders, how to handle silence, how to manage dominant voices and quiet students]

### Socratic vs. Leading
[Explicit notes on where this sequence risks becoming leading rather than Socratic, and how to stay on the Socratic side]

**Self-check before returning output:** Verify that (a) the sequence uses multiple Paul & Elder question types, (b) questions progress from concrete to abstract, (c) no question is leading (funnelling toward one answer), (d) anticipated responses include genuinely different perspectives, (e) follow-ups build on student answers rather than redirecting, and (f) wait time is built into the facilitation notes.
```

## 示例输出

**场景：** *概念：“是否应以现代道德标准评判历史人物” / 学生水平：“10 年级历史，学习过跨大西洋奴隶贸易，对此深感义愤——他们将历史上的奴隶贩子直接判定为纯粹的恶魔” / 认知起点：“学生认为参与奴隶贸易的历史人物只是选择了作恶的坏人”*

---

## 苏格拉底式提问序列：以现代标准评判历史人物

**适用对象：** 10 年级历史
**认知起点：** 学生将历史上的奴隶贩子视为单纯选择作恶的坏人，脱离历史背景直接套用现代道德框架。
**引导方向：** 迈向更复杂的理解：道德标准会随时间演变，个体在某种程度上是其社会环境的产物，**而且**这并不构成对其行为的开脱或辩护——能够同时容纳这两种认知，而不滑向道德相对主义或今人中心主义（presentism）。

### 开场问题

**Q1：** “你们已经学过跨大西洋奴隶贸易。如果能和当时参与其中的一位商人对话，你会想对他说什么？”

- **类型：** 澄清类（呈现当前立场）
- **目的：** 这是一个易于切入、能调动情感的开场问题，旨在在不先入为主质疑学生的前提下，呈现他们当前的道德判断。它肯定了学生的道德反应，同时为后续序列提供素材。
- **预期回答：**
  - (a) “我会告诉他们他们是怪物 / 恶魔 / 坏透了的人。” → 跟进：“当你说‘恶魔’时——你的意思是他们明知自己在做错事却故意为之？还是别的意思？”
  - (b) “我会问他们怎么能对其他人做出这种事。” → 跟进：“这是一个非常深刻的问题。你觉得他们实际上会怎么回答你？认真想想——他们当时真会怎么说？”
  - (c) “我会告诉他们他们的行为毁了数百万人的生活。” → 跟进：“你觉得他们能听懂这个论点吗？‘毁了生活’这个概念在他们那个时代和在今天对你的意义会是一样的吗？”

### 提问序列

**Q2：** “如果你要求 1750 年的一名奴隶贩子为自己的生意辩护，你觉得他**实际上**会给出什么理由？”

- **类型：** 观点与视角类
- **目的：** 促使学生走入一个令他们厌恶的历史心态内部。这个问题**不是**让他们认同那种辩护——而是要求他们理解当时那种辩护究竟是什么。这是历史共情（historical empathy，而非同情 sympathy）的基础。
- **预期回答：**
  - (a) “他们会说这很正常 / 大家都在这么做。” → 跟进：“‘大家都在这么做’是一个站得住脚的道德理由吗？你能想到现在大家都觉得很正常、但 200 年后的人可能会严厉谴责我们的事情吗？”
  - (b) “他们会说因为种族主义观念，他们有权力这么做。” → 跟进：“那些观念是从哪里来的？是他们主动选择成为种族主义者，还是他们成长的社会告诉他们某些种族低人一等？这有区别吗？”
  - (c) “他们大概会说他们需要钱 / 这是他们的生计。” → 跟进：“经济原因能改变我们对他们的道德评判吗？如果今天有人为了赚钱而伤害他人，我们会因此原谅他吗？”

**Q3：** “你能想到今天有哪些完全正常且合法的事情，在 200 年后可能会遭到后人的严厉评判吗？”

- **类型：** 推论与后果类
- **目的：** 核心转折问题。这促使学生将自己的道德框架反身应用到自己身上——如果我们用现代标准评判古人，未来的人也会用同样的方式评判我们。这个问题并不主张道德相对主义，而是揭示跨时代评判的复杂性。
- **预期回答：**
  - (a) “工厂化养殖 / 吃肉。” → 跟进：“很有意思。如果未来的人像你们评判奴隶贩子那样严厉地评判我们，你觉得这公平吗？为什么公平，或者为什么不公平？”
  - (b) “气候变化 / 快时尚 / 血汗工厂。” → 跟进：“你买衣服。你用能源。这说明你是个坏人吗？还是说你在某种程度上是你所生活社会的产物？你和 1750 年的人之间有什么区别？”
  - (c) “我想不出有什么事能像奴隶制那么糟糕。” → 跟进：“也许没有。但有没有可能我们现在正在做某些我们自己根本看不出是错的事——就像 1750 年的许多人看不出奴隶制是错的一样？这对我们评判古人意味着什么？”

**Q4：** “这里有一个更难的问题：在 18 世纪，**确实**有一些人主张奴隶制是错误的——比如贵格会教徒、一些启蒙思想家，以及反抗的被奴役者自己。既然在当时就有可能看出这是错的，那是不是说明奴隶贩子**罪加一等**——因为他们本可以知道得更清楚？”

- **类型：** 探究理由与证据类
- **目的：** 使正在浮现的相对主义复杂化。学生此时可能开始倾向于“好吧，那只是他们那个时代的问题”——这个问题则反向施压：在**那个时代内部**就存在道德批评者。废奴主义者的存在证明了历史背景并不能构成完全的免责借口。
- **预期回答：**
  - (a) “是的——既然有人知道这是错的，那些贩子就是故意装作看不见。” → 跟进：“但成为一名废奴主义者容易吗？在当时的社会和经济环境下反对奴隶制要付出什么代价？‘做正确的事很困难’能成为不这么做的借口吗？”
  - (b) “也许吧，但废奴主义者太罕见了——大多数人都接受奴隶制。” → 跟进：“站在大多数人一边会降低你的道德责任吗？‘大多数人都觉得没问题’在任何时候都能成为辩护理由吗？”
  - (c) “这很复杂——你不能简单地说他们全是恶魔，也不能说他们全都是时代的产物。” → 跟进：“我觉得你触及了核心张力。你能不能同时坚持这两种想法：他们既受制于时代背景，同时他们的行为又造成了巨大的伤害？这有可能同时成立吗？”

**Q5：** “那么，我们一路讨论到这里。有没有可能去理解历史人物为什么会那样做——把他们看作时代的产物——但同时**不**去原谅他们的所作所为？还是说，‘理解’总是会导致‘原谅’？”

- **类型：** 关于问题本身的问题（元认知类）
- **目的：** 这是核心的历史思维技能——同时保持理解与评判的能力。该问题旨在凸显这一张力，而非强行消解它。这个问题没有单一标准答案，其价值在于学生能否细腻地阐述自己的立场。
- **预期回答：**
  - (a) “你可以理解而不去原谅——就像理解罪犯为什么犯罪并不意味着你觉得他犯罪是对的。” → 跟进：“这是一个非常精准的类比。所以历史学家的任务是理解，而我们作为道德主体的责任是评判。这两件事能同时进行吗？”
  - (b) “我觉得如果你理解得太深，确实会开始原谅。” → 跟进：“这确实是一个很现实的担忧。那么界限在哪里？你怎样才能在深入研究一段历史的同时不丧失自己的道德罗盘？”
  - (c) 某位真正改变了立场的学生。 → 跟进：“你的看法从讨论开始到现在发生改变了吗？是哪一个问题或观点改变了你？这一点很值得留意。”

### 引导说明

- **候答时间不容妥协。** 尤其是在 Q3（“未来的人会因什么评判我们？”）之后，学生需要 5–10 秒的思考时间。沉默会让人觉得有些尴尬，但请坚持住。最好的回答往往出现在最长的沉默之后。
- **不要评价回答。** 不要说“好观点！”或“不太对”。相反，带着好奇心去回应：“再多说说你的想法”“是什么让你这么认为的？”“有人有不同看法吗？”评价会终结对话，好奇心才会延续对话。
- **管理主导发言者：** 如果某位学生一直主导讨论，请重新定向：“谢谢 Ella——我想听听还没发过言的同学。Kwame，你对 Ella 刚才说的话有什么反应？”在 Q3 进入全班讨论前，先用“思考-配对-分享”给较内向的学生留出加工时间。
- **应对情绪化回应：** 这一主题会引发强烈情绪。如果某位学生说出了令他人感到冒犯的话（例如过分替奴隶贩子辩护），不要直接压制——而是追问：“这是一个极具争议的立场。你会用什么证据来支撑它？不同意你的人又会怎么反驳你？”让全班的推理去回应，而不是动用你的教师权威。
- **如果班级很快得出“这很复杂”的结论：** 继续深挖。“**哪一种**复杂？你能具体说出这种张力是什么吗？”缺乏具体性的复杂只是讨论的终点。

### 苏格拉底式提问 vs 诱导性提问

**本序列容易滑向诱导性提问的风险点：**
- 如果 Q4 问成：“但当时已经有人**知道**这是错的，**难道这不就说明**贩子们是有罪的吗？”，这就成了一个带有预设偏好的反问句。相反，应中性地陈述历史事实，然后提出开放问题：“废奴主义者的存在，对于我们应当如何评判奴隶贩子有什么启示？”让学生自己得出结论。
- 如果教师通过语气或肢体语言暗示 Q5 的“正确答案”，就成了诱导性提问。教师必须真正将其作为一个开放问题来对待。有些学生会得出“理解确实会导致原谅”的结论。这是一个值得探讨的合理立场，而非需要纠正的错误。

**如何保持苏格拉底式立场：**
- 追随学生的推理，而不是死守你的教案。如果学生把讨论带向了意想不到但富有成效的方向，顺着走下去。
- 问那些你**真正好奇**学生会如何回答的问题，而不是你一直在等某个特定字眼的问题。
- 如果你发现自己心里在想“拜托，快说出我想让你说的那句话吧”，你就已经偏离了苏格拉底式提问，进入了“猜猜老师心里想什么”的游戏。此时请暂停，换成一个真正开放的问题。

---

## 已知局限性

1. **苏格拉底式提问需要充满智识安全感的课堂文化。** 在一个惩罚错误回答、同伴互相嘲笑或教师流露不满的教室里，学生绝不会分享真实的、试探性的或有争议的想法。建设这种文化是前置工作，本技能无法代劳——它假定这种文化已经存在。

2. **序列是预先准备的脚本，但真实的苏格拉底式对话是即兴的。** 分支跟进问题覆盖了常见回应，但学生总会说出意料之外的话。教师必须具备实时即兴追问的能力。本技能提供的是框架与起点，而非覆盖每条可能对话路径的完整剧本。

3. **苏格拉底式提问并非适用于所有学习目标。** 如果学生需要掌握具体的事实性内容（日期、公式、操作步骤），苏格拉底式提问是一种低效的方法。它最有价值的场景是发展概念理解、伦理推理与批判性思维——即推理过程与结论同等重要的任务。事实与程序请用显性教学；有争议的概念与复杂判断请用苏格拉底式提问。
