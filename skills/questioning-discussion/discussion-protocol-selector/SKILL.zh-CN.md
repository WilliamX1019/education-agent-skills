---
# AGENT SKILLS STANDARD FIELDS (v2)
name: discussion-protocol-selector
description: "根据讨论目的、主题与群体准备度，选择并配置结构化讨论规范（discussion protocol）。适用于规划课堂讨论、苏格拉底式研讨或结构化辩论的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "questioning-discussion/discussion-protocol-selector"
skill_name: "讨论规范选择器与引导指南"
domain: "questioning-discussion"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Resnick et al. (2015) — Accountable Talk: instructional dialogue that builds the mind"
  - "Michaels et al. (2008) — Deliberative discourse idealized and realized: accountable talk in the classroom"
  - "Howe & Abedin (2013) — Classroom dialogue: a systematic review across four decades of research"
  - "Mercer & Dawes (2014) — The study of talk between teachers and students, from the 1970s to the 2010s"
  - "Alexander (2008) — Towards Dialogic Teaching: rethinking classroom talk (4th edition)"
input_schema:
  required:
    - field: "discussion_purpose"
      type: "string"
      description: "讨论应达成的目标——探索、辩论、凝聚共识或分析"
    - field: "topic_or_question"
      type: "string"
      description: "讨论的具体主题或核心驱动问题"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及参与结构化讨论的经验"
  optional:
    - field: "class_size"
      type: "integer"
      description: "学生人数——影响规范的适用性"
    - field: "time_available"
      type: "string"
      description: "可用于讨论的分钟数"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：口头表达自信水平、话语主导模式、EAL 需求"
    - field: "subject_area"
      type: "string"
      description: "学科背景"
output_schema:
  type: "object"
  fields:
    - field: "recommended_protocol"
      type: "string"
      description: "所选讨论规范及选择依据"
    - field: "facilitation_guide"
      type: "object"
      description: "分步指南，包括场地布置、教师策略、时间安排与复盘"
    - field: "sentence_stems"
      type: "array"
      description: "供学生在讨论中使用的句式支架（talk frames）"
    - field: "common_pitfalls"
      type: "array"
      description: "该规范常见的问题及预防措施"
chains_well_with:
  - "socratic-questioning-sequence-generator"
  - "dialogic-teaching-move-generator"
  - "academic-language-sentence-frame-generator"
  - "hinge-question-designer"
teacher_time: "4 分钟"
tags: ["discussion", "dialogue", "accountable-talk", "protocols", "oracy"]
---

# 讨论规范选择器与引导指南（Discussion Protocol Selector & Facilitation Guide）

## 本技能的功能

针对给定的目的、主题与班级，选择最恰当的讨论规范（discussion protocol）——随后生成完整的引导指南，包括场地布置说明、讨论中的教师话语策略、学生句式支架（sentence stems）、时间分配以及复盘结构。涵盖的规范包括苏格拉底式研讨（Socratic seminar）、哈克尼斯圆桌讨论（Harkness discussion）、鱼缸式讨论（fishbowl）、思考-配对-分享（think-pair-share）、哲学座椅（Philosophical Chairs）以及结构化学术争议（Structured Academic Controversy）。AI 在此具有独特价值，因为选择恰当的规范需要将讨论形式与讨论目的精准匹配（例如用辩论规范来达成共识会适得其反），且有效的引导需要提前规划教师策略——明确何时介入、何时保持沉默以及如何在不主导课堂的前提下重新定向。

## 循证依据

