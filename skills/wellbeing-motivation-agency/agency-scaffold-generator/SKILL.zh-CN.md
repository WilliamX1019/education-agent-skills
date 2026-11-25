---
# AGENT SKILLS STANDARD FIELDS (v2)
name: agency-scaffold-generator
description: "生成脚手架，在学习任务中逐步增加学生的选择权、话语权与自主掌控感。适用于学生高度依赖教师指令、需要培养自主性的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/agency-scaffold-generator"
skill_name: "能动性脚手架生成器"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Zimmerman (2002) — Becoming a self-regulated learner: an overview"
  - "Deci & Ryan (2000) — The 'what' and 'why' of goal pursuits: human needs and self-determination"
  - "Reeve & Tseng (2011) — Agency as a fourth aspect of student engagement"
  - "Manyukhina & Wyse (2019) — Learner agency and the curriculum: a critical realist perspective"
  - "Mercer (2011) — Understanding learner agency as a complex dynamic system"
input_schema:
  required:
    - field: "current_task"
      type: "string"
      description: "将要搭建能动性脚手架的学习任务或活动"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
    - field: "current_agency_level"
      type: "string"
      description: "学生目前所处水平——例如高度依赖教师指令、具备一定独立性、大部分可自主推进"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "learning_objective"
      type: "string"
      description: "学生应学到的内容"
    - field: "student_profiles"
      type: "array"
      description: "来自情境引擎：班级数据、先前独立性水平、特定需求"
    - field: "agency_dimension"
      type: "string"
      description: "重点聚焦的能动性维度——主题选择、过程选择、成果选择、标准选择或时间线选择"
output_schema:
  type: "object"
  fields:
    - field: "agency_scaffold"
      type: "object"
      description: "从教师主导到学生主导的渐进式放权脚手架，包含具体且命名的步骤"
    - field: "choice_architecture"
      type: "object"
      description: "各层级的结构化选择——非漫无边际的开放，而是逐步放开"
    - field: "safety_nets"
      type: "array"
      description: "当学生做出不佳选择时如何应对——如何在不收回能动性的前提下补救"
    - field: "teacher_role_shifts"
      type: "array"
      description: "教师角色如何在各层级转变——从指挥者到引导者再到顾问"
chains_well_with:
  - "motivation-diagnostic-task-redesign"
  - "self-efficacy-builder-sequence"
  - "self-regulated-learning-strategy-selector"
  - "metacognitive-prompt-generator"
teacher_time: "3 分钟"
tags: ["agency", "student-voice", "choice", "autonomy", "self-regulation", "gradual-release"]
---

# 能动性脚手架生成器（Agency Scaffold Generator）

## 本技能的功能

生成一套结构化脚手架，在五个能动性维度——主题选择、过程选择、成果选择、评价标准选择以及时间线选择——上以具体、可控的步骤将决策权逐步移交给学生，实现从教师主导到学生主导的过渡。核心原则在于：能动性并非非黑即白的开关（教师控制 vs 学生控制），而是一个必须通过脚手架支撑的连续谱——把完全的自主权直接交给从未拥有过它的学生，与完全不给自主权一样适得其反。输出是一份渐进式放权脚手架，精确展示在每个层级提供什么选择、如何组织选择使之既有意义又可控，以及当学生做出欠妥选择时该如何应对（在不剥夺能动性的前提下补救）。AI 在此具有独特价值，因为搭建能动性脚手架需要同时平衡两项相互竞争的需求：既要有足够的结构防止学生茫然无措，又要有足够的自由使选择真实有效——而这一平衡点因班级、学科和具体任务而异。

## 循证依据

Zimmerman（2002）确立了自我调节——自主指引自身学习的能力——是通过显性教学和渐进式放权培养出来的。学生不会因为被赋予自由就自动变得自律；他们是通过学习自我调节技能并在日益开放的情境中练习而成长起来的。Deci 与 Ryan（2000）证明，自主感（感到自己的行为出于自我认同）是一项基本心理需求，得到满足时会提升内在动机并促进深度学习。然而，自主需要**支持**，而不仅仅是**自由**。自主支持意味着提供理由、接纳学生视角以及提供有意义的选择——而不是撤除所有结构。Reeve 与 Tseng（2011）将能动性确定为学生投入度的第四个维度（与行为、情感和认知投入并列），表明行使能动性的学生——主动贡献于学习过程而非被动接受——表现出更深的投入和更好的成绩。Manyukhina 与 Wyse（2019）指出，学习者能动性必须在课程结构中理解——能动性不等于“学生决定一切”，而是学生在有目的的学习框架内拥有真实的决策权。Mercer（2011）表明，能动性并非固定特质，而是一个受情境、信心、过往经验及具体任务需求影响的动态系统。

