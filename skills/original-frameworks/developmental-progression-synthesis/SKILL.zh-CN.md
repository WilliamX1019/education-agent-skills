---
# AGENT SKILLS STANDARD FIELDS (v2)
name: developmental-progression-synthesis
description: "将已完成的 KUD 图表综合为发展进阶矩阵及分能力叙事章节。适用于需要从项目整体视角审视知识、理解与表现在各阶段如何发展的场景。"
disable-model-invocation: true
user-invocable: true
effort: high

# EXISTING FIELDS

skill_id: "original-frameworks/developmental-progression-synthesis"
skill_name: "发展进阶综合器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Wiggins & McTighe (2005) — Understanding by Design (backward design; desired results as the basis for programme coherence)"
  - "Vygotsky (1978) — Mind in society (ZPD; band statements describe the upper edge of capability with support)"
  - "Bruner (1960) — The Process of Education (spiral curriculum; concepts revisited with increasing sophistication across developmental stages)"
  - "Hattie & Donoghue (2016) — Learning strategies: a synthesis and conceptual model (surface to deep to transfer as a developmental progression model)"
  - "Biggs & Collis (1982) — Evaluating the Quality of Learning: the SOLO Taxonomy (structural complexity as a developmental progression lever)"
input_schema:
  required:
    - field: "kud_charts"
      type: "string"
      description: "待综合的完整 KUD 图表集。提供项目的所有图表——每张图表应包含 LT 名称、知识类型（T1/T2/T3）以及各阶段的 Know/Understand/Do 内容。将所有图表作为单一输入粘贴。"
    - field: "competency_structure"
      type: "string"
      description: "能力框架——能力名称列表、其下属 LT 成员以及阶段范围（如“A–F 阶段，5–17岁”）。用于按能力分组组织矩阵。"
  optional:
    - field: "output_focus"
      type: "string"
      description: "\"matrix\" 仅生成产出 1，\"chapters\" 仅生成产出 2，或 \"both\"（默认）。使用 \"matrix\" 快速获取项目概览；使用 \"chapters\" 生成项目指南章节内容。"
    - field: "knowledge_type_filter"
      type: "string"
      description: "\"T1\"、\"T2\"、\"T3\" 或 \"all\"（默认）。将综合结果筛选至特定知识类型——例如用 \"T3\" 生成纯倾向性发展视图。"
    - field: "audience"
      type: "string"
      description: "\"teachers\"、\"parents\"、\"researchers\" 或 \"AI-systems\"。调整叙事综合的语域与深度。默认为 \"teachers\"。"
output_schema:
  type: "object"
  fields:
    - field: "developmental_matrix"
      type: "object"
      description: "产出 1——能力 × 阶段矩阵，展示每个单元格的核心发展里程碑。类型 2 与类型 3 单元格在视觉上加以区分。适合作为项目概览页。"
    - field: "competency_chapters"
      type: "object"
      description: "产出 2——分能力叙事章节，展示 K/U/Do 跨阶段的发展。结构化适配作为项目指南章节内容。"
    - field: "design_notes"
      type: "object"
      description: "在综合过程中浮现的标记、缺口与连贯性观察——进阶薄弱点、断层、类型 3 区分度不足以及输入缺口。"
chains_well_with:
  - "kud-chart-author"
  - "learning-target-authoring-guide"
  - "scope-and-sequence-designer"
  - "coherent-rubric-logic-builder"
  - "dispositional-knowledge-assessment-designer"
tags: ["developmental-progression", "KUD", "programme-guide", "scope-and-sequence", "matrix", "competency", "bands", "synthesis", "curriculum-design"]
---

# 发展进阶综合器

## 本技能的功能

本技能接收一套已完成的 KUD 图表，并将其综合为用于项目指南的两份相互关联的成果：

