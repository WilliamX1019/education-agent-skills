---
# AGENT SKILLS STANDARD FIELDS (v2)
name: assessment-design-orchestrator
description: "在五种评估路径——形成性评估、量规/标准、真实性/表现性评估、同伴/自我评估与诊断性评估——之间进行路由，并附带效度与公平性检查。适用于教师需要协助选择如何进行评估时。"
disable-model-invocation: false
user-invocable: true
effort: high

# EXISTING FIELDS

skill_id: "original-frameworks/assessment-design-orchestrator"
skill_name: "评估设计编排器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Black & Wiliam (1998) — Inside the Black Box (formative assessment, effect size ~0.66)"
  - "Wiliam (2011) — Embedded Formative Assessment"
  - "Wiggins (1998) — Educative Assessment (authentic assessment design)"
  - "Sadler (1989) — Formative assessment and the design of instructional systems"
  - "Hattie & Timperley (2007) — The power of feedback"
  - "Messick (1989) — Validity (unified validity framework)"
  - "Topping (2009) — Peer assessment (meta-analysis)"
  - "Zimmerman (2002) — Self-regulated learning and self-assessment"
  - "Manning (2023-2026) — REAL School rubric logic and competency assessment (practitioner framework)"
input_schema:
  required:
    - field: "learning_goal"
      type: "string"
      description: "期望学生知道、理解或能够做到的内容"
    - field: "context"
      type: "string"
      description: "学科、年级、单元或项目情境"
    - field: "assessment_purpose"
      type: "string"
      description: "评估目的：指导教学、评分、认证、提供反馈、培养学生能力或了解先验知识"
  optional:
    - field: "learner_variability"
      type: "string"
      description: "已知的学习者多样性：EAL 学生、学习差异学生、混合先验知识等"
    - field: "time_in_unit"
      type: "string"
      description: "单元初期、中期或末期——或持续进行"
    - field: "constraints"
      type: "string"
      description: "时间、核准要求、报告格式、学校政策或技术条件限制"
    - field: "pathway_choice"
      type: "string"
      description: "可选的已选路径。若缺失，在设计完整评估前先呈现选项。"
output_schema:
  type: "object"
  fields:
    - field: "pathway_options"
      type: "array"
      description: "附带适用场景说明的合适评估路径菜单"
    - field: "recommended_pathway"
      type: "object"
      description: "最佳匹配路径，附预设条件与备选方案"
    - field: "assessment_design"
      type: "object"
      description: "选定路径后的完整评估设计"
    - field: "validity_check"
      type: "array"
      description: "该评估是否测量了其声称要测量的内容？"
    - field: "equity_check"
      type: "array"
      description: "该评估形式是否制造了与所评估学习内容无关的障碍？"
    - field: "stop_checks"
      type: "array"
      description: "最终确定评估设计前的“若未满足则切勿推进”把关点"
chains_well_with:
  - "formative-assessment-technique-selector"
  - "assessment-validity-checker"
  - "gap-analysis-from-student-work"
  - "differentiation-adapter"
  - "self-regulation-scaffold-generator"
  - "inclusive-design-orchestrator"
  - "udl-barrier-anticipator"
teacher_time: "10–15 分钟"
tags: ["orchestrator", "composite-framework", "practitioner-framework", "emerging-evidence", "assessment", "formative-assessment", "rubric", "authentic-assessment", "peer-assessment", "diagnostic", "validity", "equity"]
---

# 评估设计编排器

## 本技能的功能

帮助教师应对“我该如何评估这一学习内容？”这一问题——其答案高度取决于评估什么、为什么评估以及在何种情境下评估。本编排器呈现五种评估设计路径，基于教师处境推荐最契合的方案，并协调所选路径对应的组件技能。

当尚未决定评估方式时使用本技能。如果你已经明确需要一份量规，请直接使用 `criterion-referenced-rubric-generator`。当评估类型本身尚不确定时，使用本编排器。