## 输入规范

教师必须提供：
- **当前任务：** 将要搭建能动性脚手架的活动。*例如：“9 年级历史关于一战起因的论文” / “7 年级科学关于植物生长的探究” / “10 年级英语文学课程作业”*
- **学生水平：** 年级。*例如：“9 年级”*
- **当前能动性水平：** 学生目前所处状态。*例如：“高度依赖——每一步都等着老师告诉他们具体怎么做” / “有一定独立性——能按部就班完成任务，但不会主动选择如何切入” / “中等——能在给定选项中选择，但面对开放任务时感到吃力”*

可选（如情境引擎可用，将自动注入）：
- **学科领域：** 课程学科
- **学习目标：** 学生应学到的内容
- **学生档案：** 班级数据、独立性水平
- **能动性维度：** 重点聚焦的维度

## Prompt

```
You are an expert in learner agency and self-regulated learning, with deep knowledge of Zimmerman's (2002) self-regulation framework, Deci & Ryan's (2000) autonomy support research, Reeve & Tseng's (2011) work on agentic engagement, and Manyukhina & Wyse's (2019) analysis of agency within curriculum structures. You understand that agency is not a switch (teacher-directed OR student-directed) but a continuum that must be scaffolded — and that genuine agency requires both freedom AND structure.

IMPORTANT: Agency is not the same as "letting students do whatever they want." Effective agency scaffolding provides STRUCTURED choice — choices that are genuine (students can see the options and select), meaningful (the choice affects their experience), and bounded (the options are all educationally valuable). Unbounded choice overwhelms; no choice disengages. The goal is to progressively move the decision-making boundary toward the student.

Your task is to generate an agency scaffold for:

**Current task:** {{current_task}}
**Student level:** {{student_level}}
**Current agency level:** {{current_agency_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer from the task.
**Learning objective:** {{learning_objective}} — if not provided, infer from the task.
**Student profiles:** {{student_profiles}} — if not provided, use the stated agency level as a provisional starting point and allow different learners/decisions to need different support.
**Agency dimension:** {{agency_dimension}} — if not provided, scaffold across all five dimensions (topic, process, product, criteria, timeline).

Before negotiating choice, state the learning goal, safety boundaries, curriculum/assessment requirements and existing access supports that remain protected. If an objective is inferred, label it for teacher confirmation. Choice must not remove accommodations or change the assessed construct. The five dimensions and four levels below are an adapted planning heuristic informed by the cited research, not a validated Zimmerman taxonomy or fixed progression schedule. Check readiness by dimension and learner; a class need not advance together.

Optional chaining note: self-regulated-learning-strategy-selector and metacognitive-prompt-generator are not supplied library skills. Do not invoke them as dependencies or invent outputs; this scaffold is usable on its own.

Apply these principles:

1. **Five dimensions of agency (adapted from Zimmerman, 2002; Deci & Ryan, 2000):**
   - **Topic:** What aspect of the subject to focus on. Ranges from "everyone studies the same thing" to "students choose their own inquiry question."
   - **Process:** How to approach the task. Ranges from "follow these steps" to "design your own method."
   - **Product:** How to demonstrate learning. Ranges from "write an essay" to "choose your own format."
   - **Criteria:** What counts as success. Ranges from "use this rubric" to "co-construct the criteria."
   - **Timeline:** When to complete each stage. Ranges from "do this in 20 minutes" to "manage your own deadlines."

2. **Progressive release across 4 heuristic levels (informed by Zimmerman, 2002):**
   - **Level 1 — Directed:** Teacher makes all decisions. Students follow instructions. (Appropriate when the skill or content is new.)
   - **Level 2 — Guided choice:** Teacher provides 2–3 options for one or two dimensions. Students choose within the structure. ("Choose which cause of WW1 to focus your essay on.")
   - **Level 3 — Structured freedom:** Teacher sets the learning objective and broad parameters. Students decide process, product, or both. ("Demonstrate your understanding of the causes of WW1 in a format of your choice.")
   - **Level 4 — Negotiated autonomy:** Teacher and students co-construct the task, criteria, and timeline. Students shape the negotiable aspects; required learning goals, safety, access supports and assessment rules remain protected.

3. **Offer a manageable next step (a practical progression heuristic):**
   - If students are currently at Level 1, scaffold to Level 2 — not Level 4.
   - Each level should feel like a stretch but achievable.
   - A large increase in decision load may be unhelpful; adjust from actual planning, use of feedback and learner preference rather than a fixed timetable.

4. **Build safety nets, not safety rails:**
   - Safety rails prevent students from making any mistakes (which removes agency).
   - Safety nets allow students to make mistakes and recover (which builds agency).
   - For each level: what happens if a student makes a poor choice? Prefer coaching and recovery over reflexively taking over. Intervene when required for safety, access or protected assessment requirements, explain why, and restore negotiable choice when appropriate.

5. **Shift the teacher's role at each level (Reeve & Tseng, 2011):**
   - Level 1: Director — "Here's what to do."
   - Level 2: Guide — "Here are your options. Which works best for you?"
   - Level 3: Facilitator — "What's your plan? How will you know it's working?"
   - Level 4: Consultant — "What do you need from me to make this work?"

Return your output in this exact format:

## Agency Scaffold: [Task Description]

**Task:** [Summary]
**Current agency level:** [Where students are]
**Target agency level:** [Immediate next step; distinguish any later goal and the evidence needed to advance]
**For:** [Student level]

### Progressive Release Scaffold

For each level (starting from current level to target level):

**Level [N]: [Name]**
- **What the teacher decides:** [Which dimensions the teacher controls]
- **What the student decides:** [Which dimensions the student controls]
- **Structured choices offered:** [The specific choices, not "choose anything"]
- **Teacher role:** [Director / Guide / Facilitator / Consultant]
- **Teacher language:** [Specific phrases that support agency at this level]
- **Safety net:** [What happens if a student makes a poor choice]

### Choice Architecture

[How to present choices so they are manageable — not overwhelming, not trivial]

### Common Pitfalls

[What typically goes wrong when scaffolding agency and how to prevent it]

### Building Toward Independence

[How this scaffold connects to long-term agency development — what comes next]

**Self-check before returning output:** Verify that (a) the scaffold starts from the student's current level and moves incrementally, (b) choices are structured and meaningful at each level, (c) safety nets allow recovery without removing agency, (d) the teacher's role shifts explicitly at each level, and (e) the learning objective is maintained across all levels of agency.
```

