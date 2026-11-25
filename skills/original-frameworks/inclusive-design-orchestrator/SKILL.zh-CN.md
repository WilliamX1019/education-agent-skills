---
# AGENT SKILLS STANDARD FIELDS (v2)
name: inclusive-design-orchestrator
description: "通过“通用优先”层级协调 UDL 与差异化教学工具：先消除共性障碍，再进行定向差异化，并行提供个体化调适。适用于规划无障碍学习。"
disable-model-invocation: false
user-invocable: true
effort: high

# EXISTING FIELDS

skill_id: "original-frameworks/inclusive-design-orchestrator"
skill_name: "融合设计编排器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Rose & Meyer (2002) — Universal Design for Learning: Theory and Practice"
  - "CAST (2018) — UDL Guidelines version 2.2"
  - "Meyer, Rose & Gordon (2014) — Universal Design for Learning: Theory and Practice"
  - "Ok, Rao, Bryant & McDougall (2017) — UDL systematic review"
  - "Tomlinson (2001) — How to Differentiate Instruction in Mixed-Ability Classrooms"
  - "Gay (2010) — Culturally Responsive Teaching: Theory, Research, and Practice"
  - "Manning (2023-2026) — Orchestration synthesis (practitioner framework)"
input_schema:
  required:
    - field: "lesson_or_unit"
      type: "string"
      description: "教师正在设计或审阅的课程、单元、任务或项目"
    - field: "inclusion_challenge"
      type: "string"
      description: "驱动本次请求的可及性或融合关切：特定学生、已知障碍、规划检查或评估设计关切"
    - field: "context"
      type: "string"
      description: "年级、学科、班级构成、学校环境"
  optional:
    - field: "known_learner_needs"
      type: "string"
      description: "已知的多样性：EAL 学生、学习差异学生、感官或运动需求、IEP/支持计划等"
    - field: "existing_plan"
      type: "string"
      description: "如果教师已有课程或单元计划，请在此提供以供审计"
    - field: "constraints"
      type: "string"
      description: "时间、资源、人员配备、技术或政策限制"
    - field: "pathway_choice"
      type: "string"
      description: "可选的已选路径。若缺失，在协调完整设计前先呈现选项。"
output_schema:
  type: "object"
  fields:
    - field: "pathway_options"
      type: "array"
      description: "附带适用场景说明的融合路径菜单"
    - field: "recommended_pathway"
      type: "object"
      description: "最佳匹配路径，附预设条件与备选方案"
    - field: "coordinated_skill_chain"
      type: "array"
      description: "带有交接说明的离散融合工具序列"
    - field: "inclusive_design_output"
      type: "object"
      description: "消除障碍后的课程、单元或评估设计"
    - field: "specialist_referral_flags"
      type: "array"
      description: "转介专科评估比设计修改更合适的情况"
    - field: "stop_checks"
      type: "array"
      description: "推进设计修改前的检查项"
chains_well_with:
  - "udl-lesson-auditor"
  - "udl-options-designer"
  - "udl-barrier-anticipator"
  - "differentiation-adapter"
  - "assessment-design-orchestrator"
  - "language-demand-analyser"
  - "scaffolded-task-modifier"
teacher_time: "10–15 分钟"
tags: ["orchestrator", "composite-framework", "practitioner-framework", "emerging-evidence", "inclusive-design", "udl", "differentiation", "accessibility", "equity", "barrier-removal", "universal-design"]
---

# 融合设计编排器

## 本技能的功能

当教师正在规划一节课、一个单元或一个项目，并希望确保其对更多学习者可及时，协调融合设计与通用学习设计（UDL）工具。本编排器基于教师具体的融合挑战，在 UDL 工具、差异化教学与语言可及性方法之间进行路由，并采用**通用优先（universal-first）**规划：主动减少共性障碍，同时**并行**提供现有、必需或紧急的个体支持。任何学习者都不必等待其他层级耗尽后才获得支持。

当融合挑战尚未明确归结为单一特定工具时使用本技能。如果你已经确定需要一份 UDL 课程审计，请直接使用 `udl-lesson-auditor`。当融合干预的类型尚不确定时，使用本编排器。

本编排器协调设计工具，但不能替代专科评估、临床知识或教育心理学。当需要这些专业力量时，它会明确指出。

## 循证基础

各条路径汲取自通用学习设计（Rose & Meyer, 2002; CAST, 2018; Meyer, Rose & Gordon, 2014; Ok, Rao, Bryant & McDougall, 2017 系统综述）、差异化教学（Tomlinson, 2001）以及文化回应教学（Gay, 2010）。核心组织原则是从一开始就将可及性嵌入设计之中。下方的三个层级是本实践者框架的规划结构，而非要求延迟个体支持的经研究验证的门槛。

