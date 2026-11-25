---
# AGENT SKILLS STANDARD FIELDS (v2)
name: regenerative-project-design-orchestrator
description: "呈现项目设计路径选项，并运用逆向设计、PBL、SEEDS、慈悲系统行动或公民/服务学习路径编排再生型项目。"
disable-model-invocation: false
user-invocable: true
effort: high

# EXISTING FIELDS
skill_id: "original-frameworks/regenerative-project-design-orchestrator"
skill_name: "再生型项目设计编排器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Wiggins & McTighe (2005) — Understanding by Design"
  - "Larmer, Mergendoller & Boss (2015) — Gold Standard Project Based Learning"
  - "Manning (2025) — SEEDS regenerative inquiry cycle and regenerative learning design"
  - "Kimmerer (2013) — Braiding Sweetgrass (reciprocity and care)"
  - "Meadows (2008) — Thinking in Systems (leverage, feedback, unintended consequences)"
input_schema:
  required:
    - field: "project_intent"
      type: "string"
      description: "教育者希望学生设计、改进、探究、再生或贡献的事物"
    - field: "learner_stage"
      type: "string"
      description: "年龄范围或年级"
  optional:
    - field: "curriculum_goals"
      type: "string"
      description: "必修内容、标准、能力或评估目标"
    - field: "system_or_context"
      type: "string"
      description: "所涉班级、学校、社区、生态、社会、数字或机构系统"
    - field: "time_available"
      type: "string"
      description: "课程序列、项目周、学季、学期或学年"
    - field: "community_or_adult_partners"
      type: "string"
      description: "应参与其中的成人、社区群体、专家或机构"
    - field: "constraints"
      type: "string"
      description: "评估、安全、许可、资源、权力或实施限制"
    - field: "pathway_choice"
      type: "string"
      description: "可选的已选项目路径。若缺失，在设计完整项目前先呈现选项。"
output_schema:
  type: "object"
  fields:
    - field: "pathway_options"
      type: "array"
      description: "附带契合度、产出与权衡的项目路径菜单"
    - field: "recommended_pathway"
      type: "object"
      description: "附带预设条件与备选方案的最佳匹配路径推荐"
    - field: "orchestrated_skill_chain"
      type: "array"
      description: "按顺序排列的选定技能及交接产出"
    - field: "project_design"
      type: "object"
      description: "选定路径后产出的再生型项目序列"
    - field: "regenerative_quality_gates"
      type: "array"
      description: "针对互惠、管家精神、有界能动性、可行性与非预期后果的检查"
chains_well_with:
  - "backwards-design-unit-planner"
  - "project-brief-designer"
  - "self-determined-project-design-protocol"
  - "seeds-regenerative-inquiry-cycle"
  - "agency-scaffold-generator"
  - "service-learning-project-designer"
  - "systems-awareness-iceberg"
  - "aspirational-systems-iceberg"
  - "agency-circles-for-systems-action"
  - "assessment-validity-checker"
teacher_time: "8 分钟"
tags: ["orchestrator", "composite-framework", "practitioner-framework", "regenerative", "emerging-evidence", "project-design", "PBL", "backwards-design", "SEEDS", "service-learning", "student-agency"]
---

# 再生型项目设计编排器

## 本技能的功能

本编排器旨在设计不仅产出作品或展示、更致力于促进某一系统健康、能力或繁荣的项目。该系统可以是生态的、社会的、文化的、班级的、数字的、机构的或社区的。

它是模型中立的（model-agnostic）：可以路由至逆向设计、项目式学习（PBL）、SEEDS、慈悲系统行动或服务/公民行动。它不应假设 SEEDS 永远是唯一正确的模型，也不应假设传统 PBL 结构总是足够。

## 证据空间与证据强度

这是一个复合型实践者框架。它协调了多项循证教学传统，但具体的路径架构尚未作为完整干预方案接受过直接评估。请将其作为课程设计支架使用，而非声称遵循该序列必定产出特定成效。

### 组件证据