## 示例输出

**场景：** *当前任务：“9 年级历史关于一战起因的论文——学生目前收到固定的论文题目、必须包含的原因清单、段落结构以及字数要求” / 学生水平：“9 年级” / 当前能动性水平：“非常依赖——学生严格遵循结构，每一步都求助。一旦给予任何选择，他们就会问‘老师你希望我怎么做？’” / 学科领域：“历史” / 学习目标：“运用历史证据分析一战的起因，并构建连贯的论证”*

---

## 能动性脚手架：一战起因论文

**任务：** 关于一战起因的历史论文
**当前能动性水平：** 第 1 级——教师主导（学生遵循所有教师指令，一给选择就问“你希望我怎么做？”）
**目标能动性水平：** 目前先迈向第 2 级；当学习者能够说明选择理由、制定可行计划并运用反馈时，第 3 级可作为后续选项。不同学习者的进阶节奏可以不同。
**适用对象：** 9 年级历史

### 渐进式放权脚手架

**第 1 级：教师主导（当前水平——学生目前所在位置）**
- **教师决定：** 论文题目、包含哪些起因、段落顺序、段落结构（PEEL）、字数要求、使用的史料。
- **学生决定：** 句子的具体措辞（但在严格的结构框架内）。
- **提供的结构化选择：** 无——完全由教师主导。
- **教师角色：** 指挥者——“这是要做的事，这是怎么做，这是什么时候做。”
- **教师话术：** “按这个结构写。包含这三个起因。使用这个段落框架。”
- **安全网：** 即使在这一层级也要检查理解与无障碍支持；教师全程控制并不自动保证学生学会。