## 证据空间与证据强度

这是一个复合型实践者框架。它协调了多项循证融合传统，但具体的路径架构——包括路由逻辑、交接结构、通用优先层级执行以及专科转介标记——尚未作为完整干预方案接受过直接评估。请将其作为融合规划支架使用，而非声称遵循该序列必定产出特定的学习或幸福感成效。

### 组件证据

- **通用学习设计（UDL）**（中等）：Ok、Rao、Bryant 与 McDougall（2017）的系统综述在18项研究中发现了积极效应；大多数研究规模较小且为非实验性研究。CAST（2018）指南具有坚实的理论基础与广泛的实践采纳度。
- **差异化教学**（中等）：Tomlinson（2001）属于奠基性实践文献；关于差异化教学效应量的研究结果呈混合态势，部分原因在于“差异化”涵盖了范围极广的实践。针对性教学调整的证据强于全班系统性差异化。
- **文化回应教学**（中等）：Gay（2010）及相关研究显示在投入度与文化认同方面有益处；专门针对学业成果的对照研究较少。
- **UDL 障碍预判**（新兴）：UDL 障碍分析工具由实践者开发；在教学前主动识别障碍的做法在理论上基础充分，但针对障碍预判过程本身的直接研究证据有限。

### 综合证据

包括四条命名路径、通用优先层级执行、专科转介标记以及对象征性融合（tokenistic inclusion）警示在内的编排路径，是 Gareth Manning 的原创综合。在经真实教育者测试并基于课堂使用修订之前，应视其为新兴证据。

### 本技能不应声称的内容

切勿声称遵循本编排器就能“确保融合”。融合是关系性的、文化性的且持续进行的过程——它不是一劳永逸达到的设计状态。切勿使用本技能替代专科评估或临床知识。切勿将消除障碍核对清单作为真正融合的证据。如果增加视觉图或提供选择并未解决实际识别出的障碍，切勿声称其构成了 UDL。

### 适用范围

将本技能用作融合规划的设计支架。当教师需要协助在多种融合方法中做出选择，并在投入设计之前了解每种路径的要求时最为适用。它是一个规划工具，而非认证。

## 依赖维护

本技能依赖于 `udl-barrier-anticipator`、`udl-lesson-auditor`、`udl-options-designer`、`differentiation-adapter`、`language-demand-analyser` 与 `scaffolded-task-modifier`。每当任一被串联技能变更其证据强度、输出模式、核心质量把关点或主要警示时，请复核本编排器。除非复合工作流本身经过实证检验，否则切勿提高本复合框架的证据等级声明。若某组件技能被弃用或大幅修订，使用前必须先复核本编排路径。

## 通用优先层级

本编排器使用三个规划层级。从考量共性障碍开始，同时立即尊重现有支持计划与紧急可及性需求；这些层级并非获得支持的先决门槛：

1. **通用设计（Universal Design）**——在教学开始前为所有学习者减少障碍。益处：人人都能获得可及性；没有学生被单独标出；设计精力集中在能帮助最多人的地方。
2. **定向差异化（Targeted Differentiation）**——为有明确需求的单个学生或小组调适特定任务、资源或模态。用于共享设计尚未满足的已识别需求，包括在推进通用改进的同时。
3. **个体化调适（Individualised Accommodation）**——为拥有支持计划、IEP 或临床需求的特定学生进行调整。尊重现有计划与必需的便利条件；与设计工作**并行**，协同授权人员处理紧急可及性需求。切勿要求前序层级“失败”或等待新文档才提供恰当支持。

这一层级不是对学生价值的排序。它是减少共性障碍的规划优先级，绝非扣留个体支持的关卡。

## 路径原则

在协调工具之前先呈现路径选项。如果未提供 `pathway_choice`，先返回**路径选项菜单**，附带推荐方案并提问：“我应展开哪条路径？”如果用户明确要求完整设计，则按推荐路径推进并标注为“暂定（provisional）”。

## 路径选项

### 1. 主动障碍消除（Proactive Barrier Removal）
适用于在教学开始前规划新课程或新单元，并希望从一开始就为可及性而设计的场景。产出：内置 UDL 改进的降障课程设计。

典型链条：`udl-barrier-anticipator` → `udl-options-designer`。

最适用于：教授新单元之前、面对已知学习者多样性的班级、重新设计先前排斥了部分学习者的课程。

切勿使用本路径：针对一小时后就要上的课——请改用“现有计划审计”或“定向差异化”。

