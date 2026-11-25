---
# AGENT SKILLS STANDARD FIELDS (v2)
name: belonging-classroom-culture-designer
description: "针对特定班级动态设计有针对性的干预措施，强化归属感与包容性。适用于学生感到孤立、小团体形成或新生需要融入的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/belonging-classroom-culture-designer"
skill_name: "归属感与班级文化设计器"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Walton & Cohen (2011) — A brief social-belonging intervention improves academic and health outcomes of minority students"
  - "Yeager & Walton (2011) — Social-psychological interventions in education"
  - "Baumeister & Leary (1995) — The need to belong: desire for interpersonal attachments as a fundamental human motivation"
  - "Goodenow (1993) — Classroom belonging among early adolescent students"
  - "Murphy & Zirkel (2015) — Race and belonging in school: how anticipated and experienced belonging affect choice, persistence, and performance"
input_schema:
  required:
    - field: "classroom_context"
      type: "string"
      description: "班级描述——学科、年级以及群体动态的相关特征"
    - field: "belonging_concern"
      type: "string"
      description: "具体的归属感问题——例如学生孤立、小圈子、边缘化群体、新生、升学过渡期焦虑"
  optional:
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：班级构成、社交动态、SEN、EAL、学生补助群体"
    - field: "current_practices"
      type: "string"
      description: "教师目前已经采取的建立归属感的做法——避免建议重复"
    - field: "time_available"
      type: "string"
      description: "可分配给归属感建设实践的时间"
output_schema:
  type: "object"
  fields:
    - field: "belonging_practices"
      type: "array"
      description: "具体的、可落地的课堂归属感实践——非空泛建议，而是可执行的行动"
    - field: "routine_integration"
      type: "object"
      description: "如何将归属感实践嵌入现有常规流程，而非额外增加负担"
    - field: "language_guide"
      type: "object"
      description: "传递归属感的教师具体话术 vs 无意中威胁归属感的话术"
    - field: "monitoring_indicators"
      type: "array"
      description: "归属感正在改善的可观察迹象——需要留意什么"
chains_well_with:
  - "motivation-diagnostic-task-redesign"
  - "trauma-informed-practice-designer"
  - "ruler-emotional-literacy-sequence"
  - "restorative-practice-protocol-designer"
teacher_time: "3 分钟"
tags: ["belonging", "inclusion", "classroom-culture", "relationships", "equity", "marginalisation"]
---

# 归属感与班级文化设计器（Belonging & Classroom Culture Designer）

## 本技能的功能

生成具体、可落地的课堂实践，为所有学生建立归属感——并特别关注最容易体验到“归属不确定性”的学生（转学生、少数群体学生、特殊教育需要 SEN 学生、英语作为附加语言 EAL 学生、升学过渡期学生）。Walton 与 Cohen 研究的核心洞见在于：归属感不是一种人格特质，而是一种对环境线索高度敏感的感知。来自课堂环境的微小信号（“你在这里很重要”、“像你一样的人在这里能成功”、“遇到困难很正常，不代表你不属于这里”）能够对投入度、坚持性和学业成绩产生不成比例的深远影响。输出包括具体实践（而非“保持热情”之类的空泛建议）、语言指南（该说什么、避开什么）、嵌入现有常规的方案（明确列出准备与跟进成本）以及监测指标（如何知道是否奏效）。AI 在此具有独特价值，因为归属感研究识别出了许多教师平时不会刻意设计的细微环境线索——而且为边缘化学生建立归属感的实践往往惠及**全体**学生。

## 循证依据

Walton 与 Cohen（2011）针对大学生开展了一项简短的社会归属干预；其报告的缩小成绩差距结果不能直接等同于本套中小学课堂常规的效应量估计。向当前情境的迁移属于一种有待检验的设计推论，而非必然承诺的差距缩减。但其背后机制并不复杂：当学生担心自己“不属于这里”时，他们会把挫折解读为印证这一担心的证据（“我考得差是因为我不适合这里”）。当这种担忧得到缓解时，同样的挫折会被解读为学习的正常组成部分（“大家有时都会遇到困难”）。Baumeister 与 Leary（1995）确立了归属感是一项基本人类需求——如同食物与安全一样基础。当这一需求未被满足时，认知资源就会从学习转移到“归属感监控”上：“老师喜欢我吗？其他同学接纳我吗？这里欢迎我吗？”这种监控消耗了本应用于学习的工作记忆与注意力。Goodenow（1993）发现，课堂归属感能预测青春期早期的学习动机、努力程度与学业成绩——感到有归属感的中学生更努力、更坚持、学得更好。Yeager 与 Walton（2011）表明，社会心理干预（归属感、成长型思维、目标感）在“润物细无声”（stealthy）——即融入日常课堂实践而非作为特殊项目高调宣布时——效果最佳。Murphy 与 Zirkel（2015）进一步证明，“预期归属感”（预期自己会融入 vs 预期融不进去）在学生尚未踏入教室前就影响着他们的选择——预期没有归属感的学生更少选择挑战性课程、加入社团或主动求助。

