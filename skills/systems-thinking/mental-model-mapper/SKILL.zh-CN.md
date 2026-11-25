---
# AGENT SKILLS STANDARD FIELDS (v2)
name: mental-model-mapper
description: "揭示塑造系统的信念、假设、故事与价值观。适用于需要带着审慎与证据检视深层心智模式的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "systems-thinking/mental-model-mapper"
skill_name: "心智模式映射器"
domain: "systems-thinking"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Senge (1990) — The Fifth Discipline (mental models as assumptions shaping action)"
  - "Argyris & Schön (1974) — Theory in Practice (espoused theories and theories-in-use)"
  - "Meadows (2008) — Thinking in Systems (paradigms as deep leverage points)"
  - "Bang, Medin & Atran (2007) — Cultural mosaics and mental models of nature"
input_schema:
  required:
    - field: "system_focus"
      type: "string"
      description: "需要审视的议题、愿景、决策、课程领域、冲突或基于地方的系统"
    - field: "context"
      type: "string"
      description: "该系统存在于何处以及涉及谁"
  optional:
    - field: "visible_evidence"
      type: "string"
      description: "可能揭示心智模式的事件、语言、常规流程、人工制品或决策"
    - field: "stakeholders"
      type: "array"
      description: "心智模式可能存在差异的群体"
    - field: "purpose"
      type: "string"
      description: "目标是反思、重新设计、冲突修复、课程规划还是行动"
output_schema:
  type: "object"
  fields:
    - field: "mental_model_map"
      type: "object"
      description: "当前心智模式与替代心智模式，附带证据与影响"
    - field: "belief_to_structure_links"
      type: "array"
      description: "心智模式如何塑造结构、模式与行动"
    - field: "reflection_questions"
      type: "array"
      description: "供学生/成人使用的反思提示"
    - field: "safer_language"
      type: "array"
      description: "避免指责的更安全表达方式"
chains_well_with:
  - "systems-awareness-iceberg"
  - "aspirational-systems-iceberg"
  - "ladder-of-inference-reflection"
  - "systems-wellbeing-impact-mapper"
  - "culturally-responsive-teaching-designer"
  - "place-based-inquiry-anchor"
teacher_time: "5 分钟"
tags: ["mental-models", "assumptions", "systems-thinking", "compassionate-systems", "culture", "reflection", "beliefs"]
---

# 心智模式映射器（Mental Model Mapper）

## 本技能的功能

揭示塑造系统的信念、假设、故事、价值观、身份认同、恐惧以及对成功的定义。心智模式不仅仅是一种观点；它是一种解读现实的方式，影响着人们注意什么、把什么视为理所当然、围绕什么进行设计，以及认为什么是可能的。

本技能适用于冰山分析之后、愿景冰山构建之中、冲突反思期间、重新设计课程时或审视组织文化时。它帮助学生和成人追问：“我们在假设什么？这里运行着什么故事？那个故事维系着哪些结构？哪一种替代模式可能更具慈悲心、系统性或再生性？”

## 循证依据

Senge 将心智模式界定为塑造组织行为的深层假设。Argyris 与 Schön 区分了“宣称理论”（人们口头上说指导自己的理念）与“使用中理论”（人们实际行动所揭示的信念）。Meadows 将范式与目标确立为系统中的深层杠杆点。Bang、Medin 与 Atran 表明，关于自然的心智模式在不同文化社群中存在差异并塑造着生态推理，这使得本工具在地方本位（place-based）与再生性教育工作中尤为重要。

## 输入规范

必填：
- **系统焦点：** 议题、愿景、冲突、课程领域或基于地方的系统。
- **情境：** 发生在何处以及涉及谁。

可选：
- **可见证据：** 语言、常规流程、人工制品、决策、学生作品、互动或观察记录。
- **利益相关方：** 可能需要映射其心智模式的群体。
- **目的：** 反思、重新设计、冲突修复、课程规划或行动。

## Prompt

