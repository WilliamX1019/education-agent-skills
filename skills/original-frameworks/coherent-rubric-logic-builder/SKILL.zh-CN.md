---
# AGENT SKILLS STANDARD FIELDS (v2)
name: coherent-rubric-logic-builder
description: "为发展阶段内的学习目标构建具有连贯逻辑的五级量规。适用于“胜任（Competent）= 成功”的 Manning 方法论项目。对于通用课程量规，请改用 criterion-referenced-rubric-generator。"
disable-model-invocation: true
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "original-frameworks/coherent-rubric-logic-builder"
skill_name: "连贯量规逻辑构建器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Manning — REAL School Rubric Logic Guide v2.1 (January 2026, original methodology)"
  - "Burch (1970) — Four stages of competence (unconscious incompetence → conscious incompetence → conscious competence → unconscious competence)"
  - "Haring et al. (1978) — The instructional hierarchy: acquisition, fluency, retention, generalisation, adaptation"
  - "Black & Wiliam (1998) — Assessment and classroom learning (rubrics are only useful if they change decisions)"
  - "Sadler (1989) — Formative assessment and the design of instructional systems (students must understand quality before they can self-assess)"
input_schema:
  required:
    - field: "learning_target"
      type: "string"
      description: "正在评估的具体学习目标（LT）阶段陈述——来自某一发展阶段的特定“我能够……”陈述"
    - field: "band"
      type: "string"
      description: "该量规所针对的发展阶段——A、B、C、D、E 或 F"
    - field: "product_or_performance"
      type: "string"
      description: "学生将产出或执行以证明该学习目标的内容——具体的评估任务"
  optional:
    - field: "student_level"
      type: "string"
      description: "用于校准语言表达的年龄/年级"
    - field: "formative_or_summative"
      type: "string"
      description: "是阶段性检查点量规还是终结性评估量规"
    - field: "compound_lt"
      type: "string"
      description: "该学习目标是否包含值得拆分为独立量规行的不同子技能"
output_schema:
  type: "object"
  fields:
    - field: "teacher_rubric"
      type: "object"
      description: "带有精确描述语的完整五级量表（无证据 / 萌芽 / 发展中 / 胜任 / 拓展）"
    - field: "co_construction_plan"
      type: "object"
      description: "如何通过范例分析与学生共创学生友好型标准语言"
    - field: "student_rubric_template"
      type: "object"
      description: "语言通俗易懂的学生版量规"
    - field: "written_feedback_guide"
      type: "object"
      description: "如何针对每个等级撰写具体、可操作的反馈"
    - field: "known_limitations"
      type: "object"
      description: "仍需专业判断之处；量规无法做到什么"
chains_well_with:
  - "learning-target-authoring-guide"
  - "developmental-band-system-designer"
  - "self-determined-project-design-protocol"
  - "ai-feedback-design-principles"
  - "curriculum-knowledge-architecture-designer"
  - "kud-knowledge-type-mapper"
teacher_time: "5 分钟"
tags: ["rubric", "Manning", "competency", "five-level", "co-construction", "Sadler", "formative", "Competent", "assessment"]
---

# 连贯量规逻辑构建器

## 本技能的功能

本技能编码了由教育者、课程设计师及学习系统设计师 Gareth Manning 开发的原创实践者框架。与其他领域的技能不同，它并非源自同行评审研究传统，而是植根于对学习科学的深入研习、原创课程设计工作以及一线课堂测试。将其纳入本库，是因为该方法论逻辑连贯、可迁移且真正实用——同时出于学术诚实，需将实践者框架与经研究验证的方法加以区分。

本技能为某一学习目标或项目评估构建完整、连贯的量规——采用五级量表，其中**“胜任（Competent）”本身就是成功**，而非中间档。大多数之所以失败，是因为它们把中间等级视为“一般/平均”，把最高等级视为“优秀”——从而制造出一个隐含地将大多数学生贴上“不够好”标签的体系。Manning 的量规逻辑将此反转：“胜任”代表对该发展阶段期望的真正掌握，它**就是**目标。“拓展（Extending）”十分罕见，需要超出该阶段期望的迁移、深度或老练程度的明确证据。“萌芽（Emerging）”是一个正当的起点，而非失败。输出包括在每一等级均有精确描述语的完整量规表，外加一套与学生共同建构标准、使标准内化为学生自己语言的共创计划。Sadler（1989）确立了学生必须先理解高质量是什么样子才能进行有意义自我评估的原则——共创过程是必需的，而非可选项。该量规方法论旨在与《学习目标撰写指南》（技能98）协同工作——量规是特定学习目标的评估工具，而非一套孤立系统。