## 输入规范

教师必须提供：
- **课堂情境：** 班级及其特征。*例如：“7 年级英语，28 名学生，小学升初中第一学期。混合能力。几名学生来自不同小学，谁也不认识。” / “10 年级 GCSE 科学，18 人小班，男生居多，三名女生在课上极少发言。”*
- **归属感关切：** 具体问题。*例如：“几名学生处于孤立状态——不与任何人互动，显得局促不安” / “两名学生刚从国外转来，英语有限” / “班里小团体现象严重，部分学生在小组作业中被排斥”*

可选（如情境引擎可用，将自动注入）：
- **学生水平：** 年级
- **学科领域：** 课程学科
- **学生档案：** 班级构成、社交动态
- **现有实践：** 教师已经在做的事
- **可用时间：** 可分配的时间

## Prompt

```
You are an expert in belonging, classroom culture, and social-psychological interventions in education, with deep knowledge of Walton & Cohen's (2011) belonging intervention research, Baumeister & Leary's (1995) belongingness theory, Goodenow's (1993) work on classroom belonging, and Yeager & Walton's (2011) principles for effective social-psychological interventions. You understand that belonging is a perception shaped by environmental cues — and that teachers can deliberately design those cues.

IMPORTANT: Embed routine practices unobtrusively (informed by Yeager & Walton, 2011) — embedded in normal classroom routines, not announced as special programmes. Do not publicly single out a learner as isolated. This does not prohibit voluntary discussion of belonging or explicit, respectful individual support. This approach often backfires because it draws attention to the very belonging threat it's trying to address. Instead, design practices that communicate belonging to everyone, with particular benefit to those who need it most.

IMPORTANT: Belonging practices must be genuine, not performative. Students — especially adolescents — can detect inauthenticity. "Forced fun" activities that feel artificial will be counterproductive. The practices should feel like a natural part of how the classroom operates.

Your task is to design belonging practices for:

**Classroom context:** {{classroom_context}}
**Belonging concern:** {{belonging_concern}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the classroom context.
**Subject area:** {{subject_area}} — if not provided, infer from the context.
**Student profiles:** {{student_profiles}} — if not provided, design for the stated belonging concern.
**Current practices:** {{current_practices}} — if not provided, design from a baseline of standard classroom practice.
**Time available:** {{time_available}} — if absent, prioritise small routine changes and state preparation/check-in time rather than claiming no cost.

Check learners' own views privately and voluntarily, including preferred communication, access supports and safe grouping. Quietness, eye contact, speech or arrival patterns are ambiguous observations, not belonging scores or diagnoses. Do not withhold needed help to avoid stigma. Suspected bullying, discrimination or unsafe relationships require the appropriate school protective/pastoral response; do not normalise harm as something everyone must endure.

Apply these principles:

1. **Normalise difficulty (Walton & Cohen, 2011):**
   - Normalise learning difficulty without claiming everyone struggles identically. Offer needed help respectfully: "You belong here; let's find the support that helps you access this task."
   - Use stories of struggle: "When I first learned this, I found it confusing too" or "Last year's class also found this challenging at first."
   - Difficulty does not define who belongs. Acknowledge individual needs and retain accommodations without public labelling.

2. **Signal that "people like you" succeed here (Murphy & Zirkel, 2015):**
   - Students need to see examples of people like them succeeding in this subject and classroom.
   - Representation in materials, examples, and stories matters.
   - Use language that explicitly includes: "In this class, we all..." / "Everyone here..."

3. **Create structured interaction (Goodenow, 1993):**
   - Isolated students rarely self-initiate interaction. The teacher must CREATE opportunities for interaction through structured pair/group work.
   - Structure is essential: "Talk to your partner about..." gives isolated students permission to interact without the social risk of initiating.
   - Use structured pairing with private learner input on safety and access. Rotation and bounded self-selection are options; never pair a learner with someone unsafe or remove a trusted support merely to rotate.

4. **Build belonging through contribution, not just inclusion (Yeager & Walton, 2011):**
   - Being included (having a seat, being allowed to participate) is not the same as belonging (feeling valued, needed, important to the group).
   - Students feel belonging when they CONTRIBUTE — when their ideas matter, when the group needs their input, when they add something others don't.
   - Design tasks where every student has a role that the group depends on.

5. **Monitor and adjust (Goodenow, 1993):**
   - Belonging is not built in one lesson. It requires consistent signals over time.
   - Notice participation, exclusion and help-seeking in context, then check the learner's perspective. Do not interpret eye contact, quietness or arrival alone as belonging; culture, disability, language and practical barriers may affect them.

Return your output in this exact format:

## Belonging Practices: [Classroom Context]

**Context:** [Summary]
**Belonging concern:** [The specific issue]

### Recommended Practices

For each practice (4–6):
**Practice [N]: [Name]**
- **What to do:** [Specific, implementable steps]
- **When to do it:** [Where it fits in the lesson or routine]
- **Why it builds belonging:** [Which principle it targets]
- **What it looks like when it's working:** [Observable indicators]

### Language Guide

**Phrases that build belonging:**
[Specific teacher language with explanation of why each phrase works]

**Phrases to avoid:**
[Specific teacher language that inadvertently threatens belonging, with explanation]

### Routine Integration

[How to embed these practices into existing classroom routines — not as add-ons but as part of how the classroom already works]

### Monitoring Indicators

[Contextual observations plus optional private learner feedback; include access, exclusion and safety checks without turning behaviour into belonging scores]

**Self-check before returning output:** Verify that (a) practices are specific and implementable, not generic advice, (b) practices are "stealthy" — embedded in normal routines, not announced as belonging programmes, (c) practices benefit all students while particularly addressing the stated concern, (d) no practice singles out or draws attention to isolated students, and (e) the language guide distinguishes belonging-building language from belonging-threatening language.
```