Resnick 等（2015）确立了“负责任的对话”（accountable talk）框架作为高效课堂讨论的标准：即对学习共同体负责（尊重他人、在他人观点上建构）、对推理标准负责（基于证据、逻辑连贯）以及对知识负责（准确、有据可依）。Michaels 等（2008）将负责任的对话操作化为具体的教师话语策略——重述转译（revoicing）、追问理由（pressing for reasoning）、提出挑战（challenging）与邀请参与（inviting）——从而在教师不主导的前提下维持对话质量。Howe 与 Abedin（2013）对 225 项课堂对话研究进行了系统综述，发现高效的讨论需要：清晰的结构（而非“大家随便聊聊”）、明确的话语规范以及具有多种合理解读的真实问题。Alexander（2008）区分了五种谈话类型（机械背诵 rote、背诵抽查 recitation、讲授指令 instruction、讨论 discussion、对话 dialogue），并论证了真正的“对话”——参与者相互接续想法以迈向共同理解——是最稀缺也最有价值的。Mercer 与 Dawes（2014）指出，如果缺乏对讨论技能的显性教学（基本规则、话语策略、句式支架），课堂讨论往往会退化为争辩式话语（无理据的断言与反驳）或累积式话语（缺乏质疑的盲目附和）。

## 输入规范

教师必须提供：
- **讨论目的：** 讨论应达成什么目标。*例如：“探索争议性议题的多元视角” / “对文本形成共同解读” / “针对某项命题进行正反论证” / “就问题的最佳解决方案达成共识”*
- **主题或问题：** 核心驱动问题。*例如：“向广岛投掷原子弹是否正当？” / “《蝇王》的结局对人性有何启示？” / “是否应允许对人类胚胎进行基因编辑？”*
- **学生水平：** 年级与讨论经验。*例如：“10 年级，经常进行‘思考-配对-分享’，但尚未开展过较长时间的结构化讨论”*

可选（如情境引擎可用，将自动注入）：
- **班级规模：** 学生人数
- **可用时间：** 讨论时长（分钟）
- **学生档案：** 口头表达自信度、话语主导模式、EAL 需求
- **学科领域：** 学科背景

## Prompt

```
You are an expert in dialogic pedagogy and classroom discussion, with deep knowledge of Resnick et al.'s (2015) accountable talk framework, Michaels et al.'s (2008) teacher talk moves, Alexander's (2008) typology of classroom talk, and the practical implementation of structured discussion protocols. You understand that productive discussion requires structure, not just freedom — and that the choice of protocol must match the discussion's purpose.

Your task is to select and design a discussion protocol for:

**Discussion purpose:** {{discussion_purpose}}
**Topic/question:** {{topic_or_question}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Class size:** {{class_size}} — if not provided, design for a class of 25–30 students. Note any protocol adjustments needed for significantly larger or smaller groups.
**Time available:** {{time_available}} — if not provided, design for 20–25 minutes of discussion time (plus 5 minutes setup and 5 minutes debrief).
**Student profiles:** {{student_profiles}} — if not provided, assume a typical class with a mix of confident speakers and reluctant contributors, and design structures that ensure all students participate.
**Subject area:** {{subject_area}} — if not provided, infer from the topic and adapt reasoning expectations to the discipline.

Apply these evidence-based principles:

1. **Match protocol to purpose:**
   - **Exploring multiple perspectives:** Philosophical Chairs, fishbowl, Socratic seminar
   - **Building shared interpretation:** Harkness discussion, Socratic seminar
   - **Arguing for/against a proposition:** Structured Academic Controversy, debate with roles
   - **Reaching consensus:** Structured Academic Controversy, think-pair-share-square
   - **Deepening textual analysis:** Socratic seminar, Harkness discussion
   The wrong protocol for the purpose undermines the discussion. A debate format for consensus-building creates winners and losers instead of shared understanding.

2. **Ensure universal participation (Mercer & Dawes, 2014):**
   - In any discussion with 10+ students, at least half will not speak unless the structure requires it.
   - Build in mechanisms: think time before speaking, pair discussion before whole-group, turn-and-talk, roles that require contribution, sentence stems.
   - Monitor airtime: no individual should dominate more than 15% of the discussion.

3. **Teach the talk moves (Michaels et al., 2008):**
   - Students need explicit sentence stems for productive discussion:
     - Agreeing and extending: "I agree with ___ because..., and I'd add that..."
     - Respectfully disagreeing: "I see it differently because..."
     - Asking for clarification: "Can you explain what you mean by...?"
     - Building on: "To build on what ___ said..."
     - Providing evidence: "The evidence for that is..."
   - Display these throughout the discussion. For novice discussers, require their use.

4. **Teacher role during discussion (Resnick et al., 2015):**
   - The teacher is a FACILITATOR, not a participant. Resist the urge to evaluate, correct, or teach during the discussion.
   - Use four key moves: revoice ("So you're saying that..."), press for reasoning ("Why do you think that?"), invite responses ("Does anyone see it differently?"), challenge ("What would someone who disagrees say?").
   - The teacher should speak no more than 20% of the total talk time.

5. **Debrief the process, not just the content (Alexander, 2008):**
   - After the discussion, debrief how students discussed, not just what they discussed.
   - "Who changed their mind during the discussion? What argument or evidence caused the change?"
   - "Did we hear from everyone? How could we improve our discussion next time?"

Return your output in this exact format:

## Discussion Protocol: [Protocol Name]

**For:** [Student level]
**Purpose:** [Discussion purpose]
**Topic:** [The driving question]
**Time:** [Total time including setup and debrief]

### Why This Protocol
[3–4 sentences explaining why this protocol was selected over alternatives for this purpose]

### Setup (X minutes)
[Physical arrangement, materials needed, ground rules to establish]

### Protocol Steps
[Step-by-step guide with timing for each phase]

### Teacher Moves During Discussion
[Specific facilitation moves with examples — when to intervene, when to stay silent, how to redirect]

### Sentence Stems for Students
[A set of discussion stems to display or distribute]

### Debrief (X minutes)
[How to close the discussion and reflect on both content and process]

### Common Pitfalls
[3–4 things that typically go wrong with this protocol and how to prevent them]

**Self-check before returning output:** Verify that (a) the protocol matches the stated discussion purpose, (b) structures for universal participation are built in, (c) sentence stems are provided, (d) the teacher role is facilitative not evaluative, (e) a debrief is included, and (f) common pitfalls are addressed.
```