### 2. 现有计划审计（Existing Plan Audit）
适用于课程或单元已经存在，且教师希望在将其用于新班级或更多元群体前识别并消除可及性障碍的场景。产出：带批注的障碍审计及针对性修改建议。

典型链条：`udl-lesson-auditor` → 通过 `udl-options-designer` 或 `differentiation-adapter` 进行具体修改。

最适用于：审阅现有资源、为新学年组改编课程、核查从其他教师处继承的单元计划。

切勿使用本路径：仅仅作为例行合规检查。唯有对识别出的障碍采取行动，审计才有价值。

### 3. 定向差异化（Targeted Differentiation）
适用于特定学生或小组需要以调适后的方式接触对大多数学习者有效的任务的场景。产出：调适后的任务、修改后的资源或支架化替代方案。

典型链条：`differentiation-adapter` → 可选针对 EAL 学生的 `language-demand-analyser` 或 `scaffolded-task-modifier`。

最适用于：回应已识别的个体需求、落实 IEP 的部分内容、为 EAL 学生搭建支架，或为缺勤返校的学生进行调整。

检查某项通用修改是否也能帮助其他人，同时不延误现有或紧急的定向支持。

### 4. 评估可及性（Assessment Accessibility）
适用于专门关切评估形式是否制造了与所评估内容无关的障碍——即掩盖了学生真实所知障碍的场景。产出：在恰当处提供形式替代方案的降障评估设计。

典型链条：聚焦评估的 `udl-barrier-anticipator` → 生成评估形式替代方案的 `udl-options-designer` → 连接至 `assessment-design-orchestrator`。

最适用于：设计测验、项目、展示或量规，而形式要求可能掩盖学生理解时；核查现有评估是否公平。

切勿使用本路径：作为降低期望的理由。目标是消除与所评估学习内容无关的形式障碍——而不是让任务变简单。

## 提示词

```text
You are an inclusive design orchestrator. Your first responsibility is to make pathway options visible and prioritise universal barrier reduction while providing existing, required or urgent targeted/individual support in parallel. Universal-first is a planning priority, never a wait-for-failure rule.

Inputs:
Lesson or unit: {{lesson_or_unit}}
Inclusion challenge: {{inclusion_challenge}}
Context: {{context}}
Known learner needs: {{known_learner_needs}}
Existing plan: {{existing_plan}}
Constraints: {{constraints}}
Pathway choice: {{pathway_choice}}

Step 1: First preserve existing support plans, access arrangements and learning goals, and flag urgent access needs for prompt authorised action. If pathway_choice is not provided, present all four pathway options with when-to-use guidance. State what each produces and when not to use it.

Step 2: Recommend the best-fit pathway. Explain which tier of the universal-first hierarchy applies: Is this a universal design decision, a targeted differentiation, or an individualised accommodation? Name your assumptions.

Step 3: If no pathway_choice is provided, ask the teacher to choose before producing the full design. If the user explicitly requested a full design, proceed with the recommended pathway and label it provisional.

Step 4: Once a pathway is selected, coordinate the relevant skills in sequence. For each step, specify:
- Which skill/tool to use
- What barrier or need it addresses
- What the teacher inputs
- What the tool produces
- Handoff to the next step
- Do-not-proceed-if check

Step 5: Apply the universal-first hierarchy explicitly. Identify shared barrier reductions and any remaining targeted needs. Honour existing/required support and urgent access arrangements in parallel; never wait for universal or targeted options to fail before addressing these.

Step 6: Apply specialist referral check. Flag clearly when a need exceeds what inclusive design can address:
- If a student requires educational psychology assessment to understand their learning profile, flag this.
- If a student's needs include speech-language, occupational therapy, or clinical mental health support, flag this.
- If a barrier persists despite multiple design modifications and the student is not making progress, flag this.
A referral flag identifies a need for specialist collaboration. It does not suspend ordinary inclusion or existing support; stop only the decision requiring specialist authority and continue safe design work.

Step 7: Apply tokenism check. For each proposed modification:
- Does this modification address an actual identified barrier, or is it a generic addition ("add a visual") that may not help anyone specifically?
- Is there evidence — from student work, teacher observation, or the barrier analysis — that this modification addresses a real need?

Return:

## Inclusive Design Pathway Options
[Menu with recommendation and choice prompt if no pathway is selected]

## Recommended Pathway and Hierarchy Tier
[Best fit, which tier applies, assumptions, and one viable alternative]

## Coordinated Skill Chain: [Pathway Name]
[Only if a pathway is selected or a provisional design is explicitly requested]

For each step:
**Step [N]: [Tool Name]**
- **Barrier addressed:** [what access issue this tackles]
- **Input:** [what the teacher provides]
- **Output:** [what the tool produces]
- **Handoff:** [what passes to the next step]
- **Do not proceed if:** [quality gate]

## Inclusive Design Output
[Barrier-reduced lesson, unit, or assessment design]

## Universal-First Hierarchy Check
- [ ] Universal barrier reductions prioritised, alongside existing or urgent access support?
- [ ] Targeted needs addressed without waiting for shared redesign?
- [ ] Existing/required accommodations retained and urgent access needs addressed with authorised staff?
- [ ] No student has been singled out unnecessarily by the design modifications?

## Specialist Referral Flags
[List any situations where specialist referral is more appropriate than design modification]

## Stop / Do Not Proceed If
- [ ] A proposed decision requires clinical, psychological or specialist authority: pause that decision and seek the appropriate human input; continue ordinary inclusion
- [ ] Modifications are being added as compliance gestures without identifying actual barriers
- [ ] An existing, required or urgent individual support is being delayed pending earlier tiers
- [ ] The teacher has not yet examined what barriers exist — barrier analysis must precede barrier removal

Self-check: Am I helping the teacher think about barriers and access, or am I generating a compliance checklist? Is the universal-first hierarchy being followed? Am I being honest about the limits of design-based inclusion? Have I flagged specialist referral needs clearly?
```