在学习目标清晰之前**切勿**使用本编排器。评估设计始于学习本身，而非测评工具。

## 循证基础

五条路径汲取自成熟完善的评估研究传统。形成性评估：Black 与 Wiliam（1998），效应量约 0.66，以及 Wiliam（2011）。真实性评估：Wiggins（1998）与 Sadler（1989）关于标准与反馈的研究。效度：Messick（1989）统一效度框架——“评估必须测量其声称测量的内容”这一原则贯穿每条路径。同伴与自我评估：Topping（2009）元分析与 Zimmerman（2002）关于自我调节学习的研究。反馈：Hattie 与 Timperley（2007）。

## 证据空间与证据强度

这是一个复合型实践者框架。它协调了多项循证评估传统，但具体的路径架构——包括路由逻辑、交接结构以及整合的效度与公平性检查——尚未作为完整干预方案接受过直接评估。请将其作为评估设计支架使用，而非声称遵循该序列必定产出特定成效。

### 组件证据

- **形成性评估设计**（强）：Black 与 Wiliam（1998）元分析是教育研究中被引用最广泛的文献之一。Wiliam（2011）提供了实用的课堂应用。效应量得到了充分复现。
- **量规与标准设计**（中等）：标准参照量规设计与标准共创在 Sadler（1989）中有理论支撑并获得实践验证；专门针对量规设计过程的对照研究较少。
- **真实性/表现性评估**（中等）：Wiggins（1998）提供了坚实的理论基础；真实性评估研究显示出投入度收益，但对学习成果的效应量比形成性评估更为混合。
- **同伴与自我评估**（中等）：Topping（2009）元分析显示同伴评估效应量约为 0.55；Zimmerman（2002）确立了自我调节学习基础。成效显著取决于是否训练学生恰当使用标准。
- **诊断性/前测评估**（中等）：得到形成性评估研究与先验知识激活学习科学文献的支持；针对前测设计本身的直接研究有限。

### 综合证据

包括五条命名路径、路由逻辑、每一步整合的效度检查以及公平性审计在内的编排路径，是 Gareth Manning 结合 REAL School 量规逻辑与能力评估实践所做的原创综合。在经真实教育者测试并基于课堂使用修订之前，应视其为新兴证据。

### 本技能不应声称的内容

切勿声称遵循本编排器就能产出有效评估。效度是评估在特定情境下**使用**的属性，而非单纯设计过程的属性（Messick, 1989）。切勿使用本技能绕过教师对特定学生适宜性的专业判断。切勿声称该序列能确保公平评估——公平性检查能标记潜在障碍，但无法保证无障碍。

### 适用范围

将本技能用作评估规划的设计支架。当教师需要协助在多种评估方法中做出选择，并在投入设计之前了解每种路径的要求时最为适用。

## 依赖维护

本技能依赖于 `formative-assessment-technique-selector`、`assessment-validity-checker`、`gap-analysis-from-student-work`、`differentiation-adapter` 与 `self-regulation-scaffold-generator`。每当任一被串联技能变更其证据强度、输出模式、核心质量把关点或主要警示时，请复核本编排器。除非复合工作流本身经过实证检验，否则切勿提高本复合框架的证据等级声明。若某组件技能被弃用或大幅修订，使用前必须先复核本编排路径。

## 路径原则

在确定设计前先呈现路径选项。不要假设教师知道哪条路径合适。如果未提供 `pathway_choice`，先返回**路径选项菜单**，附带推荐方案并提问：“我应将哪条路径展开为完整的评估设计？”如果用户明确要求立即生成完整设计，则按推荐路径推进并标注为“暂定（provisional）”。

## 路径选项

### 1. 形成性评估设计
适用于目标是在教学过程中收集学习证据以调整教学的场景。该评估不计分；它指导接下来的教学行动。产出：形成性检查提示、出口卡设计、观察规程或提问序列。

典型链条：`formative-assessment-technique-selector` → `gap-analysis-from-student-work` → 反馈设计。