## 示例输出

**场景：** *讨论目的：“在一个道德复杂的问题上探索多元视角——没有单一的正确答案” / 主题：“违法在任何情况下都可能是正当的吗？” / 学生水平：“9 年级，经常做‘思考-配对-分享’，但尚未开展过采用结构化规范的持续全班讨论” / 可用时间：“共 30 分钟”*

---

## 讨论规范：哲学座椅（Philosophical Chairs）

**适用对象：** 9 年级，首次采用结构化讨论规范
**目的：** 在道德复杂的问题上探索多元视角
**主题：** “违法在任何情况下都可能是正当的吗？”
**时间：** 30 分钟（5 分钟布置 + 20 分钟讨论 + 5 分钟复盘）

### 为何选择此规范

选择“哲学座椅”是因为本讨论旨在探索一个没有单一正确答案的道德复杂问题中的多元视角，同时学生属于结构化讨论的新手。哲学座椅提供了物理空间上的结构（学生通过实际移动来表明立场），使抽象思维变得具体可见。它降低了口头表达的准入门槛：学生在组织语言陈述理由之前，可以先通过站位来参与，这比直接开口发言心理压力小得多。相较于苏格拉底式研讨（需要更成熟的持续对话经验）和结构化辩论（强制分配立场而非允许真实探索），该规范更为合适。哲学座椅能够自然地呈现出教师所期待的复杂性，因为学生在听到不同论据时可以随时调整站位——“改变想法”本身就是该规范的内置机制。

### 场地布置（5 分钟）

**空间安排：** 在教室中清出一片空地。张贴三块标识：
- 左侧墙面：“赞同——有时违法是正当的”
- 右侧墙面：“反对——违法在任何情况下都不正当”
- 中间区域：“未定 / 视情况而定”

**材料：** 在黑板上展示句式支架（见下文）。给每位学生发一张小卡片记录自己的理由。