**产出 1——发展进阶矩阵：** 一张“能力 × 阶段”网格，展示每个阶段中每项学习目标（LT）的核心发展里程碑。矩阵为任何读者提供整个项目弧线的单页全景图——学生在每个发展阶段、每项能力上正朝着什么方向努力。类型 2 的表现性 Do 陈述与类型 3 的观察指标在矩阵中在视觉上加以区分，因为它们代表不同性质的证据和不同的评估路径。将它们混同为统一的单元格格式会歪曲项目的真实运作方式。

**产出 2——分能力发展章节：** 针对每项能力生成一段叙事章节，展示该能力下属各 LT 的 Know、Understand 和 Do 如何跨阶段发展。这是项目指南的章节内容——默认面向教师撰写，也可针对家长、研究者或 AI 系统文档进行调整。按“能力”而非按单个 LT 来组织是一项刻意的设计选择：能力具有内在连贯性（例如类型 2/类型 3 的配对放在一起阅读时最有意义），且少数几个能力章节比大量零散的单个 LT 章节更具可读性。

**本技能不是什么：** 它不是教学范围与顺序（scope-and-sequence）工具。`scope-and-sequence-designer` 产出的是课程排期与前置排序文档——何时教什么、按什么顺序教。本技能产出的是发展进阶文档——成长在整个项目弧线上呈现出什么样貌。两者皆为必需；它们回答不同的问题。

**核心设计原则：** 综合必须明确揭示进阶逻辑，而不仅仅是复述阶段陈述。对于每个能力章节，叙事应当点明正在起作用的进阶杠杆（复杂度、精确度、推理、范围、迁移、独立性），并向阅读它的教师或家长解释这条发展弧线的意义。读完一个能力章节的读者不仅应知道学生在每个阶段做什么，还应理解为什么进阶序列是这样编排的。

**矩阵中的类型 2 与类型 3 对比：** 类型 2 的 Do 陈述描述的是任务表现——学生在量规评估的任务中产出什么。类型 3 的 Do 陈述描述的是观察指标——教师随时间推移注意到什么。这两者在矩阵中必须在视觉上清晰区分。统一的单元格格式会暗示存在统一的评估路径，而这对于本框架而言是错误的。

## 循证基础

Wiggins 与 McTighe（2005）提供了支撑本综合结构的逆向设计框架：预期结果——项目末期的发展图景——必须在做出课程决策之前被清晰阐述。本技能将逆向设计中的“预期结果”栏形式化为任何利益相关方都能阅读的项目级矩阵与叙事。Vygotsky（1978）的最近发展区（ZPD）贯穿每一条阶段陈述：矩阵中的每个单元格描述的是学生在该发展阶段**在适当支持下**能做到的事——即 ZPD 的上沿，而非独立表现的底线。Bruner（1960）的螺旋式课程是跨阶段综合的架构原则：相同的能力出现在每一个阶段，以不断提升的成熟度被重温，而非被不同内容替换。综合必须让这种螺旋清晰可见——读者应能沿着矩阵追踪单个 LT 跨阶段的发展，并看到进阶杠杆是如何推进的。Hattie 与 Donoghue（2016）提供了表层-深层-迁移模型作为宏观核查：跨越完整阶段范围的进阶是否推动学生从表层习得经由深层加工走向迁移？在过多阶段停滞于表层水平的阶段陈述无法通过这一核查。Biggs 与 Collis（1982）的 SOLO 分类学提供了结构复杂度视角——从前结构到拓展抽象——这正是叙事综合在相关处应当明确点名的进阶杠杆系统（复杂度）之一。

## 输入模式

设计师必须提供：
- **KUD 图表：** 该项目的完整已完成 KUD 图表集。每张图表应包含 LT 名称、知识类型（类型 1/类型 2/类型 3）以及每个发展阶段的 Know/Understand/Do 内容。将所有图表作为单一输入块粘贴。
- **能力结构：** 能力列表、其下属 LT 成员以及阶段范围。这是矩阵与章节的组织支架。

可选：
- **输出聚焦：** `"matrix"` 仅生成产出 1，`"chapters"` 仅生成产出 2，或 `"both"`（默认）。
- **知识类型筛选：** `"T1"`、`"T2"`、`"T3"` 或 `"all"`（默认）。将综合筛选至单一知识类型。
- **受众：** `"teachers"`（默认）、`"parents"`、`"researchers"` 或 `"AI-systems"`。调整语域。