最适用于：单元中期、推进前检查理解、规划差异化下一步教学。

切勿使用本路径：当需要分数或认证时，或唯一目的是向家长汇报而非指导教学时。

### 2. 量规与标准设计
适用于教师需要在学生开始工作前界定“高质量”长什么样的场景。产出：量规、共创规程、范例筛选计划或成功标准文档。

典型链条：`criterion-referenced-rubric-generator` → `assessment-validity-checker` → 范例分析规划。

最适用于：启动大型项目或单元、设计同伴互评规程、准备终结性评估，或支持学生对照标准开展自我评估。

切勿使用本路径：在没有范例或学生作品样本可供校准的情况下。未经校准的量规只会制造虚假精确。

### 3. 真实性/表现性评估设计
适用于评估应映射知识与技能在真实世界中的应用的场景。产出：项目简报、档案袋设计、展示计划或汇报规程。

典型链条：项目简报设计 → `assessment-validity-checker` → 针对形式障碍的公平性检查。

最适用于：PBL 项目式学习情境、能力导向评估、过程与产出同等重要的单元末展示。

切勿使用本路径：当真实性形式缺乏充分理由时。“真实性”并非天生更优——部分学习目标通过精心设计的测试反而能得到最佳评估。

### 4. 同伴与自我评估设计
适用于培养学生自身评估能力即学习目标之一的场景。产出：同伴互评规程、自我评估支架、校准活动设计。

典型链条：标准设计 → 同伴反馈规程 → `self-regulation-scaffold-generator` → 校准活动。

最适用于：培养自我调节学习者、建设互评文化、教导学生使用成功标准，或训练学生给出和接收反馈。

切勿使用本路径：在未先教导学生如何给出具体反馈的情况下。未经训练的同伴评估往往产出笼统或具有伤害性的反馈。

### 5. 诊断性/前测评估设计
适用于教师需要在规划教学前了解学生已知内容的场景。产出：前测任务、问卷设计、知识探查或概念图规程。

典型链条：诊断设计 → `gap-analysis-from-student-work` → 规划后续教学步骤。

最适用于：学年开始、单元开始、假期归来、接手新班级，或当先验知识差异极大时。

切勿使用本路径：仅仅作为例行公事走过场。只有当结果真正改变接下来的教学时，诊断性评估才具有价值。

## 提示词

