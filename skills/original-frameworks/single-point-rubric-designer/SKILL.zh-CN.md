---
# AGENT SKILLS STANDARD FIELDS (v2)
name: single-point-rubric-designer
description: "设计单点量规，包含单一清晰标准及用于记录具体证据的开放栏位。适用于学生自我评估、同伴反馈、教师形成性反馈或任务前规划。可配合任意学习目标使用，无论是否采用发展阶段系统。"
disable-model-invocation: true
user-invocable: true
effort: low

# EXISTING FIELDS

skill_id: "original-frameworks/single-point-rubric-designer"
skill_name: "单点量规设计器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Fluckiger (2010) — Single point rubric: A tool for responsible student self-assessment"
  - "Sadler (1989) — Formative assessment and the design of instructional systems (evaluative expertise; students must understand quality before they can self-assess)"
  - "Andrade (2000, 2013) — Using rubrics to promote thinking and learning (student self-assessment improves learning when students help generate criteria)"
  - "Boud (1995) — Enhancing Learning Through Self-Assessment (self-assessment as a core academic skill)"
  - "Panadero & Jonsson (2013) — The use of scoring rubrics for formative assessment purposes revisited"
input_schema:
  required:
    - field: "learning_target"
      type: "string"
      description: "该量规所针对的学习目标、目标或评估焦点——“我能够……”陈述、能力描述或任何对学生努力方向的清晰陈述"
    - field: "purpose"
      type: "string"
      description: "谁将使用本量规以及用途——例如“提交前的学生自我评估”、“起草过程中的同伴反馈”、“教师形成性反馈”、“任务前规划以明确质量标准”"
  optional:
    - field: "band"
      type: "string"
      description: "如果使用基于阶段的进阶系统，则为发展阶段（A–F）。默认采用三栏格式，并在提供 student_level 时据此校准语言。仅当明确指定 A 或 B 阶段时才采用两栏格式。"
    - field: "format"
      type: "string"
      description: "“three-column”或“two-column”——如提供则覆盖基于阶段的默认设置"
    - field: "student_generated"
      type: "string"
      description: "若为“yes”，则生成供学生自行撰写标准陈述的提示，而非直接提供标准"
    - field: "task_description"
      type: "string"
      description: "学生将产出或执行的内容——有助于校准标准陈述"
    - field: "student_level"
      type: "string"
      description: "用于校准语言的年龄或年级——未提供阶段时使用"
output_schema:
  type: "object"
  fields:
    - field: "rubric"
      type: "object"
      description: "采用恰当格式且带有精确标准陈述的单点量规"
    - field: "criterion_design_notes"
      type: "object"
      description: "为什么以这种方式撰写该标准；它捕捉了什么以及刻意排除了什么"
    - field: "usage_guidance"
      type: "object"
      description: "如何将该量规用于指定目的；教师或学生如何处理填妥后的栏位"
    - field: "student_generated_prompt"
      type: "object"
      description: "仅当 student_generated 为“yes”时出现——供学生自行撰写标准的提示与支架"
    - field: "known_limitations"
      type: "object"
      description: "仍需专业判断之处"
chains_well_with:
  - "learning-target-authoring-guide"
  - "coherent-rubric-logic-builder"
  - "criterion-referenced-rubric-generator"
  - "dispositional-knowledge-assessment-designer"
  - "kud-chart-author"
teacher_time: "3 分钟"
tags: ["single-point-rubric", "self-assessment", "peer-assessment", "formative-assessment", "criterion", "reflection", "Manning", "Sadler", "Fluckiger"]
---

# 单点量规设计器

## 本技能的功能

本技能设计单点量规（single-point rubric）：一种聚焦于单一标准、留出空间记录具体证据而非采用打分等级的评估工具。与在多个等级上评估多项标准的分析型量规不同，单点量规只呈现一条关于“高质量长什么样”的精确陈述——即**标准（criterion）**——并将两侧栏位留白以填写情境化的具体证据。

本技能无论是否配合发展阶段系统均可使用。任何拥有学习目标与明确用途的教育者都能使用。

本技能生成两种格式：

**三栏格式（默认）：**

| 成长空间 | 标准 | 优势表现 |
|---|---|---|
| 朝向该标准进步的具体证据 | [标准陈述] | 达到或超越该标准的具体证据 |

中间栏包含标准陈述。左右两栏由学生或教师填写具体的、实证性的证据。该格式适用于学生自我评估、同伴反馈以及教师形成性反馈。

**两栏格式（面向低龄学习者、A–B 阶段或明确指定时）：**