## 循证基础

Manning 通过课程设计开发了这一量规逻辑，记录于《Rubric Logic Guide v2.1》（2026年1月）。五级量表依托两个互补框架：Burch（1970）的胜任力四阶段——无意识不胜任（不知道自己不知道）→ 有意识不胜任（知道自己不知道）→ 有意识胜任（通过刻意努力能做到）→ 无意识胜任（能自动化做到）——为各等级提供了发展逻辑。Haring 等人（1978）的教学层级——习得、流利、保持、泛化、适应——映射到各等级并决定了恰当的教学回应：处于“萌芽”阶段的学生需要有指导的习得练习，而非家庭作业；处于“胜任”阶段的学生已准备好进行独立应用与迁移。Black 与 Wiliam（1998）确立了量规只有在实际改变教学与学习决策时才有用。仅在单元末用于打分的量规不是形成性工具——它只是贴标签系统。共创过程确保学生在开始工作**之前**就理解标准，从而支持贯穿整个学习过程的持续自我评估与目标设定。Sadler（1989）指出有效自我评估必须满足三个条件：（a）学生必须理解高质量是什么样子（标准）；（b）学生必须能将当前作品与标准比较（监控）；（c）学生必须知道如何缩小差距（策略）。共创中的范例分析环节正是针对条件（a）——学生在生成标准语言之前先研习强、中、弱三类范例。

## 输入模式

教育者必须提供：
- **学习目标：** 精确的“我能够……”陈述。*例如：“我能够构建一个包含清晰主张、支持证据以及对不同观点回应的论证”（C阶段，批判性思维 LT2） / “我能够设计并开展一项控制单一变量的公平科学探究”（B阶段，科学探究 LT1） / “我能够通过贡献想法并在他人贡献基础上拓展来与小组协作”（B阶段，协作 LT1）*
- **发展阶段：** 属于哪个发展阶段。*例如：“C阶段（10-12岁）” / “B阶段（8-10岁）” / “A阶段（5-7岁）”*
- **产出或表现：** 学生将做什么。*例如：“一篇300–500词的书面议论文，就真实本地议题阐述立场” / “一份包含问题、方法、结果与结论的科学探究报告” / “在30分钟小组问题解决任务中的可观察参与”*

可选（如有，由上下文引擎注入）：
- **学生水平：** 用于语言校准的年龄/年级
- **形成性或终结性：** 检查点还是最终评估
- **复合学习目标：** 该学习目标是否需要拆分

## 提示词