- **逆向设计 / 追求理解的教学设计（UbD）**（强）：Wiggins 与 McTighe（2005）在课程规划中得到广泛研究与使用，在课程对齐与评估效度方面证据基础坚实。
- **项目式学习（PBL）**（中-强）：Larmer、Mergendoller 与 Boss（2015）的黄金标准 PBL 拥有扎实研究基础，表明在良好实施的情境下对投入度、深度学习与技能发展有益。
- **SEEDS 再生探究**（新兴/原创）：Manning（2025）是一个实践者框架。理论上植根于 Kimmerer（2013）与 Meadows（2008），但尚未作为课堂项目接受过独立评估。
- **慈悲系统行动**（新兴）：参见 `systems-awareness-iceberg` 与 `agency-circles-for-systems-action` 的证据评级。向项目设计的复合应用由实践者综合而成。
- **服务 / 公民学习**（中等）：大量文献支持服务学习对公民参与与学习的益处；效果高度取决于质量、框架与社区互惠。

### 综合证据

包括五条命名路径选项、路由逻辑、交接结构与再生质量把关点在内的编排路径，是 Gareth Manning 的原创综合。在经真实教育者测试并基于课堂使用修订之前，应视其为新兴证据。

### 本技能不应声称的内容

切勿声称本框架已作为再生教育项目或通往学生及生态成效提升的保障路径获得验证。切勿使用它绕过教师判断、社区关系、文化礼仪或评估效度要求。

### 适用范围

将本技能用作项目规划与路径选择的设计支架。当教育者需要协助在若干可行项目设计路线间做出选择，并在投入完整项目序列之前理解各自权衡时最为适用。

## 依赖维护

本技能依赖于 `backwards-design-unit-planner`、`project-brief-designer`、`seeds-regenerative-inquiry-cycle`、`systems-awareness-iceberg`、`aspirational-systems-iceberg`、`agency-circles-for-systems-action`、`service-learning-project-designer` 与 `assessment-validity-checker`。每当任一被串联技能变更其证据强度、输出模式、核心质量把关点或主要警示时，请复核本编排器。除非复合工作流本身经过实证检验，否则切勿提高本复合框架的证据等级声明。若某组件技能被弃用或大幅修订，使用前必须先复核本编排路径。

## 路径原则

在设计项目之前先呈现路径选项。教育者未必清楚逆向设计项目、PBL 探究、SEEDS 循环、慈悲系统行动项目与公民/服务项目之间的区别。编排器应让这些选项清晰可见并推荐一条路线。

如果缺少 `pathway_choice`，先返回路径菜单与推荐方案。如果用户明确要求立即生成完整设计，则按推荐路径暂定推进。

## 路径选项

### 1. 逆向设计项目（Backwards Design Project）
适用于学习成果与评估要求已固定的场景。当课程连贯性、学习证据与效度尤为重要时最为合适。

典型链条：`backwards-design-unit-planner` → `project-brief-designer` → `criterion-referenced-rubric-generator` 或 `coherent-rubric-logic-builder` → `assessment-validity-checker`。

### 2. 项目式学习 / 探究项目（Project-Based Learning / Inquiry Project）
适用于项目需要驱动性问题、学生探究、互评/修订、公开成果与真实受众的场景。

典型链条：`project-brief-designer` → `learning-target-authoring-guide` → `formative-assessment-technique-selector` → `assessment-validity-checker`。

### 3. SEEDS 再生探究（SEEDS Regenerative Inquiry）
适用于地方、生态、关爱、管家精神与延续性处于核心的场景。本路径始于感知（Sense），终于持久设计与分享（Design to Last and Share）。

典型链条：`seeds-regenerative-inquiry-cycle` → 可选 `ecological-inquiry-anchor-designer` → `dispositional-knowledge-assessment-designer`。

### 4. 慈悲系统行动项目（Compassionate Systems Action Project）
适用于项目关乎社会、幸福感、文化或机构模式的场景：归属感、求助行为、反馈文化、同伴规范、学校常规或冲突。

典型链条：`systems-awareness-iceberg` 或 `aspirational-systems-iceberg` → `mental-model-mapper` → `agency-circles-for-systems-action` → `agency-scaffold-generator`。

