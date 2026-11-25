---
# AGENT SKILLS STANDARD FIELDS (v2)
name: ruler-emotional-literacy-sequence
description: "设计 RULER 情绪素养序列，培养识别（Recognising）、理解（Understanding）、命名（Labelling）、表达（Expressing）与调节（Regulating）情绪的能力。适用于学生在情绪调节、冲突或焦虑方面遇到困难的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/ruler-emotional-literacy-sequence"
skill_name: "RULER 情绪素养序列"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Brackett (2019) — Permission to Feel: the power of emotional intelligence to achieve well-being and success"
  - "Brackett et al. (2012) — RULER: a theory-driven, systemic approach to social and emotional learning"
  - "Rivers et al. (2012) — Improving the social and emotional climate of classrooms: a clustered randomized controlled trial of RULER"
  - "Hagelskamp et al. (2013) — Improving classroom quality with the RULER approach to social and emotional learning"
  - "Mayer & Salovey (1997) — What is emotional intelligence?"
input_schema:
  required:
    - field: "emotional_context"
      type: "string"
      description: "触发情绪素养需求的情境或学生行为——例如冲突、考前焦虑、协作困难、情绪爆发"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科——用于将 RULER 融入学科内容"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：班级情绪氛围数据、特定学生需求"
    - field: "time_available"
      type: "string"
      description: "可分配的时间——嵌入课程、班会时间或专项环节"
    - field: "ruler_familiarity"
      type: "string"
      description: "学生之前是否接触过 RULER 工具——情绪仪（Mood Meter）、元时刻（Meta-Moment）、蓝图（Blueprint）"
output_schema:
  type: "object"
  fields:
    - field: "ruler_sequence"
      type: "object"
      description: "运用 RULER 技能的结构化序列——识别、理解、命名、表达、调节"
    - field: "tool_selection"
      type: "string"
      description: "最适合的 RULER 工具——情绪仪、元时刻、蓝图或班级宪章（Charter）"
    - field: "integration_plan"
      type: "object"
      description: "如何将 RULER 序列嵌入学科内容或课堂常规"
    - field: "teacher_modelling"
      type: "string"
      description: "教师应如何亲身示范 RULER 技能——情绪素养始于教师"
chains_well_with:
  - "belonging-classroom-culture-designer"
  - "trauma-informed-practice-designer"
  - "restorative-practice-protocol-designer"
  - "perma-based-lesson-designer"
teacher_time: "3 分钟"
tags: ["RULER", "emotional-intelligence", "Brackett", "Yale", "SEL", "emotional-literacy", "mood-meter"]
---

# RULER 情绪素养序列（RULER Emotional Literacy Sequence）

## 本技能的功能

运用耶鲁大学情商中心（Yale Center for Emotional Intelligence）的 RULER 框架，设计一套入门级的教育适配方案来培养情绪素养——教导学生在自己和他人身上**识别**（Recognise）情绪、**理解**（Understand）情绪的成因与后果、用细腻的词汇**命名**（Label）情绪、恰当地**表达**（Express）情绪，以及运用有效策略**调节**（Regulate）情绪。输出包括具体选用的 RULER 工具（情绪仪 Mood Meter、元时刻 Meta-Moment、蓝图 Blueprint 或宪章 Charter）、如何引入和实施、如何将情绪素养融入学科内容而非孤立对待，以及教师自身应如何示范这些技能——因为情绪素养始于教师，而非学生。AI 在此具有独特价值，因为针对特定课堂情境挑选恰当的 RULER 工具、按年龄段调整语言并将情绪素养融入学科内容，同时需要情绪智力专业知识与教学法知识。

## 循证依据

Brackett（2019）与 Brackett 等（2012）在耶鲁大学情商中心基于 Mayer 与 Salovey（1997）的能力型情商模型开发了 RULER。RULER 将情绪智力视为一组可教习的技能，而非天生的人格特质：识别（从面部表情、声音、肢体语言和自身身体反应中辨识情绪）、理解（了解情绪的诱因与后果）、命名（使用精准词汇——不只是“好”或“坏”，而是“沮丧”、“忐忑”、“振奋”等具体情绪词）、表达（了解何时何地以何种方式恰当表达情绪）以及调节（运用策略管理情绪体验——不是压抑情绪，而是有效回应情绪）。Rivers 等（2012）在 62 个班级开展了 RULER 的整群随机对照试验，发现课堂情绪氛围显著改善，包括更多的情感支持、更好的课堂组织以及更强的教学支持。Hagelskamp 等（2013）发现 RULER 在 CLASS 课堂观察系统的全部三个维度上均提升了课堂质量。关键在于，RULER 始于教师——“情商四大锚点”（情绪仪、元时刻、蓝图、宪章）首先由教职工练习，然后再引入学生。成人示范是一项核心实施实践；项目层面的研究证据并不直接确立每一份生成的短序列本身的有效性。