## 提示词

```
You are synthesising a set of completed KUD charts into two linked programme guide artefacts: a developmental matrix and per-competency narrative chapters. Follow these rules PRECISELY.

═══════════════════════════════════════════════════════════════
TWO-OUTPUT ARCHITECTURE
═══════════════════════════════════════════════════════════════

This skill produces two outputs from the same KUD chart inputs.

**Output 1 — Developmental matrix:** A competency × band grid. One key milestone sentence per cell. Suitable for a programme overview page.

**Output 2 — Per-competency narrative chapters:** One section per competency. Synthesised prose showing K/U/Do development across bands. Suitable for programme guide chapter content.

Both outputs are produced by default unless output_focus specifies otherwise. Read ALL KUD charts in full BEFORE beginning either output.

═══════════════════════════════════════════════════════════════
PRE-SYNTHESIS READING PROTOCOL (mandatory before any output)
═══════════════════════════════════════════════════════════════

Before generating any output, read all provided KUD charts and build an internal map:

1. **Competency membership:** Which LTs belong to which competency.
2. **Knowledge type inventory:** Which LTs are Type 1, Type 2, Type 3, or compound hybrid.
3. **Band coverage:** Which bands each LT covers. Note any bands explicitly marked N/A.
4. **Progression levers in use:** At each band transition, which lever(s) advance the progression — independence, complexity, scope, precision, reasoning, or transfer.
5. **Assessment route per LT:** Whether each LT uses performance Do statements (Type 1/Type 2) or observation indicators (Type 3).
6. **Internal flags:** Any inconsistencies, missing bands, underdifferentiated indicators, or gaps noticed during reading. These become design notes.

Do not begin Output 1 or Output 2 until this mapping is complete.

═══════════════════════════════════════════════════════════════
OUTPUT 1 — DEVELOPMENTAL MATRIX: CONSTRUCTION RULES
═══════════════════════════════════════════════════════════════

**Structure:**
- Rows: one row per LT, grouped by competency (competency name as a spanning header row above the group)
- Columns: the band range provided (e.g. Bands A through F)
- Each cell: one sentence capturing the key developmental milestone at that band for that LT — the most important thing a reader should understand about what the student is working toward at this stage

**Cell content by knowledge type:**

*Type 1 cells:* Draw the sentence from the Know or Understand element — the key concept or knowledge milestone at this band.

*Type 2 cells:* Draw the sentence from the Do statement — what the student performs or produces at this band.

*Type 3 cells:* Draw the sentence from the observation indicators — what the teacher notices at this band. Mark every Type 3 cell with an asterisk (*). Add a legend at the foot of the matrix: * = Observation indicator (multi-informant, not rubric-assessed).

*N/A cells:* Mark N/A. No further content. Do not leave blank.

*Compound hybrid LTs (Type 2 + Type 3 elements):* Produce two sub-rows — one labelled "Performance (T2)" and one labelled "Observation (T3)*". Both rows must appear for every band.

**Whole-matrix check:** After completing the matrix, read each row as a sequence. Does the progression within each row tell a coherent developmental story? Flag in design notes any row where the arc is discontinuous or where a band transition is not clearly justified by a lever advance.

═══════════════════════════════════════════════════════════════
OUTPUT 2 — PER-COMPETENCY CHAPTERS: CONSTRUCTION RULES
═══════════════════════════════════════════════════════════════

**Structure:** One section per competency, in the order provided in competency_structure.

**Each section opens with:**
- The competency name as a heading
- Its definition (one sentence)
- The number of LTs it contains and their knowledge types
- A one-paragraph orientation: what this competency is, why it matters developmentally, and what a reader should be watching for as they read the section

**For each LT within the competency:**

*Type 1 and Type 2 LTs — narrative progression account:*
Write a synthesised narrative of K/U/Do development across bands. Do not reproduce the KUD chart as a table. Describe what develops and why. Name the progression levers explicitly. A reader finishing this narrative should know not just what students do at each band but what is advancing from band to band and why the sequence is designed the way it is.

*Type 3 LTs — dispositional arc account:*
Instead of describing task performance development, describe the developmental arc of the observation indicators. What does this disposition look like in the earliest bands — how it shows up in simple, adult-scaffolded moments? What does it look like in the later bands — how it manifests independently and across diverse contexts? What does that mean for how a teacher or parent recognises growth? This prose is observational, not performative — it describes what is noticed over time, not what is scored on a task.

*Type 2/Type 3 pairs within a competency:*
Where two LTs within a competency are a Type 2/Type 3 pair (analytical capability + enacted disposition), show them together with explicit discussion of the relationship. Name the distinction plainly: the Type 2 LT describes what the student can reason about or produce when assessed; the Type 3 LT describes whether they enact it in real contexts. A student can be strong on Type 2 and weak on Type 3 simultaneously — name this possibility explicitly so teachers and parents understand the assessment distinction and what it means about a student's development.

**Each section closes with:**
- Key prerequisites from other competencies that teachers should be aware of
- The single most important progression observation for this competency: what a teacher should be watching for as the clearest sign of genuine development

═══════════════════════════════════════════════════════════════
AUDIENCE REGISTER
═══════════════════════════════════════════════════════════════

Apply the register consistently across both outputs.

**teachers (default):** Practical, grounded in classroom and observation language. Names what teachers will see students doing and what teachers will notice. Uses assessment terms as givens (rubric, observation indicators, developmental conversation). Does not over-explain the framework.

**parents:** Accessible language, no educational jargon. Focuses on what growth looks like from the outside — what a parent would notice at home or in conversation. Avoids unexplained terms (rubric, LT, KUD chart). Centres the student's visible behaviour and experience.

**researchers:** Includes progression lever terminology explicitly. References the knowledge type classification and names the theoretical warrants (SOLO, ZPD, spiral curriculum). Suitable for a programme evaluation or curriculum audit audience.

**AI-systems:** Structured, precise, complete. Names the assessment route for each LT explicitly. Identifies every progression lever at each band transition by name. Minimises interpretive prose; maximises structured labelling. Optimised for machine parsing of the developmental model.

═══════════════════════════════════════════════════════════════
DESIGN NOTES: CONSTRUCTION RULES
═══════════════════════════════════════════════════════════════

After completing both outputs, produce design notes. These are honest flags for the programme designer — not errors, but signals that further work may be needed.

Produce a note for each of the following where found:

1. **Weak or discontinuous progression arc:** Any LT where the band-to-band progression felt unclear, where the same lever repeated without advancing, or where a band transition introduced new content rather than advancing existing complexity.

2. **Delivery pressure:** Any band where multiple LTs converge in a way that may create pressure — e.g. a band where three LTs simultaneously advance on the reasoning lever for the first time.

3. **Underdifferentiated Type 3 indicators:** Any Type 3 LT where adjacent-band observation indicators are too similar — where Band C and Band D, for example, describe behaviours that would be difficult to distinguish in practice from a single observation event.

4. **Invisible Type 2/Type 3 relationship:** Any competency where the Type 2/Type 3 pair relationship is not clearly visible from the KUD chart inputs — where the analytical LT and the dispositional LT do not obviously complement each other.

5. **Input gaps:** Any LT or band where the KUD chart provided insufficient content to complete the matrix cell or narrative account. Name the specific gap: which LT, which band, which K/U/Do element is missing or underdeveloped.

If none of the above are found, state that explicitly. Do not omit the design notes section.

═══════════════════════════════════════════════════════════════
SELF-CHECK BEFORE RETURNING OUTPUT
═══════════════════════════════════════════════════════════════

Before returning any output, verify:

- [ ] Does the matrix visually distinguish Type 3 cells (asterisk marking on every Type 3 cell, legend at foot)?
- [ ] Does each competency chapter name at least one progression lever explicitly by name?
- [ ] Are Type 2/Type 3 pairs shown together with the T2/T3 distinction explained?
- [ ] Does the chapter narrative synthesise rather than reproduce the KUD chart content?
- [ ] Are design notes honest about gaps and discontinuities — specific, not reassuring?
- [ ] Is the register appropriate and consistent for the specified audience throughout both outputs?
- [ ] Are N/A cells marked N/A in the matrix (not left blank)?
- [ ] Are compound hybrid LTs shown as two labelled sub-rows in the matrix?

═══════════════════════════════════════════════════════════════

Your task is to synthesise:

**KUD charts:** {{kud_charts}}

**Competency structure:** {{competency_structure}}

The following optional parameters may or may not be provided. Use whatever is given; apply defaults for any not provided.

**Output focus:** {{output_focus}} — if "both" or not specified, produce both Output 1 and Output 2.

**Knowledge type filter:** {{knowledge_type_filter}} — if "all" or not specified, include all knowledge types in both outputs.

**Audience:** {{audience}} — if not specified, default to "teachers".

Return your output in this exact format:

## Developmental Progression Synthesis

### Output 1 — Developmental Matrix

[Competency × band matrix. Competency names as spanning header rows. One LT row per LT (or two sub-rows for compound hybrids). One milestone sentence per cell. Type 3 cells marked *. N/A cells marked N/A.]

* = Observation indicator (multi-informant, not rubric-assessed)

### Output 2 — Per-Competency Developmental Guide

#### [Competency Name]

**Competency definition:** [one sentence]
**LTs in this competency:** [LT names with knowledge types]

[Orientation paragraph — what this competency is, why it matters developmentally]

[LT-by-LT narrative — synthesised prose, not KUD chart reproduction. Progression levers named explicitly. Type 2/Type 3 pairs shown together with the distinction explained.]

**Prerequisites from other competencies:** [list, or "None identified"]
**Key progression observation:** [the single most important thing a teacher should watch for]

[Repeat #### section for each competency]

### Design Notes

**1. Progression arc flags:**
[LTs with weak or discontinuous progression, or "None identified"]

**2. Delivery pressure:**
[Bands with convergent demand, or "None identified"]

**3. Underdifferentiated Type 3 indicators:**
[Type 3 LTs where adjacent bands are difficult to distinguish in practice, or "None identified"]

**4. Invisible Type 2/Type 3 relationships:**
[Competencies where the T2/T3 pair relationship is not clear from the inputs, or "None identified"]

**5. Input gaps:**
[Specific LTs, bands, and K/U/Do elements where input was insufficient, or "None identified"]
```

