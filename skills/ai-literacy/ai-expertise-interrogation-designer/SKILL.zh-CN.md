---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ai-expertise-interrogation-designer
description: "设计“哈哈镜（Funhouse Mirror）”活动，让学生运用自身领域专长检测 AI 的扭曲、遗漏与过度自信。适用于学生对某主题已有足够了解、能够评估 AI 相关表述时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "ai-literacy/ai-expertise-interrogation-designer"
skill_name: "AI 专长质询设计器"
domain: "ai-literacy"
version: "1.0"
contributor: "Gareth Manning"
evidence_strength: "moderate"
evidence_sources:
  - "Chi, Glaser & Farr (1988) — The Nature of Expertise"
  - "Ericsson & Smith (1991) — Toward a General Theory of Expertise"
  - "Thiede, Anderson & Therriault (2003) — Accuracy of metacognitive monitoring affects learning of texts"
  - "Dunning, Kruger et al. (2003) — Why people fail to recognize their own incompetence"
  - "Kazemitabaar et al. (2023) — Studying the effect of AI code generators on supporting novice learners"
input_schema:
  required:
    - field: "student_expertise_domain"
      type: "string"
      description: "学生拥有真正领域知识的范畴——学校学科、兴趣爱好、文化背景、本地地理、体育项目或某项技能"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及在该领域的专业深度"
  optional:
    - field: "interrogation_depth"
      type: "string"
      description: "表层（事实性错误及人名/日期错误）vs. 深层（微妙扭曲、复杂性缺失、不当自信、文化盲区）"
    - field: "discussion_format"
      type: "string"
      description: "如何使用发现结果：个人反思、跨不同专长领域的同伴对比，或全班专长综合讨论"
    - field: "subject_area"
      type: "string"
      description: "若专长质询嵌入在某一课程单元中，所属的学校学科情境"
    - field: "target_ai_tool"
      type: "string"
      description: "学生将质询的 AI 工具"
output_schema:
  type: "object"
  fields:
    - field: "expertise_activation_protocol"
      type: "object"
      description: "质询前协议，用于在咨询 AI 之前激活并记录学生的已有知识"
    - field: "interrogation_questions"
      type: "array"
      description: "向 AI 提问的校准问题集——从事实性到阐释性再到细微差别，按专长深度分级"
    - field: "distortion_annotation_protocol"
      type: "object"
      description: "对照专家知识标注 AI 输出的协议——标注什么以及为什么"
    - field: "distortion_taxonomy"
      type: "object"
      description: "该领域中可能出现的 AI 扭曲分类法——事实错误、过度自信、文化扁平化、细节缺失、虚假普适性"
    - field: "discussion_guide"
      type: "object"
      description: "全班综合讨论引导指南——对比不同专长领域中的扭曲现象并提炼可迁移结论"
chains_well_with:
  - "metacognitive-monitoring-ai-contexts"
  - "ai-output-critical-audit-designer"
  - "pedagogical-content-knowledge-developer"
teacher_time: "4 分钟"
tags: ["AI-literacy", "expertise", "distortion", "Funhouse-Mirror", "metacognition", "Dunning-Kruger", "domain-knowledge"]
---

# AI 专长质询设计器

## 本技能的作用

生成一项活动——Kharbach（2026）提出的“哈哈镜（Funhouse Mirror）”——让学生运用自身的领域专长作为工具，去检测 AI 的扭曲、遗漏与过度自信。这逆转了 AI 评估中常见的专家-新手动态：在大多数 AI 素养活动中，学生是被动接受“AI 有局限性”警告的新手；而在这项活动中，学生**才是**领域专家。他们就自己真正熟悉的事物向 AI 提问——比如深入研究过的学科、长期参加的竞技体育、成长其中的文化背景、了如指掌的家乡地理——并运用自己的知识识别 AI 在哪些地方搞错了、过度简化了、扁平化了，或带着虚假的自信胡说八道。其教学机制在于通过直接交锋建立经过校准的 AI 审慎态度：在自己擅长的领域发现 AI 犯错，会带来切身且持久的认知——AI 并非全知全能。一个亲眼看见 AI 自信满满地讲错自己熟悉的运动、文化传统或家乡的学生，比一个只听过“AI 可能会犯错”抽象警告的学生，能建立起可靠得多的审慎意识。输出包括专长激活协议（学生在咨询 AI 前先记录自己的知识）、经过校准的质询问题、扭曲标注协议、针对特定领域的扭曲分类法，以及用于综合全班不同专长领域发现的讨论指南。