| 标准 | 我的反思 |
|---|---|
| [标准陈述] | 描述一个具体的瞬间或例子，展示你目前在这件事上的状态。 |

左栏包含标准，右栏由学生填写。当三栏格式的双向结构在发展上超前于实际需要时，这种格式更为合适。

**学生自主生成模式：** 当指定 `student_generated` 选项时，本技能会生成一份带支架的提示，供学生自行撰写标准陈述。当目标是让学生自己建立对质量的感知而非对照外部定义标准工作时，使用此模式。

核心设计原则是**标准精确度**：单点量规的价值在于填入各栏的证据的具体性——而不在于标准陈述本身。一个只能诱发笼统回答（“我在变好” / “我做得不错”）的标准就是失败的。标准必须足够精确，使学生与教师都能为每一栏找出具体、可指认的证据。

本技能不产出分数或等级。单点量规是形成性工具。填妥后的栏位是开展对话、反思与下一步规划的证据——而非用于终结性打分。

## 循证基础

Fluckiger（2010）专门将单点量规引入作为负责任的学生自我评估工具——指出多级量规详尽地描述了平庸的表现，而单点量规将注意力聚焦于高质量真正长什么样，并为学生自己的证据留出空间。Sadler（1989）确立了任何自我评估工具发挥作用的基础条件：学生必须具备评价专业性（evaluative expertise）——即在能够产出或评估高质量之前先能识别高质量的能力。单点量规预设了这一条件并为其搭建支架：标准就是质量陈述，而两侧栏位要求学生证明自己能在自身作品中识别出质量证据。Andrade（2000, 2013）证明，当学生参与共同生成标准时，学生自我评估对学习成效的提升最为可靠——本技能中的学生生成模式正是这一发现的直接应用。Boud（1995）主张自我评估本身就是一项核心学术技能，而非附加活动：对照标准判断自身作品的能力正是学习者走向独立的关键。单点量规是通往这一能力的低门槛入口。Panadero 与 Jonsson（2013）综述了关于量规的形成性评估文献，发现当学生将量规用于自我调节——而非主要将其当作打分工具——时，量规能显著促进学习。单点格式在结构上天然契合自我调节，因为它要求学生生成证据，而不是勾选一个等级。

## 输入模式

教育者必须提供：
- **学习目标：** “我能够……”陈述、能力描述或评估焦点。*例如：“我能够构建一个包含清晰主张、支持证据以及对不同观点回应的论证” / “当我感到沮丧或不堪重负时，我能够调节自己的反应” / “我能够设计一项控制单一变量的科学探究”*
- **用途：** 谁使用该量规以及用于什么。*例如：“提交前的学生自我评估” / “起草过程中的同伴反馈” / “教师形成性反馈” / “任务前规划以明确质量标准” / “个人反思”*

可选（如有，由上下文引擎注入）：
- **阶段：** 发展阶段（A–F）——A 或 B 阶段触发两栏格式
- **格式：** `"three-column"` 或 `"two-column"`——覆盖基于阶段的默认设置
- **学生生成：** `"yes"`——触发学生自主生成模式
- **任务描述：** 学生将产出的内容——校准标准精确度
- **学生水平：** 年龄或年级——未提供阶段时用于校准语言

## 提示词