## 示例输出

**场景：** *能力：“分析推理” / LTs：LT-AR1（类型 2——推理质量）与 LT-AR2（类型 3——倾向性） / 仅 A–D 阶段*

**本示例使用的 KUD 图表输入：**

*LT-AR1：证据分析（类型 2）*
- A阶段：Know — 什么是主张以及支持主张意味着什么；Understand — 主张需要支持才可信；Do — 在给定文本中识别主张并说明其是否得到支持
- B阶段：Know — 证据与断言的区别；Understand — 并非所有证据都同样可靠；Do — 比较两条证据并解释哪一条更好地支持主张
- C阶段：Know — 偏见的类型及其如何影响证据质量；Understand — 分析结论取决于所用证据的质量；Do — 评估一组来源并论证哪一个对给定目的最可信
- D阶段：Know — 分析框架如何跨学科运作；Understand — 强有力的分析需要点明证据背后的假设；Do — 分析相互竞争的证据、点明潜在假设并构建有支持的分析立场

*LT-AR2：作为实践的推理（类型 3）*
- A阶段指标：当被给予一条规则或主张时，学生问“为什么？”；当教师提供解释时，学生接纳并建立联结
- B阶段指标：学生在接受主张前会独立质疑；学生能注意到同伴论证何时缺乏证据
- C阶段指标：学生无需提示即可跨学科应用分析性质疑；学生在论证中途能捕捉到自己缺乏支持的断言
- D阶段指标：学生在推理时能说出自己正在使用的分析招式；学生在最终确定立场前会主动寻找反证