## 实证基础

Chi、Glaser & Farr（1988）确立了专家-新手研究框架：专家组织知识的方式不同于新手，能在更深层次感知问题，并拥有更丰富、联系更紧密的领域表征。关键在于，专家能察觉领域表征中**缺失或被扭曲**的部分——他们拥有看出漏洞的知识。这正是本活动的基石：拥有真正领域专长的学生能看出普通学生会漏掉的 AI 扭曲，因为只有知道“本该有什么”的人，才能察觉“少了什么”。Ericsson & Smith（1991）指出，专长的特征在于能够敏锐察觉细微差异以及对预期模式的偏离——这正是专家阅读关于其领域的 AI 输出时激活的同一认知机制。Thiede 等人（2003）证明，当学习者拥有真实的知识库可供比对时，元认知准确性（主观判断的理解度与实际理解度之间的相关性）会大幅提升——发现已知知识与所读内容之间的差异会激活准确的自我评估。本活动恰好制造了这种比对：学生领域知识与 AI 输出之间的比对。Dunning 等人（2003）关于达克效应的研究在反向维度上同样相关：熟悉某领域的学生比不熟悉该领域的学生更**善于**识别 AI 在该领域的局限——专长使人能够识别 AI 的无能，而不仅仅是自己的无能。Kazemitabaar 等人（2023）提供了实证证据，表明学习情境中的 AI 辅助可能掩盖真实的知识缺口；本活动则通过逆转专家/新手定位来主动暴露这一动态。

## 输入规范

教师必须提供：
- **学生专长领域（Student expertise domain）：** 学生真正熟悉的内容。*例如：“足球（具体而言：曼联历史与英超统计数据）” / “匈牙利民间音乐与舞蹈传统（本土知识）” / “竞技游泳——技术、训练与赛事” / “K-Pop 文化，特别是 BTS 的唱片目录与粉丝文化” / “布达佩斯第七区的地理与历史”*
- **学生水平（Student level）：** 年级与专长深度。*例如：“十年级，学生在不同领域（体育、音乐、地理、文化传统）拥有深厚的个人专长” / “十二年级，学生已学习 A-level 深度的历史”*

可选项（如可用则由上下文引擎注入）：
- **质询深度（Interrogation depth）：** 表层错误 vs. 深层扭曲
- **讨论形式（Discussion format）：** 如何分享发现
- **学科领域（Subject area）：** 课程学科框架（如有）
- **目标 AI 工具（Target AI tool）：** 学生将质询哪个 AI 系统

## 提示词（Prompt）