**基本规则（大声宣读并展示）：**
1. 倾听是为了理解，而不是为了赢。
2. 针对论点，不对人。“我不同意这个观点，因为……”而不是“你错了。”
3. 改变想法是完全可以的——实际上非常值得赞赏。移动站位代表你在深入思考，而非软弱。
4. 每人至少发言一次。我会协助大家做到这一点。
5. 使用黑板上的句式支架。

**初始站位：**
“阅读黑板上的问题：‘违法在任何情况下都可能是正当的吗？’先静默思考 30 秒——不要说话。然后移动到反映你当前想法的位置。你可以站在两端、两端连线上的任意位置，或者如果你真的拿不定主意，可以站在中间。”

*留出 60 秒让学生移动，观察分布情况。*

### 规范步骤

**第一阶段：初始立场陈述（5 分钟）**
“你们已经选好了位置。现在我想听听你们**为什么**站在那里。我将从每个区域各请一位同学来解释他们的想法。”

- 从“赞同”、“反对”、“未定”区域各点一名学生发言。
- 每位发言后追问：“有人想补充这个立场吗？或者认同这个结论但有不同的理由？”
- 每次初始陈述控制在 90 秒以内。

**第二阶段：跨立场对话（10 分钟）**
“现在我们要在不同立场之间展开对话。规则是：你只能针对**不同立场**的同学刚才说的内容做出回应。请使用句式支架。”

- 教师通过跨阵营邀请回应来引导对话：“Sarah 刚才说了 X。‘反对’阵营里有人想针对这一具体观点做出回应吗？”
- 每经过 2–3 轮有分量的交流后暂停一下：“有人听到什么让自己想换位置的话了吗？如果有，现在就移动。不需要解释——直接移动即可。”留出 10 秒移动时间。
- 如果有人移动，询问移动者：“是哪一个论点让你改变了站位？”
- 如果 3 轮后无人移动，引入一个具体案例：“来看看这个案例：罗莎·帕克斯（Rosa Parks）拒绝让出公交车座位而触犯了法律。她当时的违法行为正当吗？”观察学生移动并展开讨论。
- 如有需要，引入第二个案例：“如果有人为了把濒危病人送往医院而超速违法呢？”

**第三阶段：最终立场总结（5 分钟）**
“讨论还剩最后 5 分钟。我想听听在讨论过程中**移动过位置**的同学怎么说。是什么改变了你的想法？”

- 请 2–3 名移动过的学生发言。追问：“具体是哪一个论据或例子促使你的想法发生转变的？”
- 随后提问：“经过这场讨论，这个问题对你来说是变简单了，还是变复杂了？”收集 3–4 个回答。
- “请移动到你的最终立场。时间 20 秒。”

### 讨论中的教师策略

| 时刻 | 教师策略 | 话术示例 |
|--------|-------------|--------|
| 学生只下结论不给理由 | **追问理由** | “你说有时是正当的。你能举一个具体例子，并解释为什么在那种情况下是正当的吗？” |
| 一方提出有力论点后 | **邀请质疑** | “这个论证很清晰。另一方有人想挑战它吗？最有力的反方论点会是什么？” |
| 讨论开始重复兜圈子 | **引入新情境** | “我抛出一个具体案例：[案例情境]。**现在**你们怎么看？” |
| 某位学生主导发言 | **重新定向** | “谢谢 Marcus。我想听听还没发过言的同学。Fatima，你一直在认真倾听——你有什么看法？” |
| 学生表达不清、他人没听懂 | **重述转译** | “让我确认一下我理解得对不对。你的意思是……[转述]？是这样吗？” |
| 学生各说各话、未能交锋 | **建立关联** | “Aisha，我觉得你的观点和 James 刚才说的有联系。James，你看出其中的联系了吗？” |
| 讨论进展顺利 | **保持沉默** | 什么都不说。最好的讨论是学生对学生的对话。仅在对话停滞、偏离主题或排斥部分声音时介入。 |

**关键原则：** 切勿透露你自己在这一问题上的个人立场。一旦你表态，学生就会停止独立思考，转而试图迎合你的观点。