---

## 发展进阶综合

### 产出 1——发展进阶矩阵

| LT | A阶段 | B阶段 | C阶段 | D阶段 |
|---|---|---|---|---|
| **分析推理** | | | | |
| LT-AR1：证据分析（类型 2） | 在给定文本中识别主张并判断其是否得到支持。 | 比较两条证据并解释哪一条更好地支持主张。 | 评估一组来源并论证哪一个对给定目的最可信。 | 分析相互竞争的证据、点明潜在假设并构建有支持的立场。 |
| LT-AR2：作为实践的推理（类型 3）* | 当被给予规则时问“为什么？”；接纳并联结他人提供的解释。* | 在接受主张前独立质疑；注意到同伴论证何时缺乏证据。* | 无需提示即可跨学科应用分析性质疑；在论证中途捕捉到自己缺乏支持的断言。* | 在推理时说出自己正在使用的分析招式；在最终确定立场前寻找反证。* |

* = 观察指标（多信息源，非量规评估）

---

### 产出 2——分能力发展指南

#### 分析推理

**能力定义：** 审视证据、评估其质量并构建有充分支持立场的能力。
**该能力下的学习目标：** 2项——LT-AR1（类型 2，推理质量量规）与 LT-AR2（类型 3，多信息源观察）

分析推理是支撑整个项目中所有循证工作的基础能力。它不同于特定学科的内容知识：一名学生可以对某个主题了如指掌，却依然在推理上表现糟糕。本节同时描述了可通过量规任务评估的分析能力（LT-AR1），以及必须跨情境随时间推移观察的推理倾向（LT-AR2）。请将两者结合起来阅读——两个学习目标之间的关系正是核心发展洞察所在。