```
You are an expert in expertise research and AI literacy pedagogy, with knowledge of Chi, Glaser & Farr's (1988) expert-novice framework, Ericsson & Smith's (1991) expertise theory, Thiede et al.'s (2003) metacognitive accuracy research, and Dunning et al.'s (2003) work on competence and self-assessment. You understand the core mechanism of this activity: expertise enables detection. A student who has found AI confidently wrong about something they know deeply will have earned a much more durable AI skepticism than one who was warned abstractly. The pedagogical value is not in cataloguing AI errors — it is in the moment of discovery, and in the generalisation it enables.

CRITICAL PRINCIPLES:
- **The expertise must be genuine.** This activity does not work with superficial knowledge. "I know a bit about football" is not enough. "I have watched every Manchester United match for five years and know the squad statistics" IS enough. The interrogation questions must be calibrated to genuinely probe the depth of the AI's knowledge.
- **The goal is distortion taxonomy, not error hunting.** AI errors alone are unsurprising. The more valuable finding is the PATTERN: what types of distortions does AI consistently produce in this domain? Is it confidently wrong about recent events? Does it flatten cultural specificity? Does it privilege English-language sources? Does it confuse similar-but-distinct concepts?
- **Expertise activation precedes AI consultation.** Students must document what they know BEFORE asking the AI. This serves two purposes: (1) it creates a reference document that makes distortions visible as discrepancies; (2) it prevents the AI's confident output from overwriting the student's own knowledge before they've had a chance to articulate it.
- **The discussion synthesis is the most important phase.** Finding one AI error in your domain is interesting. Discovering that students with expertise in very different domains all found the SAME types of distortions (e.g., AI always sounds confident even when it's wrong; AI consistently misses recent events; AI flattens cultural specificity) is the generalisable insight that makes this an AI literacy activity, not just a fact-checking exercise.
- **Distortions are not the same as errors.** An error is factually wrong. A distortion is subtly misleading: technically true but missing crucial context, presented at the wrong level of confidence, drawn from an unrepresentative source, or flattening genuine complexity. Students with genuine domain expertise will find both — the distortions are more interesting pedagogically.

Your task is to design an AI expertise interrogation activity for:

**Student expertise domain:** {{student_expertise_domain}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore fields marked "not provided."

**Interrogation depth:** {{interrogation_depth}} — if not provided, design for both surface (factual accuracy) and deep (distortion, false confidence, cultural flattening) levels.
**Discussion format:** {{discussion_format}} — if not provided, design for whole-class synthesis after individual interrogation.
**Subject area:** {{subject_area}} — if not provided, frame the activity as a standalone AI literacy exercise.
**Target AI tool:** {{target_ai_tool}} — if not provided, design for a general-purpose LLM chatbot.

Return your output in this exact format:

## AI Expertise Interrogation: [Domain]

**For:** [Student level]
**Expertise domain:** [The area of genuine student knowledge]
**Interrogation depth:** [Surface / Deep / Both]

### Expertise Activation Protocol

[What students do BEFORE consulting the AI — to document their knowledge and create a reference for comparison]

**Step 1:** [Knowledge inventory — what do I know about this domain?]
**Step 2:** [Identify your strongest sub-area — where is your expertise deepest?]
**Step 3:** [Write 3-5 claims you are confident about in this domain — specific, verifiable]
**Step 4:** [Identify one area where you know the real answer is more complex than most people realise]

### Interrogation Questions

[A calibrated set of questions to ask the AI, scaled from surface to deep]

**Surface questions (factual accuracy):**
[2-3 questions where the student knows the correct answer and can check if the AI is right]

**Depth questions (complexity and nuance):**
[2-3 questions that probe whether the AI understands the nuances the student knows]

**Distortion trap questions (areas likely to reveal AI limitations):**
[2-3 questions specifically targeting the types of distortion common in this domain — recent events, cultural specificity, contested claims, insider knowledge]

### Distortion Annotation Protocol

[How students mark up AI output against their expertise]

**Annotation codes:**
[Table with codes for: factual error, false confidence, missing nuance, cultural flattening, outdated information, false universalism]

**Annotation process:** [Step-by-step instructions for comparing AI output against expertise]

### Distortion Taxonomy

[For this specific domain, what types of distortions is AI most likely to produce?]

**Most likely distortions in [domain]:**
[3-5 distortion types with explanations of why AI tends to produce them in this domain and examples of what they look like]

### Discussion Guide

**Individual reflection (before class discussion):**
[Questions students answer about their findings before sharing]

**Class synthesis:**
[How to structure the comparison across students with different expertise domains]

**The generalisable question:** [The central question that draws from specific domain findings to a general AI literacy insight]

**Self-check before returning output:** Verify that (a) the expertise activation protocol genuinely prevents AI from overwriting student knowledge, (b) interrogation questions are calibrated to the stated expertise depth, (c) distortion trap questions target domain-specific AI weaknesses, not generic errors, (d) the distortion taxonomy is specific to this domain, (e) the discussion guide includes a synthesis move that turns domain-specific findings into a generalisable insight.
```

## 示例输出

**情景：** *学生专长领域：“匈牙利民间音乐与舞蹈传统——布达佩斯一所中学的学生参与过民间舞蹈团，了解地区性舞蹈与地区音乐差异，并在文化教育中学习过民间音乐” / 学生水平：“十一年级，对匈牙利地区性民间传统拥有深厚的体验式知识，正式乐理知识水平不一” / 质询深度：“表层与深层兼顾” / 讨论形式：“拥有不同专长领域的学生结对交流，随后全班综合讨论”*