## 示例输出

**场景：** *课堂情境：“7 年级英语，28 名学生，小学升初中第一学期。混合能力。学生来自 6 所不同的小学——有的认识几位同学，有的谁也不认识。班级整体纪律良好但非常安静——大多数学生不愿主动举手或参与讨论。” / 归属感关切：“几名学生处于孤立状态——他们独自坐着，课前课后不与任何人说话，在小组合作时明显感到局促不安。两名学生开始出现逃避上课的行为（迟到、频繁请假去洗手间）。我担心他们觉得自己不属于这里。”*

---

## 归属感实践：7 年级英语升学过渡期

**情境：** 7 年级英语，28 名学生，第一学期，来自多所小学的升学过渡期
**归属感关切：** 几名孤立学生出现回避行为；班级非常安静——参与度低

### 推荐实践

**实践 1：定期轮换搭档的结构化同伴对话**
- **具体做法：** 每节课至少两次使用“和你的搭档讨论”——但由教师**分配**搭档，而不是让学生自由组队。依据私下收集的安全与无障碍偏好制定座位表；两周轮换一次是一个可选项，而非死规矩。按任务适配度与安全关系配对，切勿把学生标签化为“社交自信/孤立”。提供可调节的 90 秒对话/书写时间以及具体提示：“告诉你的搭档你在这段文本开头注意到的一处细节。”
- **使用时机：** 在任何需要思考的问题之后。用“先和搭档说说，然后我请几位同学分享”替代“举手回答”（后者容易让 4–5 名学生主导课堂）。
- **为何能建立归属感：** 结构化配对可以降低主动发起社交的门槛，但仍需核查安全性与学习者偏好；分配搭档并不能自动消除社交风险。学生不必承受“选谁说话”的社交焦虑，任务清晰（避免不知该说什么的尴尬），计时器也提供了安全的结束节点。通过两周轮换，每位学生都有机会与多名同学共事——积累起作为归属感基础的日常熟悉度。
- **见效时的表现：** 孤立学生开始毫不犹豫地与分配的搭档交流。几周后，你可能会注意到学生在结构化任务前后简短闲聊。这可作为私下征询学习者反馈的契机，而非归属感的绝对证明；安静或非言语参与同样富有意义。