## 常见路径

### 新单元的主动障碍消除
1. UDL 障碍预判器——跨越表征、行动/表达与投入三个维度识别障碍。
2. UDL 选项设计器——生成降障修改方案。
3. 对照通用优先层级进行复核。
4. 标记任何需要专科转介的需求。

### 审计并调适现有课程
1. UDL 课程审计器——对现有计划进行系统审计。
2. 按影响程度排定障碍优先级；并行保留现有便利条件并处理紧急需求。
3. 针对高影响障碍使用 UDL 选项设计器。
4. 针对剩余个体需求使用差异化适配器。
5. 标记专科转介需求。

### 融合设计中的 EAL 支架搭建
1. 语言需求分析器——识别任务中的语言需求。
2. 支架式任务修改器——生成支架化替代方案。
3. 确认通用设计原则得以应用（支架面向所有人开放，而不仅限于被贴标签的学生）。

## 常见误区

1. **象征性添加。** 没有识别具体障碍就增加一张视觉图、一个选项或一个支架，这并非 UDL。修改必须连接到真实障碍。
2. **直接跳到个体化调适。** 应考量共享设计机会，但切勿在重新设计期间延迟现有、必需或紧急的个体支持。根据实际障碍与学习者需求选择支持。
3. **把合规当成融合。** 填完一份障碍审计清单并不意味着学生感到被接纳。真正的融合是关系性的、文化性的且持续进行的。
4. **降低期望而非消除障碍。** 融合设计的目标是确保学生能够展示其真实的知识与技能。消除形式障碍不等同于降低挑战性。
5. **忽视专科转介信号。** 当学生的需求持续超出设计修改所能解决的范围时，继续反复修改设计而不寻求专科支持并不是在真正服务该学生。
6. **假设通用设计永远是唯一正确的层级。** 有时定向修改才是恰当回应。层级指导决策，但并不禁止在合适时采用定向方法。

## 已知局限

1. **融合设计是真正融合的必要条件，但非充分条件。** 融合还关乎关系、归属感、文化以及学生在班级社群中的位置。没有任何设计技能能凭空创造这些。本编排器减少结构性障碍；它无法确保学生感到受欢迎、受尊重或真正成为社群的一员。
2. **无法替代专科知识。** 本编排器协调设计工具，但无法替代教育心理学评估、言语治疗、作业治疗或临床心理健康支持。基于设计的融合存在真实边界，本技能必须诚实地指明这些边界。
3. **“通用”设计永远无法做到绝对通用。** UDL 为最大多数人减少了障碍，但即便在卓越的通用设计之后，部分需求仍需要额外的定向或个体化支持。UDL 框架本身也承认这一点。
4. **结构化支持与高期望之间存在持续的张力。** 支架过多会降低挑战性并传递低期望；支架过少则会造成排斥。本编排器帮助教师驾驭这一张力，而非自动消除它。教师的专业判断是必需的。
5. **障碍分析取决于对学生的了解。** 当教师对学习者有直接了解时，本编排器最为有用。在不了解班级的情况下进行泛泛的障碍分析，只会产出可能并未解决真实障碍的泛泛修改建议。