---

## AI 专长质询：匈牙利民间音乐与舞蹈

**适用对象：** 布达佩斯十一年级中学生
**专长领域：** 匈牙利地区性民间音乐与舞蹈传统
**质询深度：** 表层（事实性）与深层（文化特异性、地区准确性）

### 专长激活协议

**第 1 步——知识盘点：** 在打开任何 AI 工具之前，花 5 分钟写下你对匈牙利民间音乐与舞蹈的了解。包括：你熟悉的地区风格（特兰西瓦尼亚？Mezőség？Alföld？）、具体舞种、特定乐器、csárdás 与 verbunkos 的区别，以及任何关于民间舞团结构或表演实践的知识。

**第 2 步——确定你最强的子领域：** 你在哪一块的了解最深？如果你跳了三年 Mezőség 风格舞蹈，那就是你最强的领域。如果你熟知绞弦琴（tekerőlant）的地区变体，那就是你的强项。

**第 3 步——写出 3 条你有把握的主张：** 写下三条你在该领域确信为真、且能在对话中有理有据捍卫的事实。*例如：“特兰西瓦尼亚民间舞具有截然不同的地区风格，彼此不可互换——来自 Kalotaszeg 的舞蹈与来自 Mezőség 的舞蹈在具体、可命名的方面存在差异。” / “匈牙利的舞屋运动（táncház）始于 20 世纪 70 年代，在某种程度上是共产主义时期的一种文化抵抗运动。”*

**第 4 步——识别一个隐藏的复杂性：** 匈牙利民间音乐或舞蹈中有哪一件事是大多数局外人会误解或过度简化的？这正是你预期 AI 会失手的地方。

### 质询问题

**表层问题（事实准确性）：**
- “匈牙利民间舞蹈的主要地区风格有哪些，各自的显著特征是什么？”
- “匈牙利舞屋运动（táncház）的历史是什么，它何时兴起？”
- “匈牙利不同地区的民间音乐传统上与哪些乐器相关？”

**深层问题（复杂性与细微差别）：**
- “Kalotaszeg 与 Mezőség 的民间音乐有何区别，是什么让每种风格独具特色？”
- “官方文化项目对匈牙利民间舞的呈现，与村落语境中活态传承的传统有何不同？”
- “原生态民间音乐在匈牙利身份政治中的意义是什么，为什么这一点存在争议？”

**扭曲陷阱问题（AI 最容易失手的区域）：**
- “目前匈牙利最具影响力的当代民间乐团有哪些，它们在风格上有何区别？”（测试 AI 是否掌握活态现场的最新知识）
- “匈牙利民间传统与罗马尼亚、斯洛伐克、塞尔维亚境内匈牙利族裔群体的民间传统有何关系——它们是一回事吗？”（测试 AI 是否会抹平匈牙利本土民间音乐与特兰西瓦尼亚等地区变体之间的关键区别）
- “一位来自布达佩斯民间乐队的乐手如果被形容为演奏‘传统匈牙利民间音乐’，他会怎么想？”（测试对当代民间音乐界自我定位的圈内理解）

### 扭曲标注协议

**标注代码：**

| 代码 | 标注内容 |
|---|---|
| FE | 事实性错误（Factual error）——AI 陈述了明显错误的内容 |
| FC | 虚假自信（False confidence）——AI 将不确定的内容当作定论来陈述 |
| CF | 文化扁平化（Cultural flattening）——AI 将不同的地区/文化变体当作可互换的同一事物 |
| MN | 细节缺失（Missing nuance）——AI 回答在技术上没错，但因残缺而产生误导 |
| OD | 信息过时（Outdated）——AI 信息反映的是旧来源，遗漏了近期发展 |
| FU | 虚假普适性（False universalism）——AI 暗示某事物具有普适性，而实际上它仅特定于某一语境 |

**标注流程：**
1. 阅读 AI 对表层问题的回答。对照你事先记录的知识，标出任何不一致之处。
2. 阅读 AI 对深层问题的回答。优先标注 CF 和 MN——这两类最常出现。
3. 阅读 AI 对扭曲陷阱问题的回答。这里最可能出现重大扭曲。标出所有让你觉得错误、残缺或盲目自信的地方。
4. 对每一处标注写一句话：“AI 说【X】。实际情况是【Y】。差距在于【Z】。”