## 输入规范

教师必须提供：
- **情绪情境：** 触发此需求的具体情况。*例如：“学生在模拟考前极度焦虑——有几名学生哭泣、拒绝进考场或彻底僵住” / “两个朋友圈之间存在持续的低烈度冲突，干扰了协作学习” / “一名学生频繁出现无法控制的情绪爆发（大喊、冲出教室）”*
- **学生水平：** 年级。*例如：“8 年级”*

可选（如情境引擎可用，将自动注入）：
- **学科领域：** 课程学科
- **学生档案：** 情绪氛围数据、特定需求
- **可用时间：** 可分配的时长
- **RULER 熟悉度：** 学生之前是否使用过 RULER 工具

## Prompt

```
You are an expert in emotional intelligence and social-emotional learning, with deep knowledge of Brackett's (2019) RULER framework, Mayer & Salovey's (1997) ability model of emotional intelligence, and the evidence from Rivers et al. (2012) and Hagelskamp et al. (2013) on RULER's impact on classroom climate and learning. You understand that emotional literacy is a set of teachable skills — not a personality trait — and that it begins with the teacher modelling the skills, not just teaching them.

The RULER framework uses four "Anchors of Emotional Intelligence":

1. **The Charter:** A collaboratively created set of agreements about how class members want to feel and what they'll do to support those feelings. Created at the start of the year.
2. **The Mood Meter:** A tool for recognising and labelling emotions using two dimensions — pleasantness (horizontal axis: unpleasant to pleasant) and energy (vertical axis: low to high). The four quadrants are: Red (high energy, unpleasant — angry, anxious, frustrated), Yellow (high energy, pleasant — excited, happy, energised), Green (low energy, pleasant — calm, content, peaceful), Blue (low energy, unpleasant — sad, tired, lonely).
3. **The Meta-Moment:** A pause between a trigger and a response — "How do I feel? How would my best self respond? What strategy can I use?" Used when emotions are intense and the automatic response would be unhelpful.
4. **The Blueprint:** A tool for understanding and resolving conflict — "Before, during, after: what happened, how did each person feel, what were the consequences, how can we move forward?" Used for interpersonal situations.

Your task is to design a RULER sequence for:

**Emotional context:** {{emotional_context}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, design as a standalone sequence that can be integrated into any lesson or tutor time.
**Student profiles:** {{student_profiles}} — use only relevant non-identifying access needs; if absent, provide low-disclosure and accessible options without inventing emotional profiles.
**Time available:** {{time_available}} — if not provided, offer a 15–20-minute introduction, clearly distinguished from full programme implementation.
**RULER familiarity:** {{ruler_familiarity}} — if not provided, assume students are new to RULER and introduce the tools from scratch.

This short sequence is an adaptation, not an evaluated full RULER implementation or therapy. Check the teacher's preparation/training and authorisation to use chosen programme materials; do not invent licensing terms. Use private self-reflection or fictional/character examples by default, with an option to pass or use a non-personal task. No emotion or cause needs public display. Do not infer an internal state from appearance, behaviour or a Mood Meter colour; invite the learner's own words without insisting. Retain access supports, offer non-breathing strategies and never guarantee calming. Persistent or severe distress needs appropriate human support; urgent safety concerns follow existing school safeguarding/emergency procedures.

Apply these principles:

1. **Select the right RULER tool for the situation:**
   - Mood Meter: for building emotional awareness and vocabulary (general emotional literacy).
   - Meta-Moment: for managing intense emotional responses (individual regulation).
   - Blueprint: for resolving interpersonal conflict (relationship repair).
   - Charter: for establishing classroom emotional norms (prevention, culture-building).

2. **Teacher models first (Brackett, 2019):**
   - The teacher MUST model the tool before asking students to use it.
   - "I'm going to show you where I am on the Mood Meter right now. I'm in the Yellow — I'm energised and interested because I'm curious about what you'll think of today's topic."
   - Modelling vulnerability (not every emotion is pleasant) is more powerful than modelling only positive emotions.

3. **Build emotional vocabulary (Mayer & Salovey, 1997):**
   - Move students beyond "fine," "good," "bad," "annoyed" to precise vocabulary: apprehensive, exhilarated, melancholy, content, frustrated, curious, overwhelmed, serene.
   - The Mood Meter helps: each quadrant contains 20+ emotion words at increasing levels of granularity.
   - Precision matters: "I'm frustrated" leads to a different response than "I'm anxious." Both might be called "bad" without vocabulary.

4. **Integrate into academic content where possible:**
   - Analyse characters' emotions using the Mood Meter in English.
   - Discuss the emotions of historical figures using the Blueprint in History.
   - Examine the emotional dimension of scientific discovery or ethical dilemmas.
   - Integration is more sustainable than standalone sessions.

5. **Regulation is NOT suppression:**
   - RULER teaches students to RESPOND to emotions, not to suppress them.
   - "Don't be angry" is not emotional regulation. "I notice I'm angry — what's causing it, and what would be a helpful response?" IS regulation.
   - All emotions are valid; not all behaviours are appropriate. RULER helps students separate the emotion (always OK) from the behaviour (which they can choose).

Return your output in this exact format:

## RULER Sequence: [Context Description]

**Emotional context:** [The situation]
**For:** [Student level]
**RULER tool(s):** [Which anchor(s) to use]

### Teacher Modelling

[How the teacher should model the RULER skill first — specific language and example]

### Sequence Steps

For each step:
**Step [N]: [RULER Skill — Recognise/Understand/Label/Express/Regulate]**
- **Activity:** [What students do]
- **Teacher script:** [Specific language to use]
- **What to look for:** [Signs the step is working]

### Academic Integration

[How to embed this sequence into subject content — specific examples]

### Sustaining the Practice

[How to maintain emotional literacy beyond this sequence — routines, language, ongoing use of tools]

**Self-check before returning output:** Verify that (a) the right RULER tool is selected for the situation, (b) the teacher models the skill before students practise it, (c) emotional vocabulary is expanded beyond basic terms, (d) regulation is taught as response management, not emotion suppression, and (e) the sequence is practical and time-efficient, and (f) privacy/pass/fictional options, accessible strategy choices and the human-support boundary are present in each activity.
```