### 学生句式支架

*全程展示在黑板上：*

**陈述立场：**
- “我认为……因为……”
- “我的立场是……我的证据是……”

**回应他人：**
- “我同意 ___ 的看法，因为……，而且我想补充……”
- “我与 ___ 的看法不同，因为……”
- “我部分同意——我认为 ___ 在……这一点上说得对，但在……这一点上我不同意”

**请求澄清：**
- “你能解释一下你说的……是什么意思吗？”
- “你能举一个关于……的具体例子吗？”

**引入复杂性：**
- “这取决于……因为在有些情况下……但在另一些情况下……”
- “反方论点可能会是……”
- “如果是……这种情况呢？”

**改变立场：**
- “我改变了想法，因为……”
- “我以前认为……，但现在我认为……因为……”

### 复盘（5 分钟）

**内容复盘（2 分钟）：**
“先不管你自己的立场是什么——你今天听到的最有力的论点是哪一个（无论正反哪一方）？不一定是你赞同的那个，而是论证最有力的那个。”
随机点名 3 名学生回答。

**过程复盘（3 分钟）：**
“现在我们来聊聊我们是**怎么**讨论的，而不仅仅是讨论了**什么**。”
- “谁觉得开口很难？是什么让开口变难的？下次怎样做能帮到你？”
- “谁改变了想法？改变想法是软弱的表现，还是思维有力量的表现？”
- “以 1–5 分打分，我们今天倾听彼此做得怎么样？下次讨论我们可以在哪一点上做得更好？”

*在黑板上记下一项改进目标，留待下次讨论使用。*

### 常见误区

1. **学生扎堆在“赞同”或“反对”一侧，中间区域空无一人。** 这通常意味着问题不够真正复杂，或学生感受到要选边站队的社交压力。解决办法：让中间立场正常化。开始时就说：“今天教室里最勇敢的位置可能是中间——它意味着你能同时容纳两种相互冲突的想法。”如果所有人挤向同一侧，就用一个反例充当“魔鬼代言人”。

2. **讨论变成一连串的独白，而非对话。** 学生各自陈述立场，却不回应别人说过的话。解决办法：严格执行跨立场规则——你只能为了回应不同立场的同学而发言。要求使用“我同意/不同意 [姓名]，因为……”句式来建立直接交锋。

3. **强势声音占据主导。** 在任何缺乏结构的讨论中，3–4 名自信的学生会占去 80% 的发言时间。解决办法：每 3 次发言后暂停，说“我想听听还没发过言的同学”。在第二阶段开始前加入“思考-配对-分享”，让较内向的学生在全班讨论前有准备时间。

4. **教师说得太多。** 最常见的引导失败是教师忍不住填补沉默、评价回答或现场微型讲授。为自己设定目标：在 20 分钟讨论中发言不超过 5 次（程序性指令除外）。数着自己的介入次数。一旦达到 5 次，剩下的时间保持沉默。

---

## 已知局限性

1. **哲学座椅最适合二元对立或光谱型问题。** 拥有超过两个明确立场的问题（例如包含四个选项的“一战最重要的起因是什么？”）需要其他规范——可考虑结构化学术争议或四角站位法变体。

2. **身体移动对部分学生而言存在社交风险。** 公开改变站位意味着公开承认自己之前“错了”。对于社交焦虑的学生或存在欺凌隐患的班级，这可能会带来心理威胁。可通过反复将移动正常化来缓解：“在这个活动里，移动位置是最聪明的表现。”如果这仍然构成障碍，可用书面立场调整（学生私下更新卡片）替代身体移动。

3. **该规范培养口语表达与推理能力，但不能保证内容准确性。** 学生可能会说出极具说服力但事实上错误的论点。复盘阶段才是纠正事实错误的时候——切勿在讨论进行中打断纠正，否则会瞬间终结对话。复盘结束后，教师应澄清任何事实性偏差：“讨论中有人提到了 X。历史证据实际上表明的是 Y。但你们刚才运用的推理过程完全正确。”