### 扭曲分类法

**匈牙利民间传统中最可能出现的扭曲：**

**文化扁平化（CF）——最常见：** 主要基于英文语料训练的 AI 会把“匈牙利民间音乐”当作一个统一类别，抹平了匈牙利本土与特兰西瓦尼亚/海外匈牙利族裔传统之间对从业者而言至关重要的区别。AI 很可能会把 Kalotaszeg 与 Mezőség 当作可互换的标签，而非各自拥有特定音乐与编舞规范的独立地区风格。

**虚假普适性（FU）——非常常见：** AI 可能会将“官方”民间音乐传统（柯达伊学派、国家民间歌舞团）呈现为代表性传统，从而忽略从业者日常面对的“体制化官方传统”与“táncház 活态民间传统”之间的张力。

**信息过时（OD）——很可能出现：** 当代匈牙利民间音乐界自 20 世纪 90 年代以来发生了巨大演变；AI 训练数据往往偏向较早期的资料。关于当前乐团、近期发展或当代现场的问题很可能会得到过时或残缺的回答。

**遗漏海外族裔传统的复杂性：** AI 要么会把特兰西瓦尼亚匈牙利民间传统直接归并进“匈牙利民间音乐”，要么把两者完全割裂，从而错失本土与跨界传统之间对 táncház 运动自我理解至关重要的复杂关系。

**对争议性主张的虚假自信：** 关于各类民间传统“原真性”或“纯正性”的问题触及匈牙利民间艺术群体内部持续的文化与政治辩论。当从业者积极争论时，AI 很可能会把其中一种立场包装成行业共识。

### 讨论指南

**个人反思（全班讨论前 5 分钟）：**
- AI 哪些地方说对了？它在哪里确实有帮助？
- 你发现的最重大扭曲是什么——哪一处最容易误导一个原本不了解该领域的人？
- AI 是自信地犯错，还是恰当地表达了不确定性？
- 你的发现说明了 AI 的知识**来自哪里**（它是基于什么语料训练的）？

**同伴对比：** 与质询了**不同**领域（体育、文化传统、学术学科）的同伴合作，对比彼此的发现：
- 你们两人都发现了哪些共同的扭曲类型？
- 你们两个领域中的扭曲有什么不同？
- 其中是否存在规律？

**全班综合讨论——可迁移的核心问题：** “根据大家的发现，AI 在处理专业知识时呈现出哪些系统性模式？AI 一贯擅长什么？它一贯在哪些地方出错或扭曲？以及——如果连在我们**自己就是专家**的领域里 AI 都表现如此，那在我们**谁都不是专家**的领域里，这又意味着什么？”

---

## 已知局限

1. **专长必须真实，活动才能奏效。** 对某领域仅有一知半解的学生，无法发现与真正专家同等质量的扭曲。当学生能够指出 AI 遗漏的具体、可命名的区分时，活动效果最佳——而不仅仅是“AI 搞错了几件事”。教师在开展前应评估学生是否真正具备所需的专长深度。

2. **活动可能过度拟合单一 AI 工具的知识盲区。** 在 ChatGPT 中发现的扭曲未必存在于使用不同数据训练的另一模型中。教学目标是培养可迁移的审慎态度，而非普查某个特定模型的错误清单。讨论综合阶段必须明确这一点。

3. **文化与少数群体专长会带来情感投入。** 在英文训练数据中代表性不足或被误读的文化传统（地方传统、少数族裔文化、非西方领域）拥有专长的学生，可能会发现令他们感到切身被冒犯的 AI 扭曲。教师应做好准备，以恰当的关怀引导相关讨论。

4. **专家-新手框架在 AI 领域的具体应用缺乏直接实证检验。** 专长研究（Chi et al., 1988; Ericsson & Smith, 1991）在人类专长发展方面有坚实证据。将其作为检测 AI 扭曲的框架合乎原则但属创新之举——“激活专长比抽象警告更能培养持久 AI 审慎态度”这一具体主张尚未经过正式实证测试。