## 示例输出

**场景：** *情绪情境：“9 年级学生在首次模拟 GCSE 考试前极度焦虑。几名学生在课上哭泣，两名学生要求见心理辅导员，班里整体氛围低沉紧张。学生嘴里说着‘我肯定考砸了’、‘复习有什么用——我根本学不会’、‘一想到考试我就想吐’。” / 学生水平：“9 年级” / 可用时间：“班会时间 20 分钟，外加融入学科课堂” / RULER 熟悉度：“学生在墙上见过情绪仪，但尚未系统使用过”*

---

## RULER 序列：考前焦虑

**情绪情境：** 9 年级考前焦虑——哭泣、回避、自我否定言论、躯体症状
**适用对象：** 9 年级
**RULER 工具：** 情绪仪 Mood Meter（用于识别与命名）+ 元时刻 Meta-Moment（用于调节）

### 教师示范

在向学生介绍工具之前，教师先示范自己的情绪体验。使用有边界的真实示例或明确标注的虚构示范；教师无需披露个人深层痛苦。

“我想和大家分享一件事。看情绪仪时，我此刻大概在这个位置[指向左上象限——红色区域，但处于中等程度]。我会用‘忐忑不安’（apprehensive）来形容自己。这周我有很多事要忙，我注意到一想到这么多事堆在一起，胸口就会发紧，脑子里开始冒出‘我肯定干不完’的想法。听起来是不是很耳熟？这种感觉完全正常——这是大脑在告诉我这件事很重要。但我学到的是：如果我一直停留在那个区域里什么都不做，我反而会完成得**更少**，而不是更多。所以我想和大家分享一个我自己常用的策略，然后我们一起来试试。”

### 序列步骤

**第一步：识别（Recognise）——只觉察，不强制披露（5 分钟）**
- **活动：** 示范情绪仪后，提供三种可选方式：在学习者自己保管的纸上做私密个人标记、使用虚构角色案例，或选择跳过/完成非个人词汇任务。切勿收集或公开张贴任何个人情绪状态（即使匿名也不行）。
- **教师话术：** “你们可以把这个记在自己手里、用我们虚构的学生案例，或者跳过。没有‘应该选哪个象限或哪种情绪’的标准答案。我也不会仅凭你们的表情去猜测你们的感受。”
- **观察要点：** 在所选案例中对“能量/愉悦度”两个维度的理解。安静、选了什么颜色或是否发言，均不构成焦虑诊断，也不能证明产生了治疗效果。

**第二步：命名（Label）——找到一个好用的词（5 分钟）**
- **活动：** 提供细腻的情绪词汇，如“忐忑”（apprehensive）、“焦虑”（anxious）、“挫败”（frustrated）或“不堪重负”（overwhelmed）。学习者可以选择自己的词汇、语言或无障碍沟通方式；词义定义是语言支持工具，而非临床诊断分类。
- **教师话术：** “哪个词最贴合你的例子？你也可以选别的词，或者说还不确定。不需要告诉全班。”
- **观察要点：** 在有帮助的情况下描述变得更精准；切勿为了迎合教师的预设解释而强行“纠正”学习者自己报告的情绪。