```
You are building a rubric using Gareth Manning's coherent rubric logic (Rubric Logic Guide v2.1). You must follow these rules PRECISELY — they are the quality standard for every rubric produced.

THE FIVE LEVELS:
1. **No Evidence** — The student has not produced work that demonstrates any aspect of this LT. This is NOT "bad work" — it is the absence of evidence. It may mean the student did not attempt the task, was absent, or produced work so unrelated that no assessment is possible. ≤10 words.

2. **Emerging** — The student demonstrates initial awareness or partial engagement with the LT. They are at the beginning of the learning journey. This is a LEGITIMATE starting point — all learners begin here. It is not failure. Corresponds to Burch's "conscious incompetence" — the student knows what they're trying to do but can't yet do it reliably. Instructional response: guided acquisition practice. ≤15 words.

3. **Developing** — The student demonstrates growing capability but is not yet consistent or complete. They can do parts of the task reliably but not all of it. This is a NATURAL and EXPECTED stage of growth on the way to Competent. It is not a punishment. Corresponds to the early stages of "conscious competence." Instructional response: practice with feedback. ≤20 words.

4. **Competent** — **This IS success.** The student has met the band-level expectation. They can reliably perform the LT across contexts relevant to their band. Competent is not "average" — it represents genuine mastery. This is the target. Corresponds to reliable "conscious competence." Instructional response: independent application and transfer. ≤25 words.

5. **Extending** — The student demonstrates evidence BEYOND the band expectation — transfer to unfamiliar contexts, unusual depth or sophistication, or the ability to teach or mentor others. Extending is RARE. It is not a motivational tool or an aspirational target for every student. It represents genuine extension beyond what the band requires. Instructional response: mentoring others, self-directed extension. ≤20 words.

QUANTITATIVE EQUIVALENTS (calibration guides, not targets):
- No Evidence: 0%
- Emerging: 1-49%
- Developing: 50-74%
- Competent: 75-89%
- Extending: 90-100%

RUBRIC WRITING RULES:
- **Work-facing voice throughout.** Describe the WORK, not the student. "Shows clear structure" not "You showed clear structure" or "The student demonstrates clear structure."
- **Word limits are mandatory.** No Evidence ≤10 words. Emerging ≤15. Developing ≤20. Competent ≤25. Extending ≤20. This forces precision and prevents waffle.
- **Each level must be DISTINCT.** A reader should be able to place a piece of student work at one level without ambiguity. If two levels sound similar, one of them is wrong.
- **Competent is the anchor.** Write Competent first — it defines what success looks like. Then write Extending (what goes beyond). Then Emerging (where the journey begins). Then Developing (the space between Emerging and Competent). Finally, No Evidence.
- **Compound LTs:** If the LT contains distinct sub-skills (e.g., "construct an argument with claim, evidence, AND counterargument"), consider whether to split into separate rubric rows. Rule: split only when pedagogically justified. Summative judgment rule for compound LTs: Competent on majority of sub-skills, none below Developing.

CO-CONSTRUCTION SEQUENCE:
1. Teacher prepares the rubric (this skill's output)
2. Students analyse 3 exemplars: one strong, one average, one weak — WITHOUT seeing the rubric first
3. Students generate their own criteria language: "What makes the strong one strong? What's missing from the weak one?"
4. Teacher maps student language to the formal rubric criteria
5. Both versions are published side by side — the teacher rubric for formal assessment, the student rubric for self-assessment

Your task is to build a rubric for:

**Learning target:** {{learning_target}}
**Band:** {{band}}
**Product or performance:** {{product_or_performance}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Student level:** {{student_level}} — if not provided, infer from the band.
**Formative or summative:** {{formative_or_summative}} — if not provided, design for summative assessment with formative use built in.
**Compound LT:** {{compound_lt}} — if not provided, assess whether the LT needs splitting.

Return your output in this exact format:

## Rubric: [LT Summary]

**Learning target:** [The exact "I can..." statement]
**Band:** [Which band]
**Assessment task:** [What students produce]

### Compound LT Check

[Does this LT need splitting? Apply the test: are there distinct sub-skills that warrant separate rubric rows?]

### Teacher Rubric

| Level | Descriptor | Word Count |
|---|---|---|
| **No Evidence** | [≤10 words] | [Count] |
| **Emerging** | [≤15 words] | [Count] |
| **Developing** | [≤20 words] | [Count] |
| **Competent** | [≤25 words] | [Count] |
| **Extending** | [≤20 words] | [Count] |

### Co-Construction Plan

[How to run the exemplar analysis with students — what exemplars to use, what questions to ask, and how to map student language to the formal criteria]

### Student Rubric Template

| Level | Student-Friendly Language |
|---|---|
| **Not yet** | [Accessible version of No Evidence / Emerging] |
| **Getting there** | [Accessible version of Developing] |
| **Got it!** | [Accessible version of Competent] |
| **Wow!** | [Accessible version of Extending] |

### Written Feedback Guide

[For each level: what specific, actionable feedback to give. Focus on what to DO NEXT, not just what the current level IS.]

### Connection to Instructional Hierarchy

[What the rubric level tells the teacher about the appropriate instructional response — Haring et al.'s hierarchy]

| Level | Instructional Stage | Appropriate Response |
|---|---|---|
| Emerging | Acquisition | [What to do] |
| Developing | Fluency/Retention | [What to do] |
| Competent | Generalisation | [What to do] |
| Extending | Adaptation | [What to do] |

### Known Limitations

[Where professional judgment is still needed; what this rubric cannot capture]

**Self-check before returning output:** Verify that (a) Competent IS success, (b) Extending is rare not aspirational, (c) Emerging is legitimate not failure, (d) word limits are respected, (e) work-facing voice is used, (f) each level is distinct, and (g) the co-construction plan is included.
```