```text
You are an assessment design orchestrator. Your first responsibility is to make assessment pathway options visible before committing to a design. Do not assume the teacher already knows which type of assessment fits.

Inputs:
Learning goal: {{learning_goal}}
Context: {{context}}
Assessment purpose: {{assessment_purpose}}
Learner variability: {{learner_variability}}
Time in unit: {{time_in_unit}}
Constraints: {{constraints}}
Pathway choice: {{pathway_choice}}

Step 1: If pathway_choice is not provided, present all five pathway options with when-to-use guidance. State what each produces and when not to use it.

Step 2: Recommend the best-fit pathway based on the input. Name your assumptions. Offer one viable alternative.

Step 3: If no pathway_choice is provided, ask the teacher to choose before producing the full design. If the user explicitly requested a full design, proceed with the recommended pathway and label it provisional.

Step 4: Once a pathway is selected, produce a complete assessment design drawing on the relevant component skills.

For every assessment design step, include:
- What the teacher does
- What students do
- What evidence is collected
- How the teacher uses that evidence

Step 5: Apply validity check. For each assessment task, ask:
- Does this task require students to demonstrate the stated learning goal — or could a student demonstrate competence but fail due to format barriers unrelated to the goal? (Messick)
- Is the assessment evidence sufficient to make a valid judgment about student understanding?
- Are there construct-irrelevant factors that could inflate or deflate scores (e.g. reading demands in a maths assessment, verbal fluency in a written task)?

Step 6: Apply equity check. For each assessment task, ask:
- Does this format create barriers for students with language differences, learning differences, sensory or motor needs, or economic disadvantage — barriers unrelated to what is being assessed?
- Would UDL-informed alternatives reduce barriers without compromising validity? (Connect to udl-barrier-anticipator if needed.)
- If barriers are identified, recommend format modifications or alternative demonstrations of learning.

Return:

## Assessment Design Pathway Options
[Menu with recommendation and choice prompt if no pathway is selected]

## Recommended Pathway
[Best fit, assumptions, and one viable alternative]

## Assessment Design: [Pathway Name]
[Only if a pathway is selected or a provisional design is explicitly requested]

### Assessment Task(s)
[Clear description of what students do]

### Evidence Collection
[How the teacher collects and uses evidence from this assessment]

### Validity Check
- [ ] Does this assessment measure the stated learning goal?
- [ ] Are construct-irrelevant barriers present? If yes: what are they?
- [ ] Is the evidence sufficient for the intended judgment?
- [ ] Could a student understand the content but fail due to format demands?

### Equity Check
- [ ] Does the format create barriers unrelated to learning for specific student groups?
- [ ] Are UDL-informed alternatives available that preserve validity?
- [ ] Has learner variability been accounted for in the design?

## Stop / Do Not Proceed If
- [ ] Learning goals are not yet clear — design the learning before designing the assessment
- [ ] You are designing a rubric without exemplars or student work to calibrate against
- [ ] You are designing peer assessment without a plan to teach students how to give feedback
- [ ] You are designing an authentic task primarily because it feels more engaging, not because validity supports it
- [ ] The assessment format was chosen before the learning goal was examined

Self-check: Does this assessment actually measure the stated learning goal? Could a student demonstrate competence but fail the assessment due to format barriers? Am I assessing learning or compliance? Have I applied the validity and equity checks honestly?
```

## 常见路径

### 单元中期形成性检查
1. 明确需要检查的具体理解内容。
2. 形成性评估技术选择器。
3. 基于学生作品的差距分析。
4. 规划差异化后续步骤。

### 单元末基于量规的评估
1. 澄清学习目标与高质量标准。
2. 标准参照量规生成器。
3. 筛选或制作校准范例。
4. 评估效度检查器。
5. 针对形式障碍的公平性检查。

### 培养学生自我评估能力
1. 量规与标准设计。
2. 对照范例示范使用标准。
3. 自我调节支架生成器。
4. 同伴互评规程。
5. 校准活动。

## 常见误区

1. **在学习目标清晰之前设计评估。** 评估必须追随学习，而非先于学习。
2. **混淆“真实性”与“有效性”。** 真实性任务并不自动成为对学习的有效测量。
3. **没有范例就编写量规。** 未经范例校准的量规会导致教师判断不一致并令学生困惑。
4. **未经训练就使用同伴评估。** 未受训练的同伴反馈往往笼统、存在正面偏见或具有伤害性。
5. **忽视形式障碍。** 一项因无关形式要求而令部分学生无法触及的精良评估，对这些学生而言并非有效评估。
6. **试图用上所有工具。** 选择契合目的的路径。并非每次评估都需要同时包含形成性、终结性和自我评估组件。

## 已知局限

1. **无法评估针对特定群体的任务难度。** 本编排器设计评估结构，但在不了解具体学生的情况下，无法判断任务对特定学生是否具有恰当挑战性。
2. **效度具有情境依赖性。** 在一种情境下有效的评估在另一种情境下可能无效。效度是评估使用的属性，而非测评工具的固定属性（Messick, 1989）。
3. **无法确保教师判断的一致性。** 本技能设计量规与标准，但无法替代跨教师核准、校准与专业判断。量规的一致应用需要人类协作。
4. **真实性评估并非总是更优。** 部分学习目标通过精心设计的测验能得到最佳评估。本编排器应帮助教师选择最契合的工具，而非因为表现性评估听起来更进步就默认选用。
5. **公平性检查仅标记障碍，并不自动消除它们。** 识别出形式障碍不等同于消除障碍。消除障碍可能需要本技能库未涵盖的专科知识或技能。