**LT-AR1：证据分析（类型 2）**

在 A阶段，学生处于分析推理的表层水平：他们能识别一个主张并检查它是否有任何支撑。此处的进阶杠杆是**范围（scope）**——学生在教师支持下处理单一给定文本。到 B阶段，杠杆推进至**复杂度（complexity）**——学生现在必须同时把握两条证据，并比较推理哪一条更有力。这是第一个要求“推理质量”而非单纯“识别”的阶段。C阶段全面引入了**推理（reasoning）**杠杆——学生必须评估一整套来源并论证自己的判断。“论证（justify）”一词在该阶段承载核心分量——它要求学生说出推理过程，而不仅仅是得出结论。在 D阶段，杠杆同时推进至**迁移（transfer）**与**精确度（precision）**——学生跨情境分析相互竞争的证据，揭示嵌入证据中的假设，并构建能经受挑战的立场。从 C阶段到 D阶段的关键发展跃迁，是从评估“显而易见之物”转向点明“隐藏之物”——假设、框架与视角。

**LT-AR2：作为实践的推理（类型 3）**

该 LT 描述的是分析推理是否已成为一种习惯，而不仅仅是一项技能。在 A阶段，教师会注意到一件虽小却真实的事：学生会问“为什么？”。这并非高深的推理——它是推理的前提条件。一个全盘接受主张而不发问的学生，无论在证据任务上表现多好，都无法发展出分析推理。到 B阶段，这种倾向开始独立运作：学生无需教师提示就会质疑主张。这是该 LT 最重要的 B阶段跃迁——从被动反应转向主动质疑。在 C阶段，教师会注意到**迁移**：学生无需提示即可跨学科应用分析性质疑。这就是 Bruner 的螺旋课程的具象化——同一推理能力在新情境中显现。在 D阶段，该倾向已变得具有反思性：学生在推理时能说出自己正在使用的分析招式。这种元认知叙事是该阶段范围内可观察到的最高形态的倾向。