```
You are designing a single-point rubric using the principles established by Fluckiger (2010) and Sadler (1989). Follow these rules PRECISELY — they are the quality standard for every rubric produced.

CRITICAL DESIGN PRINCIPLE:
Criterion precision determines evidence quality. A vague criterion produces vague column entries and the rubric fails. Write the criterion first — what does meeting this learning target actually look like as a specific, observable quality? Every other decision follows from that.

---

STEP 1 — FORMAT DECISION:

Apply this logic in order:
- If student_generated is "yes": skip to the STUDENT-GENERATED MODE section below. Do not produce a criterion.
- If format is explicitly provided as "two-column": use two-column format.
- If format is explicitly provided as "three-column": use three-column format.
- If band is A or B: use two-column format.
- If student_level suggests ages 5–9 (e.g. "Year 1", "age 6", "Kindergarten"): use two-column format.
- Default: use three-column format. Calibrate language to student_level if provided; otherwise write for a general secondary audience.

---

STEP 2 — CRITERION WRITING RULES (non-negotiable):

The criterion is a single precise statement of what quality looks like. Apply every rule:

1. **One integrated quality, not a checklist.** Do not list components. "A claim that is supported by evidence and addresses a counterargument" is one integrated quality. "Has a claim, has evidence, has a counterargument" is a checklist — it fails.
2. **Descriptive language, not evaluative language.** Describe what the work or behaviour looks like. Never use: good, excellent, thorough, adequate, appropriate, strong, clear (without specifying what clarity means). Instead: specify the observable feature.
3. **Specific enough to generate concrete evidence.** A student reading this criterion must be able to point to a specific moment, sentence, example, or action that belongs in each column. If they could only write "I did well" or "I need to improve," the criterion is too vague.
4. **Calibrated to the audience.** Neither too simple (patronising) nor too demanding (inaccessible). If band is provided, calibrate to band expectations. If student_level is provided, calibrate language to that level.
5. **Scoped to the learning target.** Does not add requirements the learning target does not contain. Does not drop requirements it does contain.
6. **Single sentence where possible.** Never more than two sentences.

Write the criterion BEFORE constructing the rubric table. State it explicitly and apply the quality check:
- Is it one integrated quality, not a list?
- Is the language descriptive not evaluative?
- Would a student know exactly what kind of evidence to write in each column?
- Is it calibrated to the audience?
- Does it match what the learning target requires, no more and no less?

If it fails any check, rewrite before continuing.

---

STEP 3 — RUBRIC OUTPUT:

**Three-column format:**

Present the rubric as a markdown table. The criterion goes in the centre column header. The outer columns contain the guidance text as a standing instruction for whoever completes the rubric — these are NOT filled in by you.

| Areas for growth | [Criterion statement] | Areas of strength |
|---|---|---|
| Record specific evidence here — moments, examples, or observations that show progress toward the criterion but do not yet fully meet it | [Criterion statement repeated] | Record specific evidence here — moments, examples, or observations that demonstrate or go beyond the criterion |

Do not fill in the evidence columns. They are left blank for the user to complete.

**Two-column format:**

| [Criterion statement] | My reflection |
|---|---|
| [Criterion statement repeated] | Describe a specific moment or example that shows where you are with this right now. |

---

STUDENT-GENERATED MODE:

When student_generated is "yes", do not produce a criterion statement. Instead produce:

**Framing sentence for the student:**
"Think about what doing this really well looks like for you personally. Write one sentence that describes it."

**Scaffolding prompts (provide 2–3):**
- "What would someone watching you be able to see or hear?"
- "What is the difference between doing this well and doing it adequately — what's the specific thing that changes?"
- "If you were helping a friend get better at this, what would you tell them to focus on?"

**Note to teacher:**
The student-generated criterion is personal and specific to this student. Do not correct, standardise, or replace it with your own language. The value is in the student's own articulation of quality — even if it is imperfect. With younger learners (Band A–B or ages 5–9), co-generate the criterion through conversation rather than expecting independent writing.

---

STEP 4 — USAGE GUIDANCE:

Identify which of the following purposes applies, apply the closest match if exact match is not found, and note the adaptation.

- **Student self-assessment before submission:** Student completes both outer columns independently using their own work as evidence. They then decide whether to revise based on what they wrote. The teacher does not complete the rubric — the student's evidence is the formative data.
- **Peer feedback:** The peer completes the columns based on their reading of the work. The owner reads the completed rubric and decides what to act on. The peer does not give a grade or level — only evidence.
- **Teacher formative feedback:** Teacher completes the columns with specific observations from the work. Shares with student as the basis for a feedback conversation, not as a verdict or grade. The evidence in the columns IS the feedback.
- **Pre-task planning:** Student completes only the "areas of strength" column as a planning tool — what specific evidence do I want to be able to put here by the end? The left column remains blank until after the task.
- **Personal reflection:** Student completes the rubric in relation to their own experience, behaviour, or growth over time — not a specific product. Evidence is drawn from memory, observation, or journal entries.

---

STEP 5 — CRITERION DESIGN NOTES:

Explain:
- Why the criterion was written this way
- What it deliberately includes and what it deliberately excludes
- What made it difficult to write precisely, if anything

---

STEP 6 — KNOWN LIMITATIONS:

Apply these standing limitations, plus any specific to the learning target provided:

1. The criterion statement requires judgment to write well — too broad produces vague evidence, too narrow becomes a checklist. If the output criterion feels like either of these, flag it to the user.
2. Single-point rubrics work best when students have already been introduced to the learning target and have some experience with the domain — they are formative tools, not introductory ones.
3. The student-generated version is only as useful as the quality of the student's self-knowledge. With younger learners the teacher may need to co-generate the criterion through conversation.
4. This skill does not produce grades or summative levels. If a summative judgment is needed, use coherent-rubric-logic-builder or criterion-referenced-rubric-generator instead.

---

Your task is to design a single-point rubric for:

**Learning target:** {{learning_target}}
**Purpose:** {{purpose}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Band:** {{band}} — if not provided, use three-column format unless student_level indicates ages 5–9.
**Format:** {{format}} — if provided, overrides band-based default.
**Student generated:** {{student_generated}} — if "yes", produce the student-generated prompt instead of a criterion.
**Task description:** {{task_description}} — if provided, use to calibrate criterion precision.
**Student level:** {{student_level}} — if provided, use to calibrate language.

Return your output in this exact format:

## Single-Point Rubric: [Learning Target Summary]

**Learning target:** [The exact learning target as provided]
**Purpose:** [The stated purpose]
**Format selected:** [Three-column / Two-column / Student-generated] — [brief reason]

### Criterion

[State the criterion here before the table. One sentence, two maximum.]

**Quality check:**
- One integrated quality, not a list: [Yes / No — if No, explain and rewrite]
- Descriptive not evaluative: [Yes / No — if No, explain and rewrite]
- Generates concrete evidence: [Yes / No — if No, explain and rewrite]
- Calibrated to audience: [Yes / brief note]
- Scoped to learning target: [Yes / brief note]

### Rubric

[Insert the appropriate format table here]

### Criterion Design Notes

[Why this criterion; what it includes and excludes; what was difficult to make precise]

### Usage Guidance

[How to use this rubric for the specified purpose — what the student, peer, or teacher does with the completed columns]

### Known Limitations

[Standing limitations plus any specific to this learning target]
```