```text
You are mapping mental models in a compassionate systems-aware way. Your task is to surface possible beliefs and assumptions shaping a system without accusing people of holding them.

Inputs:
System focus: {{system_focus}}
Context: {{context}}
Visible evidence: {{visible_evidence}}
Stakeholders: {{stakeholders}}
Purpose: {{purpose}}

Rules:
1. Treat every mental model as a hypothesis, not a verdict.
2. Distinguish espoused models from models-in-use:
   - Espoused model: what people say they believe.
   - Model-in-use: what routines, decisions, incentives, or artefacts imply.
3. Include multiple stakeholders. Different groups may hold different models for good reasons.
4. Link each mental model to visible structures or patterns. Do not list abstract beliefs without consequences.
5. Name possible protective functions. Some limiting models may have developed to protect safety, efficiency, identity, status, or belonging.
6. Propose alternative models that are believable, not just virtuous slogans.
7. Use careful language: "A possible model is..." / "The system may be acting as if..." / "One story that might be present..."

Return exactly:

## Mental Model Map: [System Focus]

**Context:** [brief]
**Purpose:** [reflection/redesign/repair/action]
**Stance:** Mental models are hypotheses to test through evidence and dialogue.

### Visible Clues
- **Language clues:** [phrases, labels, metaphors]
- **Routine clues:** [what keeps happening]
- **Artefact clues:** [policies, displays, tools, forms, spaces]
- **Decision clues:** [what gets prioritised]

### Current Mental Models That May Be Operating
For each:
**Model [N]: [short name]**
- **Possible belief/story:** [belief]
- **May be held by:** [stakeholder/s or "the system as a whole"]
- **Evidence suggesting it:** [visible clues]
- **Structures it sustains:** [rules, routines, roles, incentives, artefacts]
- **Patterns it produces:** [repeated behaviours]
- **Protective function:** [what this model might be trying to protect]
- **Risk or harm:** [what it may constrain or damage]
- **Evidence needed before concluding:** [what to ask/observe]

### Aspirational or Alternative Mental Models
For each:
**Alternative model:** [belief/story]
- **Why it may be more compassionate/systemic/regenerative:** [reason]
- **What structures would make it credible:** [routines, roles, artefacts, experiences]
- **First practice that could embody it:** [small action]

### Dialogue Prompts
- [Question that invites reflection without blame]
- [Question that helps students/adults test evidence]
- [Question that opens alternative possibilities]

### Safer Language Guide
Instead of: "People believe..."
Say: "The system may be acting as if..."
Instead of: "Students don't care..."
Say: "One possible story is that students have learned their contribution does not change anything. What evidence would test that?"

Self-check: Do not claim to know what people believe. Do not moralise mental models. Link models to structures and patterns. Include alternative models plus the structures needed to make them real.
```

## 常见误区

1. **读心术式臆断。** 我们是根据证据推断心智模式，而不是宣称某人内心偷偷相信什么。
2. **道德化评判。** 心智模式不是罪过，它们往往是对现实生活条件的适应性反应。
3. **只映射负面模式。** 愿景性/替代性心智模式同样需要映射。
4. **忽视文化背景。** 心智模式具有文化情境性；切勿将单一世界观普世化。
5. **只改口号不改结构。** 一个新故事需要能让它变得可信的常规流程与人工制品。

## 已知局限性

1. **无法确认人们实际上相信什么。** 所有心智模式都是基于可见证据（语言、常规、人工制品、决策）的推论。本技能产出的是假设，而非确认的信念。切勿将输出作为对具名个人的心理评估。
2. **缺乏可见证据时效果下降。** 当系统运作的可观察证据有限时，映射器无法生成可信假设。它需要从具体线索出发。
3. **不会自动揭示权力动态。** 有些心智模式是由掌握机构权力的人强制推行的，而不仅仅是个体持有的。这一区分对行动设计至关重要，必须由教师明确指出。
4. **若无审慎的引导规划，不适合直接作为现场课堂练习。** 当学生在场且可能在心智模式图谱中认出自己或同伴时，使用前必须做好心理安全规划。

## 核查清单

- [ ] 心智模式被明确标注为假设。
- [ ] 每个模式都与可见证据挂钩。
- [ ] 每个模式都与结构和行为模式挂钩。
- [ ] 考虑了保护性功能。
- [ ] 替代模式包含了使之落地的赋能结构。
- [ ] 对话提示足够安全，适合课堂或教职工研讨使用。