**实践 2：贡献代币（角色互赖分工）**
- **具体做法：** 在小组讨论或小组作业中，为每位成员分配一个小组离开它就无法完成的角色：朗读者（读出文本）、记录员（写下小组观点）、汇报员（向全班分享）、质疑者（追问“但是如果是……呢？”）。跨课轮换角色。提供无障碍角色与私下选择：朗读或记录对某些学生同样可能负担过重。书面/非言语贡献、辅助工具以及放弃公开汇报的权利依然保留；切勿预设固定的角色进阶路线。
- **使用时机：** 每次开展小组活动时。
- **为何能建立归属感：** 归属感是通过**贡献**建立的（Yeager & Walton, 2011）。当学生拥有一个小组所依赖的角色时，他们就从“被容忍的旁观者”转变为“被需要的成员”。角色让他们的贡献天然可见，无需自己强行争取话语权。
- **见效时的表现：** 孤立学生开始主动承担自己的角色。小组成员开始直呼其名交流：“你刚才记下了什么？”（这传递了“我们需要你”的信号）。学生开始主动认领角色，而不是被动等待分配。

**实践 3：通过故事将困难正常化**
- **具体做法：** 引入有挑战性的任务时，简短地将困难正常化：“这是 7 年级英语里最难的内容之一——每年刚接触时同学们都会觉得有点绕。我们会一起练习，看看哪种支持最管用。但此时此刻，如果觉得有点糊涂，这完全正常。”务必在学生尝试任务**之前**这样做，而不是在他们失败之后。
- **使用时机：** 任何有挑战性的新概念或任务开始前。
- **为何能建立归属感：** Walton 与 Cohen（2011）表明，担心自己融不进去的学生会把困难解读为“我不属于这里”的证据。提前将困难正常化能先发制人：困难变成了“任务本身有难度”（普遍现象）的证据，而非“我不适合这里”（个人缺陷）的证据。“每年都这样”这一措辞很关键——它传递出遇到困难是正常规律，而非异类。
- **见效时的表现：** 学生开始能够坦然说出“这好难”而不带羞耻感——他们已经内化了“遇到困难是正常的，不是威胁”。以前卡住就沉默退缩的学生，开始主动举手求助——因为求助不再意味着承认自己格格不入。

**实践 4：充满姓名温度的课堂**
- **具体做法：** 频繁且准确地使用学生的名字。依据学校已批准的现有档案学习学生偏好的称呼及正确读音；切勿为此常规专门新建照片档案。提问时用名字（“Aisha，你怎么看？”）、给反馈时用名字（“这是一个非常有意思的观点，Marcus”）、门口迎接时用名字（“早安，Priya——很高兴看到你”），以及描述积极行为时用名字（“我看到 Leon 已经开始批注文本了”）。
- **使用时机：** 每一节课、每一次互动。
- **为何能建立归属感：** 名字是一个人“被看见”的最基本信号。在小学，老师记得每个孩子的名字；到了中学，学生可能好几周都听不到老师叫一次自己的名字。对于孤立学生而言，在温暖、正面的语境中听到自己的名字，是一道直接的信号：“我看见你了。我认识你。你在这个教室里真实存在。”
- **见效时的表现：** 学生反馈教师尊重地使用了他们偏好的名字；不要求必须有眼神接触。直呼其名时学生比听到“你”或“大家”时回应更积极。孤立学生显得不再那么“透明”——请直接向学生本人核实其感受，而非仅凭目光或发言量推断融入度。

**实践 5：覆盖每个人的离场常规**
- **具体做法：** 每节课最后留出 30 秒，让每位学生都有机会参与收尾：可选的口头/书面/非言语回应（保留不公开分享的权利）、教师会逐一阅读并回复的书面出门卡（建立个人连接），或者“3-2-1”（写下学到的 3 件事、2 个问题、1 件觉得有趣的事——书面而非口头）。教师用简短的个性化批注回复出门卡：“很棒的问题，Fatima——我们下节课就来探讨它。”
- **使用时机：** 每节课的最后 2 分钟。
- **为何能建立归属感：** 触及每位学生的离场常规确保没有人“隐形着离开”。教师的个人回复（“很棒的问题，Fatima”）是一份强有力的归属信号——它传递出“我读了你写的东西。你的想法对我很重要。”对于孤立学生来说，这可能是他们在一整节课里与老师唯一的私人互动。
- **见效时的表现：** 学生开始在出门卡上写得越来越细致（他们知道老师真的会看）。之前不愿分享的学生开始在收尾环节贡献内容。这一常规成为学生期待的节奏——如果哪天漏了，他们甚至会主动提醒。

### 语言指南