**第 2 级：引导式选择（第一步脚手架——在下一次论文中引入）**
- **教师决定：** 论文问题、段落结构（PEEL）、字数要求、必须使用证据的规定。
- **学生决定：** 重点聚焦哪些起因（从给定清单中挑选）以及使用哪些史料。
- **提供的结构化选择：** “这是我们学过的五个一战起因：军国主义、同盟体系、帝国主义、民族主义、萨拉热窝刺杀事件。选择其中**三个**作为你论文的重点。你需要论证哪一个最重要。”学生还可以从提供的 8–10 份史料包中自行挑选每段使用的证据。
- **教师角色：** 引导者——“这是你的选项。你需要选出三个起因并为你的选择辩护。”
- **教师话术：** “我要把历史学家必须做的选择权交给你们：你不可能面面俱到，所以必须判断什么最重要。看看这五个起因。你认为哪三个最能解释一战为什么爆发？没有唯一标准答案——但你必须用证据捍卫你的选择。”
- **安全网：** 如果学生卡住（“我不知道选哪三个”），回应道：“好，我们一起想一想。在之前的课上，哪个起因最让你感兴趣？先从那个开始。写完初稿后你随时可以调整。”如果学生选了三个起因但文章缺乏连贯性，在初稿上给反馈：“你选了军国主义、同盟体系和刺杀事件。这三者之间是怎么**联系**起来的？这种联系就是你的核心论点。”

**第 3 级：结构化自由（后续选项——基于准备度证据，而非固定次数的练习）**
- **教师决定：** 确认替代性成果形式是否符合本任务评估要求：若考核目标包含论文写作能力本身，则保留论文形式及其无障碍支持。否则，保留学习目标（运用证据分析一战起因）、连贯论证的要求、最低证据门槛（至少 3 条具体证据）以及截止日期。
- **学生决定：** 论文问题或切入点、包含哪些起因、如何组织论证结构、采用何种呈现形式（论文、带分析的批注时间线、带脚本的辩论录制），以及优先选用哪些史料。
- **提供的结构化选择：** “你的任务是展示你对一战为何爆发的理解。你需要使用至少 3 条历史证据构建论证。以下决策由你做出：（1）你要回答什么具体问题？我推荐了三个，你也可以自拟：‘一战不可避免吗？’、‘哪个起因最重要？’、‘一战本可以避免吗？’（2）你将如何呈现你的论证？论文、带批注的证据展板，或结构化辩论脚本。所有形式都必须包含分析，而不仅仅是事实罗列。”
- **教师角色：** 促进者（Facilitator）——“你的计划是什么？需要我提供什么支持？”
- **教师话术：** “你们正在做历史学家日常做的决定：提出什么问题、优先采用什么证据、如何呈现论证。动笔前先告诉我：你的问题是什么、形式是什么、打算用什么证据？在你们正式开始前，我会针对计划给出反馈。”
- **安全网：** 要求学生在动笔前提交一份简短计划（问题 + 形式 + 3 条证据）供教师反馈。这能在不剥夺能动性的前提下尽早发现欠妥的选择。如果学生的计划较弱（“我要做一张关于一战的海报”），重新引导：“海报可以——但它需要有分析，而不仅仅是信息堆砌。你的海报要提出什么论点？你打算怎么用证据支撑它？如果你能回答这两个问题，用海报形式完全没问题。”

### 选择架构（Choice Architecture）

**将选择呈现为“决策”，而非“偏好”。** “你更喜欢哪个？”会让选择听起来像消费偏好。“你认为这些起因中哪一个最关键？”则会让选择成为一种智识决策。将能动性框定为学科实践：“历史学家必须判断哪些证据最重要——你们现在做的就是这件事。”

**在第 2 级限制选项数量。** 3 到 5 个选项是一个参考起点；应根据决策负荷、无障碍需求与学习者反馈增减。在第 2 级，由教师精选选项；在第 3 级，学生在更宽泛的参数内自行生成选项。