**第三步：理解（Understand）——探索可能的原因（5 分钟）**
- **活动：** 使用虚构考试场景：“这名学生说自己感到‘不堪重负’；可能有哪些原因，我们需要问什么才能弄清楚？”个人反思保持私密且自愿；不强制要求向同伴解释。
- **教师话术：** “我们无法从别人的脸上看出原因。不同的原因可能需要不同的支持，包括调整任务或环境。”
- **观察要点：** 试探性的解释，而非下诊断。把情绪说出来是一项词汇与认知活动，而非包治百病的承诺。

**第四步：调节（Regulate）——元时刻（Meta-Moment）（5 分钟）**
- **活动：** 示范一次暂停：觉察感受、思考自己希望做出怎样的回应、选择一个可行的策略。提供策略菜单：
  - **可选的舒适呼吸：** 仅在学习者自愿选择时使用；不要求固定秒数或屏息。感到不适立即停止。
  - **任务切块（Chunking）：** 在适当支持与时间安排下，挑选一个力所能及的复习小步。
  - **认知重构（Reframing）：** “一次考试成绩提供的是关于这份作业的信息，它不能定义我的个人价值。”
  - **连接或着陆（Connection or grounding）：** 若有帮助且可行，向信任的成人求助，或把注意力放在熟悉的物体/环境上。
- **教师话术：** “你可能会感到焦虑、平静、不确定或其他感受。挑一个适合你的策略试试，或者跳过；没有任何策略保证对每个人都管用。如果痛苦持续存在，我们会寻求恰当的支持。”
- **观察要点：** 学习者自选的应对计划以及关于策略是否有用的自愿反馈；切勿将安静服从误判为情绪已调节好。

### 学科融合

- **英语：** 分析处于压力下的文学人物（谋杀前的麦克白、被流放后的罗密欧）时，把人物放到情绪仪上。“麦克白现在处于哪个位置？是什么导致的？对她/他来说，元时刻会是什么样子？”这能同时培养文本分析能力与情绪词汇量。

- **科学：** 在实操考核前：“如果有帮助，可以私下自我检查或用虚构例子练习。开始前选一个你熟悉的策略或主动求助；不需要公开分享你的感受。”无论情绪状态如何，均须遵守实验安全指令。

- **历史：** 研究在压力下做出艰难抉择的历史人物（闪电战期间的丘吉尔、面临监禁的妇女参政者）时：“使用蓝图工具。他们当时是什么感受？是什么引发了这些感受？情绪如何影响了他们的决策？”

### 持续实践

1. **让情绪仪可见并融入日常。** 挂在墙上。每节课开始时简短签到（30 秒：“你在情绪仪的哪个位置？不需要说出来——自己觉察一下就好”）。长期观察学习者是否觉得这些词汇有用；不假定学生必然会自发使用。

2. **当**你**自己感到挫败时，亲身示范元时刻。** “我要停下来用一下元时刻。我现在很沮丧，因为设备坏了。我的本能反应是发火——但那修不好投影仪。我最好的自己会说：喘口气，再试一个办法，不行就换方案。好——让我来试一下。”

3. **让情绪词汇常态化。** 在日常交流中使用情绪词：“你需要支持，还是想先自己继续？” / “我们虚构的主人公说自己感到‘充满干劲’——在这里可能是什么意思？”教师越常使用精准的情绪语言，学生就越容易接纳并运用它。

4. **在每次高利害事件前回到元时刻。** 考试前、演讲前、家长会前：“我们来做一次元时刻检查。你现在在哪里？最好的自己此刻需要什么？”

---

## 已知局限性

1. **RULER 是一套全校性项目，而非单节课干预。** 上述序列只是引入了 RULER 工具，其完整效用需要跨多个课堂的持续使用、融入学校文化以及教职工培训。这套生成的入门序列本身的收益尚未实证确立；切勿将经过完整培训的项目研究结果直接套用到这份短脚本上。

2. **情绪素养不能替代临床专业支持。** 患有焦虑症、抑郁症或创伤反应的学生需要专业支持——学校心理咨询师、儿童青少年心理健康服务（CAMHS）转介或治疗性干预。RULER 面向普通学生群体培养情绪技能；它不能替代临床服务。如果学生的痛苦持续或严重，必须在 RULER 之外配合适当的专业转介。

3. **教师必须真诚示范。** RULER 要求教师自身具备情绪素养——在不强求个人隐私暴露的前提下，示范有边界的例子、演示元时刻并使用精准词汇。对情绪表达感到极度不适的教师会发现很难真诚地实施 RULER。教师专业发展与支持性的校园文化是有效实施的前提条件。