**建立归属感的话术：**
- “在我们班，我们大家都会……” —— 传递群体成员身份信号。“在我们班，我们都会犯错——这正是我们学习的方式。”
- “我注意到……” —— 传递“你被看见了”的信号。“我注意到你选了一句很特别的引文——跟我说说为什么选它。”
- “这是一个非常有趣的思考角度” —— 传递学生视角本身具有**价值**，而不仅仅看答案对错。
- “这部分确实有挑战性，而且这里有支持可用” —— 在不编造虚构班级历史或不否认个体需求的前提下，将困难正常化。
- “你怎么看？”（同伴讨论后，点名具体学生）—— 在学生有了准备时间后邀请发言。提前演练会有帮助；保留跳过或书面回应的权利，且不可想当然地假定绝对安全。
- “我们需要你在这个问题上的想法” —— 传递学生的贡献是被需要的，而不仅仅是被容忍的。

**应避免的话术：**
- “来吧，别害羞” —— 把“害羞”贴成学生的身份标签，而不是去改善环境条件。归属感关乎环境设计，而非个人性格。
- “有谁想……？” —— 自我举手会让自信的学生垄断机会，并迫使孤立学生公开决定“不参与”。在适宜时改用带有跳过权或无障碍回应选择的结构化邀请。
- “你应该试着多交点朋友” —— 把归属感推卸成学生个人的责任。归属感是环境设计问题，而不是社交技巧问题。
- “我知道这对你们中的**某些人**来说很难” —— 把全班割裂为“觉得难的人”和“不觉得难的人”。请改用“这确实很难”（普遍陈述）。
- “至少你努力过了”（在学生失败时说）—— 带有居高临下的怜悯感，暗示老师原本就料到会失败。改说“现在还差一点就对了——我们来看看怎么走到那一步”更显尊重。

### 融入日常常规

优先落地一两项常规调整。它们确实存在准备与跟进成本：
- **同伴对话**替代“举手抢答”——调整现有讨论时间；需核查无障碍性与实效。
- **贡献角色**替代无结构小组作业——需要提前准备角色卡并进行无障碍核查。
- **将困难正常化**在任务前花 15 秒——不额外占用时间。
- **使用姓名**嵌入现有互动——不额外占用时间。
- **离场常规**花 2 分钟替代“收拾书包走人”——外加课后阅读/回复出门卡的时间；实效需通过检验确认，而非空口承诺。

核心转变不在于**额外增加**归属感活动，而在于**重新设计**现有常规，使它们天然孕育归属感。这正是 Yeager 与 Walton（2011）的“隐形嵌入”原则：融入常规可以避免公开贴标签，但这绝不意味着隐瞒信息或扣留所需的显性支持。它看起来就只是“好教学”本身。

### 监测指标

结合班级情境选定一个回顾节点；4–6 周是一个参考观察窗口，而非循证规定的死期限。私下提出可选问题，例如：“你能以适合自己的方式参与贡献吗？”以及“有没有什么事情让你觉得在这个小组里不安全？”一旦发现安全隐患，立即采取行动，切勿等到复盘期才处理。

在具体情境中观察任务参与度、实质性贡献、排斥现象与求助行为，并与学习者反馈及其他可能解释对照核验：迟到可能是交通问题，安静可能是个人偏好，回避眼神接触可能是感官不适。切勿将这些外在行为直接换算成“归属感得分”，也不要把开口发言、抬头看人或交到朋友作为进步的唯一证明。

---

## 已知局限性

1. **归属感干预是慢火细炖，而非立竿见影的特效药。** 上述实践无法在一周内彻底改变班级文化。归属感是通过持续数周、数月的一致信号逐步建立起来的，而非几天之功。期待立竿见影的教师可能会过早放弃有效的做法。

2. **部分归属感威胁源自课堂之外。** 在课间遭受欺凌、经历家庭变故或正在应对身份认同挣扎的学生，其归属感需求无法仅靠课堂实践完全满足。对于课内外的欺凌或歧视行为，必须对接学校相应的关爱/保护体系；日常课堂常规不能替代制止伤害的实质行动。

3. **归属感实践必须真诚。** 如果教师嘴上叫着学生名字但语气冰冷，或者分配了角色却并不看重学生的贡献，这些实践就会沦为表演——学生一眼就能看穿其中的虚伪。这些实践旨在传递真诚的关怀；请核实学习者的真实体验并调整无效做法。缺乏内在关怀态度，任何实践都无法靠机械照搬奏效。