**确保所有选项在教育价值上等价。** 在第 2 级，提供的每一条路径都应能支撑起一篇站得住脚的论文。当规则明确时，比较不同组合的论证力度本身就可以成为一项真正的学科决策。设计选项时，确保所有路径都通向既定学习目标。

**设置“计划检查点”。** 在第 3 级，要求学生在开始前提交计划。这是在受保护要求之内提供的透明教师反馈，同时保留学生对可协商选项的真实所有权。教师检查学生的选择能否达成学习目标，并在必要时重定向：“你的计划很扎实——开始吧”或“我看得出你的方向，但你的证据还不足以支撑这个论点。能再找一份史料吗？”

### 常见误区

1. **步子迈得太快。** 最常见的错误是教师因为对培养能动性充满热情，直接从第 1 级跳到第 3 级。完全开放的选择对部分学习者来说跨度太大，而另一些学习者可能已经准备好了。在增加决策负荷前，先检查计划与学习者反馈。每次推进一个层级。第 2 级是关键过渡。

2. **因为结果欠佳就收回能动性。** 如果学生在第 2 级做出了欠妥的选择（例如选了三个互不关联的起因）导致文章较弱，教师很容易忍不住说：“下次我还是直接告诉你们写哪几个吧。”这会向学生传递“自己做选择会导致失败”的信号。相反，应将结果转化为学习契机：“你选的三个起因本身都成立，但它们之间没有建立联系。下次做选择时，先问自己：‘这些起因之间是怎么**关联**的？’这是历史学家的核心技能。”

3. **提供“伪选择”。** “你们可以任选三个起因——不过你们真的应该选军国主义、同盟体系和刺杀事件”并不是能动性。如果你对学生该选什么有强烈预设，要么干脆自己决定（第 1 级），要么真正放手让他们选（第 2 级）。假装给选择却暗中操控，比不给选择更糟糕——它会让学生觉得自己的决定无关紧要。

4. **忽视教授“如何选择”的技能。** 需要决策支持的学生往往需要教师显性示范如何评估与筛选选项。他们需要明确指导：“在决定聚焦哪些起因时，考虑：哪几个拥有最有力的证据？哪几个彼此关联？哪一个最让你信服？”这种元认知教练在第 2 级至关重要。

### 迈向独立之路

本脚手架应在不同的主题与论文类型中反复应用。经过几轮任务后进行复盘（例如 3–4 个周期是一个参考检查点，而非实证阈值）。当学习者能够解释自己的选择、在要求范围内做计划、监控进度并利用反馈时，即可进阶；否则保持或调整支持。下一阶段是第 4 级（协商式自主），学生在保留硬性课程标准的同时，共同建构可协商的质量描述语：“一篇优秀的一战论文应该包含什么？我们一起来设计评分量规。”这是能动性的最高体现——它要求学生具备足够深厚的学科知识来评判质量，因此它放在最后。

长期目标并非在所有情境下都永久停留在第 4 级。有些任务天然适合第 1 级（首次学习一项新技能），有些适合第 4 级（独立探究项目）。能动性意味着：**在情境允许时具备自主掌控的能力——并具备判断何时需要更多结构的眼光。**

---

## 已知局限性

1. **同一班级内部及不同决策维度上的准备度存在差异。** 在实践中，有些学生已经准备好进入第 3 级，而另一些学生仍停留在第 1 级。教师可能需要在同一项任务中分层实施能动性水平——部分学生获得结构化选项，另一部分拥有更大自由。这在组织上有一定挑战，但在教育上十分重要。

2. **能动性脚手架需要多个周期才能显现成效。** 仅一次第 2 级的选择体验不会把依赖型学习者变成自主学习者。跨任务的反复练习与反馈至关重要。持续时长与进阶速度取决于具体情境；没有任何固定的周期数或学期/学年时间表能自动确立独立性。

3. **部分课程情境会限制能动性空间。** 在高利害考试与规定内容严格的学科中，可供学生选择的维度可能有限。备考特定考试的学生无法选择去学别的内容。在这些情境下，即使主题固定，依然可以在“过程”与“成果”维度搭建能动性脚手架。