### 5. 公民 / 服务学习项目（Civic / Service Learning Project）
适用于学生围绕社区需求、公共议题、服务、倡导或公民参与开展工作的场景。需要互惠关系与成人/社区伙伴协作。

典型链条：`service-learning-project-designer` → 若属本地议题则接 `place-based-inquiry-anchor` → `agency-scaffold-generator` → `assessment-validity-checker`。

## 提示词

```text
You are a regenerative project design orchestrator. Your job is to help the educator choose a project design pathway before building the full project.

Inputs:
Project intent: {{project_intent}}
Learner stage: {{learner_stage}}
Curriculum goals: {{curriculum_goals}}
System/context: {{system_or_context}}
Time available: {{time_available}}
Community/adult partners: {{community_or_adult_partners}}
Constraints: {{constraints}}
Pathway choice: {{pathway_choice}}

Step 1: Present the five pathway options:
- Backwards Design Project
- Project-Based Learning / Inquiry Project
- SEEDS Regenerative Inquiry
- Compassionate Systems Action Project
- Civic / Service Learning Project

For each option, explain what it is for, what it produces, when to choose it, and when not to choose it.

Step 2: Recommend the best-fit pathway. Explain why and name the assumptions behind the recommendation. Include at least one viable alternative if there is one.

Step 3: If no pathway_choice was provided, ask the educator to choose before producing the full project design. If a full design is explicitly requested, proceed with the recommended pathway and label it provisional.

Step 4: Once a pathway is selected, create an orchestrated skill chain. For every skill, name:
- purpose
- input needed
- output produced
- handoff to next skill
- do-not-proceed-if check

Step 5: Produce the project design with regenerative quality gates. The project should avoid heroic student-fixer narratives and should distinguish student agency from adult/institutional responsibility.

Return:

## Regenerative Project Pathway Options
[Menu with recommendation and choice prompt if needed]

## Recommended Pathway
[Best fit, assumptions, alternatives]

## Orchestrated Skill Chain
[Step-by-step skill sequence and handoffs]

## Regenerative Project Design
[Only if pathway selected or provisional design requested]

## Regenerative Quality Gates
- [ ] Does the project increase capacity for the system to thrive, rather than only reduce harm or produce a display?
- [ ] Are students learning before acting?
- [ ] Is action bounded by real control, influence, or supported collective influence?
- [ ] Are adult/community responsibilities named?
- [ ] Are unintended consequences anticipated?
- [ ] Is there a stewardship, handoff, maintenance, or continuation plan where needed?
- [ ] Does assessment measure the intended learning, not just the attractiveness of the final product?
```

## 常见误区

1. 当教师主要需要与课程对齐的逆向设计时，强行套用 SEEDS。
2. 当项目需要管家精神与长期照料时，强行套用传统 PBL。
3. 把“再生型（regenerative）”当成一种氛围感，而非可检验的设计标准。
4. 在没有授权与支持的情况下要求学生去修补成人或机构的失灵。
5. 因为项目感觉“很真实”就跳过评估效度。
6. 把公开展示的成品误当成真实影响。

## 已知局限

1. **再生意图不等同于再生结果。** 本编排器设计旨在促进系统健康的项目——结果是否真正具有再生性取决于超出本技能控制范围的实施、成人支持、社区条件与持续努力。
2. **无法评估学生准备度。** 本技能不评估学生是否具备所选路径所需的先验知识、技能或情感准备度。这需要教师的诊断性判断或先期评估步骤。
3. **产出的是计划，而非各技能的具体产出。** 每条路径都会串联到其他必须单独运行的离散技能（如 `seeds-regenerative-inquiry-cycle`、`systems-awareness-iceberg`、`project-brief-designer` 等）。编排器提供的是序列与交接逻辑，而非完整的项目设计细节。
4. **再生质量把关点仅具建议性。** 本技能无法强制执行它所识别的质量把关点——教师完全可以带着未通过把关的项目强行推进。把关点需要教师与机构的承诺才能真正发挥作用。