**LT-AR1 与 LT-AR2 的协同：** 这两个 LT 从不同角度描述了同一片发展领地。LT-AR1 描述的是当要求学生进行推理时他们能做什么——在任务中，按量规评分。LT-AR2 描述的是当**没有**要求时他们是否会推理——自发地、跨情境地、长期地。一名学生完全可能在 LT-AR1 上得分很高，而在 LT-AR2 上只展现出有限证据：他们被要求时能分析，但并未养成质疑的习惯。这并非矛盾——而是非常有用的发展信息。它告诉教师下一步的工作在哪里：不是布置更多分析任务，而是创造更多让质疑受到重视和被看见的情境。

**来自其他能力的前置条件：** 在 LT-AR1 C阶段引入来源可信度评估要求之前，学生应已具备信息源素养（理解什么算作一个来源）。

**核心进阶观察：** 分析推理真正发展的最清晰信号，是从“按要求分析”向“习惯性推理”的转变。当一名学生在教师指出之前就开始捕捉到自己缺乏支持的断言时（LT-AR2 的 C阶段），这种倾向便已扎根。

---

### 设计说明

**1. 进阶弧线标记：**
LT-AR1 从 C阶段到 D阶段是本组中最陡峭的杠杆跃迁——从评估证据质量跃升至揭示潜在假设。教师应预见到这一过渡需要关于“假设识别”的明确教学，而不仅仅是多做证据评估任务。这一跨度在教学法上是有意为之，但需要支架支持。

**2. 交付压力：**
在这个包含两项 LT 的能力中未发现趋同交付压力。但需注意，两项 LT 在 D阶段同时达到最高要求，这要求类型 2 评估基础设施与类型 3 观察基础设施在该阶段均已正常运转。

**3. 区分度不足的类型 3 指标：**
LT-AR2 的 C阶段与 D阶段指标间距较近。C阶段：学生在论证中途捕捉到自己缺乏支持的断言。D阶段：学生说出自己正在使用的分析招式并寻找反证。在实践中，单次观察事件中很难区分这些行为。这种区分需要跨多个情境与学科的纵向证据——教师不应凭单一事件就下达 D阶段结论。

**4. 不可见的类型 2/类型 3 关系：**
LT-AR1 与 LT-AR2 配对清晰，其关系在 KUD 图表输入中一目了然。无需标记。

**5. 输入缺口：**
LT-AR1 A阶段：Know 与 Understand 要素虽存在但较为单薄。更充实的 A阶段 KUD 图表将增强该阶段矩阵单元格与章节叙事的力度。B–D 阶段未发现内容缺口。

---

## 已知局限

1. **本技能仅能综合 KUD 图表所提供的内容。** 如果输入的 KUD 图表存在进阶逻辑薄弱、阶段陈述发展不充分或 K/U/Do 要素缺失，综合器会在设计说明中揭示这些问题——但无法替你修复它们。在综合之前，请使用 `kud-chart-author` 技能完善输入。

2. **矩阵需要人工排版才能发布。** 此处生成的 Markdown 表格专为项目指南文档设计，而非直接可印刷的版式。类型 2 与类型 3 单元格之间的视觉区分（星号标记）在最终出版时可能需要调整为颜色编码、字体样式或底纹。

3. **叙事综合不能替代课程交付规划。** 章节部分描述了什么在发展以及为什么——它们阐述了预期弧线。该弧线在实践中能否落地，取决于单元计划、教学序列与形成性评估回路，而这些并非本技能的产出。请使用 `scope-and-sequence-designer` 与 `three-part-lesson-designer` 技能进行交付规划。

4. **相邻阶段的类型 3 观察区分需要纵向证据。** 设计说明标记了相邻阶段类型 3 指标间距较近的情况。这并非设计失败——倾向性的发展进阶本身就是渐进的。它确实要求将观察笔记长期留存并对比，而非基于单次事件的印象下结论。

5. **受众语域全局应用于两项产出。** 受众参数统一适用于矩阵与所有章节部分。如果项目指南的不同部分需要面向不同受众的不同语域（例如面向教师的章节配合面向家长的摘要），请分别以不同受众设置运行本技能两次并手动合并产出。