## 示例输出

### 示例 1

**场景：** *学习目标：“我能够构建一个包含清晰主张、支持证据以及对不同观点回应的论证” / 用途：“提交前的学生自我评估” / 未指定阶段 / 格式：三栏（默认）*

---

## 单点量规：有理有据的论证

**学习目标：** 我能够构建一个包含清晰主张、支持证据以及对不同观点回应的论证
**用途：** 提交前的学生自我评估
**所选格式：** 三栏——未指定阶段，适用默认设置

### 标准

该论证陈述了清晰的立场，用相关证据予以支持，并通过解释为什么该立场依然站得住脚来回应一种对立观点。

**质量检查：**
- 单一整合品质，而非清单：是——三个要素被命名为单一整合论证的组成部分，而非独立的勾选框
- 描述性而非评价性：是——“陈述清晰的立场”、“用相关证据予以支持”、“通过解释来回应一种对立观点”均为可观察特征；未使用评价性形容词
- 能生成具体证据：是——学生可以指出特定句子作为其主张、特定句子或事实作为证据，以及特定段落作为反方论证回应
- 校准至受众：通用中学水平——语言易懂且不失严谨
- 范围契合学习目标：是——标准捕捉了 LT 的全部三个组成部分，且未添加多余要求

### 量规

| 成长空间 | 该论证陈述了清晰的立场，用相关证据予以支持，并通过解释为什么该立场依然站得住脚来回应一种对立观点。 | 优势表现 |
|---|---|---|
| 在此记录具体证据——从你的作品中摘录句子或指出瞬间，说明你正在朝此标准努力但尚未完全达到 | 该论证陈述了清晰的立场，用相关证据予以支持，并通过解释为什么该立场依然站得住脚来回应一种对立观点。 | 在此记录具体证据——从你的作品中摘录句子或指出瞬间，证明已达到或超越该标准 |

### 标准设计说明

该标准将学习目标的全部三个组成部分——主张、证据、反方论证——整合为对论证整体表现的单一描述。拆写成三条独立标准固然更容易，但带有三条标准的单点量规本质上就变成了三维度分析型量规。这种整合是刻意为之的：在真实论证中，三个组成部分并非相互独立。证据唯有相对于主张才起作用；反方论证也唯有相对于所捍卫的立场才有意义。

“通过解释为什么该立场依然站得住脚来回应一种对立观点”比“承认一种不同观点”更加精确。仅仅承认可能只是一句敷衍的话（“有些人不同意”）。该标准要求学生对反方观点做出实质处理——在回应它的同时捍卫自身立场。这正是学习目标的本意，标准准确捕捉了这一点。

该标准排除了不属于本学习目标的写作技巧特征（段落结构、过渡词、词汇）。它也排除了证据本身的质量（强度、来源、相关性）——那是高于本水平 LT 所暗示的更进阶要求。

### 使用指南

**提交前的学生自我评估：**

学生以自己的草稿作为证据独立完成本量规。步骤如下：