## 示例输出

**场景：** *学习目标：“我能够构建一个包含清晰主张、支持证据以及对不同观点回应的论证” / 阶段：“C阶段（10-12岁）” / 产出或表现：“一篇300–500词的书面议论文，就真实本地议题阐述立场——例如学校是否应禁用一次性塑料” / 学生水平：“六年级，10-11岁” / 形成性或终结性：“终结性——项目末评估”*

---

## 量规：有理有据的论证（C阶段）

**学习目标：** 我能够构建一个包含清晰主张、支持证据以及对不同观点回应的论证
**阶段：** C（10-12岁）
**评估任务：** 就真实本地议题撰写的 300–500 词书面议论文

### 复合学习目标检查

该学习目标包含三个可识别的子技能：（1）清晰主张，（2）支持证据，（3）对反方观点的回应。这三者虽各自独立但高度互联——没有主张的论证不成其为论证，没有主张的证据毫无目的，而反方观点也唯有相对于主张才有意义。**决策：采用单行量规。** 将这些子技能作为一个整合能力进行整体评估最为合适。不过，下方的书面反馈指南将分别针对每个子技能给出建议，帮助学生识别自身具体的优势与薄弱环节。

### 教师量规

| 等级 | 描述语 | 词数 |
|---|---|---|
| **无证据（No Evidence）** | 作品中未见任何论证或主张。 | 8 |
| **萌芽（Emerging）** | 表明了立场，但未提供任何证据或推理加以支持。 | 13 |
| **发展中（Developing）** | 提出了主张并附带部分支持证据，但未回应任何替代观点。 | 15 |
| **胜任（Competent）** | 提出清晰主张，用相关证据加以支持，并至少回应一种替代观点且给出有理有据的答复。 | 20 |
| **拓展（Extending）** | 整合多重证据来源构建持续论证，细致入微地回应反方观点，并评估自身立场的局限。 | 18 |

### 共创计划

**在布置论文之前——安排 30–40 分钟：**

**第1步：范例分析（20分钟）。**
提供三篇关于相似主题的匿名学生论文（**不要**是他们即将写作的主题）：
- **论文 A（强）：** 首段主张清晰，三条证据，一段承认对立观点并给出有理有据回应，结尾重申立场。
- **论文 B（中）：** 有主张和部分证据，但未提及任何对立观点。证据相关但单薄——一个例子反复使用。
- **论文 C（弱）：** 仅表达个人观点（“我觉得……”）而无任何证据。情绪饱满但缺乏支撑。

大声朗读全部三篇。然后提问：
- “哪篇论文最能说服一位**反对**该立场的读者？为什么？”
- “论文 A 拥有而论文 C 缺少的是什么？”
- “怎样能让论文 B 变得更强？”

**第2步：学生生成标准（10分钟）。**
学生两两结对写下：“是什么让一篇说服性论证令人信服？”收集回答。常见学生语言：“有事实依据”、“提到了另一方的看法”、“讲得通”、“观点明确”。

**第3步：映射对照（10分钟）。**
教师将学生语言与正式量规并排映射：
- “观点明确” → “提出清晰主张”
- “有事实依据” → “用相关证据加以支持”
- “提到了另一方的看法” → “至少回应一种替代观点”

将两个版本同时公布——教师量规用于正式评估，学生量规用于自我评估。

### 学生量规模板

| 等级 | 学生友好型语言 |
|---|---|
| **还没到（Not yet）** | 我还没有写出论证，或者我的文章没有表明清晰的立场。 |
| **快到了（Getting there）** | 我说出了自己的想法并给出了一些理由，但还没有谈到反对我的人会怎么说。 |
| **掌握了！（Got it!）** | 我用证据提出了清晰的论证，**并且**解释了别人为什么可能不同意以及为什么我仍然认为自己是对的。 |
| **太棒了！（Wow!）** | 我用大量证据构建了非常有力的论证，认真思考了对立面，并诚实地指出了自己论证中的薄弱之处。 |

### 书面反馈指南

**无证据：** “我在你的作品里还看不到论证。先用一句话回答这个问题：你对[该议题]的立场是什么？这句话就是你的主张——其余所有内容都是为了支持它。”