1. 仔细阅读标准，确保理解其要求。
2. 带着标准重读自己的草稿。
3. 在右栏（“优势表现”）中，摘录具体句子或指出作品中满足该标准的具体部分。务必具体——“我的第二段”不够具体；“以‘虽然有些人认为……’开头的那句话”才是具体的。
4. 在左栏（“成长空间”）中，摘录显示你正在朝标准努力但尚未完全达到的具体句子或部分。如果你认为自己已完全达到标准，请写下要超越它还需要做什么。
5. 通读两栏。决定：提交前是否需要修改？如果需要，具体修改什么？

教师不填写此量规。学生的证据本身就是形成性数据。如果栏位中出现笼统条目（“我做得还行” / “我需要改进我的论证”），说明学生尚未理解标准——请在学生修改前进行简短对话。

### 已知局限

1. 本标准面向通用中学受众撰写。如果学生尚未接触过反方论证概念，该标准会在右栏产出笼统内容——如空洞的“我回应了另一方”。请在发放本量规前先教授反方论证概念。
2. 本标准不评估证据的质量（证据有多强、是否相关、是否来自可信来源）。如果这些本身也是学习目标，则需另设量规或独立标准。
3. 提交前的自评在学生有时间据此行动时最为有力。在截止前20分钟才发下量规会失去意义。请务必在自评之后预留至少一轮修改周期。
4. 本技能不产出分数或终结性等级。如需终结性判断，请使用 `coherent-rubric-logic-builder` 或 `criterion-referenced-rubric-generator`。

---

### 示例 2

**场景：** *学习目标：“当我感到沮丧或不堪重负时，我能够调节自己的反应” / 用途：个人反思 / student_generated：yes / 未指定阶段*

---

## 单点量规：自我调节反思

**学习目标：** 当我感到沮丧或不堪重负时，我能够调节自己的反应
**用途：** 个人反思
**所选格式：** 学生自主生成——`student_generated` 为 `"yes"`

### 学生自主生成提示

**致学生的引导语：**
想一想，对你个人而言，在感到沮丧或不堪重负时“调节自己的反应”真正做得出色是什么样子。用一句话描述它——不是笼统地说别人怎么做，而是当**你**做得很好时是什么样子。

**支架提示：**
- “如果有人在旁边看着你，他们能看到或听到什么，从而知道你在调节自己的反应——而不仅仅是把情绪压下去或爆发出来？”
- “想一想有一次你很好地处理了沮丧或不堪重负的情绪。当时你具体做了什么？那一刻和没处理好的另一次有什么区别？”
- “对你来说，要能说出‘我调节了自己的反应’，最需要满足的一件事是什么——不仅仅是保持安静，而是你真正管理好了这种感受？”

**致教师说明：**
学生自主生成的标准具有个人化与针对性。切勿将其纠正、标准化或替换为你自己的语言。价值正存在于学生自己对质量的阐述之中——即便它并不完美。对于低龄学习者或觉得该任务困难的学生，请通过对话共同生成标准：口头提出支架提示，并协助学生将回答凝练成一句话。

---

## 已知局限

1. **标准陈述需要专业判断才能写好。** 过于宽泛的标准（“作品展现出高质量思考”）只会产出“我认真思考了”这类无用证据；过于狭窄的标准（“论证恰好包含三条证据”）则会沦为核对清单。本技能产出标准与质量检查——但教育者应同时审阅两者，若标准仍感觉不贴切则予以调整。

2. **单点量规是形成性工具，而非入门工具。** 当学生已经接触过学习目标并在该领域有一定经验时效果最佳——它们是形成性工具，而非导入工具。从未写过议论文的学生无法有意义地对论证标准进行自我评估。请在教学之后而非之前使用本技能。

3. **学生自主生成版本的效用取决于学生自我认知的质量。** 对于低龄学习者（A–B 阶段，5–9岁），独立生成标准在发展上要求过高。通过对话共同生成更为恰当——支架提示正是为此设计，但教师不应期待学生无需支持就能写出完整句子。

4. **本技能不产出分数或终结性等级。** 填妥的量规栏位是用于对话、反思与下一步规划的证据。如果单元或项目末需要终结性判断，请改用 `coherent-rubric-logic-builder` 或 `criterion-referenced-rubric-generator`。

5. **三栏格式预设了学生能同时把握两个方向**——成长的证据与优势的证据。部分学生，尤其是具有完美主义倾向或低自我效能感的学生，会难以诚实填写优势栏，或者把成长栏当作自我惩罚工具。向已知存在自我效能感挑战的学生发放本量规时，请明确说明：“右栏不是自吹自擂，而是事实证据。你的任务就是把它们找出来。”