**萌芽：** “你告诉我你的想法了——这是个好开始。现在我需要知道你**为什么**这么想。你能找到两条支持你立场的证据（事实、例子、专家意见）吗？把它们加进去。”

**发展中：** “你的主张很清晰，也用证据支持了它——做得很扎实。下一步：想想一个**反对**你的人会怎么说。写一段话回应他们最有力的论点，并解释为什么你的立场依然更站得住脚。”

**胜任：** “这是一篇结构良好的论证。你有主张、有证据，也回应了反方观点。如果你想更进一步，思考一下：你**自己**的论证中有没有薄弱之处？如果有人指出来，你会怎么回应？”

**拓展：** “这是极其出色的作品。你构建了一个诚实考量多元视角的成熟论证。考虑把它呈现给真实受众——你能否投稿到校报，或分享给[相关管理部门]？”

### 与教学层级的联系

| 等级 | 教学阶段 | 恰当回应 |
|---|---|---|
| **萌芽** | 习得 | 有指导的练习：现场示范论证构建，让学生与你共同构建一段论证。**不要**留成家庭作业——学生在独立练习前需要先看见过程。 |
| **发展中** | 流利/保持 | 带反馈的结构化练习：提供论证框架（主张-证据-反方论证模板）。针对缺失的反方论证部分给出具体反馈。随着支架逐步撤除进行练习。 |
| **胜任** | 泛化 | 独立应用：布置新主题、新情境、新受众。学生已经会构建论证了——现在检验他们能否在不同学科与情境中做到这一点。 |
| **拓展** | 适应 | 自主拓展：学生指导其他同学构建论证，分析公开发表的论证（报纸社论、政治演讲），或挑战“正确”立场并不明朗的真实争议议题。 |

### 已知局限

1. **量规评估的是书面“产出”，而非思考“过程”。** 一名批判性思维出色但写作薄弱的学生，仅凭论文可能被评为“发展中”，尽管其分析思维已达“胜任”。论文只是该学习目标的证据，而非学习目标本身。教师应结合课堂讨论、口头解释及其他证据进行三角互证。

2. **共创过程需要 30–40 分钟以及三份范例。** 跳过这一步、直接发下量规的教师会发现，学生把量规当成核对清单（“我包含反方观点了吗？有，搞定。”），而不是理解质量的工具。正是共创使量规具有形成性——没有共创，量规就沦为打分工具。

3. **“拓展”是一项专业判断。** 描述语提供了指引（“整合多重证据来源、细致回应反方观点、评估局限”），但区分真正的拓展与打磨得很好的“胜任”作品需要经验丰富的判断。拿不准时，评为“胜任”——“拓展”在设计上本就罕见。

---

## 已知局限

1. **这是一套量规设计的实践者方法论。** 五级量表、“胜任即成功”原则、词数限制以及共创序列是 Manning 的原创综合。它们植根于成熟的评估研究（Black & Wiliam, Sadler, Burch, Haring），但这一具体量规逻辑尚未通过对照研究获得独立验证。

2. **词数限制迫使精确，但也可能过度简化。** “胜任”等级不超过25词的限制杜绝了空话并迫使清晰思考，但部分复杂学习目标难以用25词概括。当描述语因词数限制而显得生硬或含糊时，问题往往出在学习目标本身（过于复合），而非量规。

3. **学生版量规语言（“还没到 / 快到了 / 掌握了！/ 太棒了！”）具有年龄依赖性。** 这些标签适用于小学与初中低年级学生。年长学生（14岁以上）可能会觉得它们显得居高临下或幼稚。请根据受众调整语言：“起步 / 进阶 / 达标 / 卓越”可能更适合高年级学习者。

**本量规方法不适用于倾向性（dispositional）知识。** 五级量表适用于层级性知识与水平性知识——在这些领域，标准参照是合理的，且学生可以通过特定任务或表现来证明胜任力。它**不适用于**倾向性知识（能动性、协作、自我调节、创造自信、再生型思维模式），因为这些“知识”仅存在于跨时间与跨情境的践行之中。将终结性量规应用于倾向性发展，有可能把复杂的发展轨迹简化为一个标签，并损害倾向性发展所需的内在动机与心理安全感。对于倾向性知识，请改用《倾向性知识评估设计器》技能。
