---
# AGENT SKILLS STANDARD FIELDS (v2)
name: place-based-curriculum-orchestrator
description: "呈现路径选项并从本地场所、课程要求或社区议题出发编排基于地方的课程设计。适用于应将“地方”作为主要学习文本的场景。"
disable-model-invocation: false
user-invocable: true
effort: high

# EXISTING FIELDS
skill_id: "original-frameworks/place-based-curriculum-orchestrator"
skill_name: "基于地方的课程编排器"
domain: "original-frameworks"
version: "1.0"
evidence_strength: "emerging"
evidence_sources:
  - "Sobel (2004) — Place-Based Education: connecting classrooms and communities"
  - "Smith (2002) — Place-based education: learning to be where we are"
  - "Gruenewald (2003) — The best of both worlds: a critical pedagogy of place"
  - "Castagno & Brayboy (2008) — Culturally responsive schooling for Indigenous youth"
  - "Bang, Medin & Atran (2007) — Cultural mosaics and mental models of nature"
input_schema:
  required:
    - field: "starting_point"
      type: "string"
      description: "教育者出发的具体场所、课程要求、社区问题或本地议题"
    - field: "learner_stage"
      type: "string"
      description: "年龄范围或年级"
  optional:
    - field: "subject_or_curriculum_content"
      type: "string"
      description: "需要涵盖的课程内容、标准、能力或学科"
    - field: "local_place"
      type: "string"
      description: "具体场所：溪流、商业街、公园、校园、街区、建筑、食物系统等"
    - field: "community_knowledge_holders"
      type: "string"
      description: "了解该场所的人员、群体、长者、组织或本地专家"
    - field: "constraints"
      type: "string"
      description: "时间、可及性、安全、交通、许可、评估、政策或资源限制"
    - field: "pathway_choice"
      type: "string"
      description: "可选的已选路径。若缺失，在设计完整序列前先呈现选项。"
output_schema:
  type: "object"
  fields:
    - field: "pathway_options"
      type: "array"
      description: "附带适用场景说明与权衡的合适路径菜单"
    - field: "recommended_pathway"
      type: "object"
      description: "附带预设条件的最佳匹配路径推荐；不应隐匿备选方案"
    - field: "orchestrated_skill_chain"
      type: "array"
      description: "按顺序使用的离散技能及交接产出"
    - field: "curriculum_design_sequence"
      type: "object"
      description: "选定路径后教师可直接使用的基于地方的单元或课程序列"
    - field: "stop_slow_checks"
      type: "array"
      description: "针对伦理、安全、文化谦逊、课程效度与可行性的检查"
chains_well_with:
  - "place-based-inquiry-anchor"
  - "ecological-inquiry-anchor-designer"
  - "phenomenon-based-unit-anchor"
  - "culturally-responsive-teaching-designer"
  - "curriculum-knowledge-architecture-designer"
  - "learning-target-authoring-guide"
  - "assessment-validity-checker"
  - "systems-awareness-iceberg"
  - "mental-model-mapper"
teacher_time: "8 分钟"
tags: ["orchestrator", "composite-framework", "practitioner-framework", "place-based", "emerging-evidence", "curriculum", "pathways", "local", "community", "critical-pedagogy-of-place"]
---

# 基于地方的课程编排器

## 本技能的功能

本编排器协助教育者设计以特定本地场所作为核心学习文本的课程。它不会假设教育者已经知道哪条基于地方的路径最契合。在做出完整设计决策之前，它会先呈现路径选项、推荐最佳匹配、解释权衡，并请求用户选择路径（除非用户已经选定）。

当学习应当扎根于一条溪流、一条街道、一片校园、一座花园、一个街区、一栋建筑、一座纪念碑、一套食物系统、一项本地产业、一个社区故事或其他真实场所时，使用本技能。“地方”不应只是装饰性的点缀；它应当塑造问题、证据、知识持有者、学习活动以及可能的行动。

## 证据空间与证据强度

这是一个复合型实践者框架。它协调了多项循证教学传统，但具体的路径架构尚未作为完整干预方案接受过直接评估。请将其作为课程设计支架使用，而非声称遵循该序列必定产出特定成效。

### 组件证据

- **基于地方的教育（Place-Based Education）**（中等）：Sobel（2004）、Smith（2002）与 Gruenewald（2003）提供了坚实的理论与实践文献基础。研究显示其在投入度与本地联结方面有益处；实验性证据有限。
- **文化回应教学（Culturally Responsive Pedagogy）**（中等）：Castagno 与 Brayboy（2008）以及 Bang、Medin 与 Atran（2007）确立了文化框架在基于地方与生态探究中的重要性。在原住民教育情境中证据充分。
- **地方的批判教学法（Critical Pedagogy of Place）**（中等）：Gruenewald（2003）将批判与基于地方的学习整合在一起；教育研究予以支持，但直接课堂效应研究有限。
- **组件技能**（各异）：`place-based-inquiry-anchor`、`ecological-inquiry-anchor-designer`、`curriculum-knowledge-architecture-designer` 与 `assessment-validity-checker` 各自带有独立的证据评级。

### 综合证据

包括五条命名路径选项、路由逻辑、交接结构与停止/放缓检查在内的编排路径，是 Gareth Manning 的原创综合。在经真实教育者测试并基于课堂使用修订之前，应视其为新兴证据。

### 本技能不应声称的内容

切勿声称本框架已作为课程项目或通往成效提升的保障路径获得验证。切勿使用它绕过教师判断、本地知识、文化礼仪、社区关系或评估效度检查。

### 适用范围

将本技能用作基于地方课程规划的设计支架。当教育者需要协助在若干可行设计路线间做出选择，并在投入完整单元设计之前理解各自权衡时最为适用。

## 依赖维护

本技能依赖于 `place-based-inquiry-anchor`、`ecological-inquiry-anchor-designer`、`curriculum-knowledge-architecture-designer`、`culturally-responsive-teaching-designer`、`learning-target-authoring-guide` 与 `assessment-validity-checker`。每当任一被串联技能变更其证据强度、输出模式、核心质量把关点或主要警示时，请复核本编排器。除非复合工作流本身经过实证检验，否则切勿提高本复合框架的证据等级声明。若某组件技能被弃用或大幅修订，使用前必须先复核本编排路径。

## 路径原则

基于地方的编排器应当“路由（route）”，而非“强推（bulldoze）”。它应当让可用路径对教育者清晰可见，以便其有意识地做出选择。

如果未提供 `pathway_choice`，先返回**路径选项菜单**，附带推荐方案并提问：“我应将哪条路径展开为完整设计？”如果用户明确要求立即生成完整设计，则按推荐路径推进，但将其标注为“暂定（provisional）”。

## 路径选项

### 1. 地方优先探究（Place-First Inquiry）
适用于教育者已选定特定场所，并希望发现该场所能教给学生什么的场景。从直接接触与观察开始，然后围绕浮现的内容映射课程。

典型链条：`place-based-inquiry-anchor` → `curriculum-knowledge-architecture-designer` → `learning-target-authoring-guide` → `assessment-validity-checker`。

### 2. 课程优先本地化（Curriculum-First Localisation）
适用于必修内容或标准已固定，而教育者希望将其扎根于本地的场景。从课程出发，随后识别哪个本地场所能够真实地揭示它。

典型链条：`curriculum-knowledge-architecture-designer` → `place-based-inquiry-anchor` 或 `ecological-inquiry-anchor-designer` → `learning-target-authoring-guide` → `assessment-validity-checker`。

### 3. 批判性地方探究（Critical Place Inquiry）
适用于该场所涉及身份认同、权力、历史、可及性、土地、文化、公平或争议性故事的场景。本路径同时包含欣赏与批判。

典型链条：`place-based-inquiry-anchor` → `culturally-responsive-teaching-designer` → `source-credibility-evaluation-protocol` 或 `historical-document-set-curator` → `assessment-validity-checker`。

### 4. 生态地方探究（Ecological Place Inquiry）
适用于本地场所是一个生命系统的场景：池塘、溪流、树木、花园、树篱、土壤、校园绿地、海岸或城市生态系统。

典型链条：`ecological-inquiry-anchor-designer` → `outdoor-learning-sequence-designer` → `learning-target-authoring-guide` → 可选 `agency-circles-for-systems-action`。

### 5. 地方 + 系统路径（Place + Systems Pathway）
适用于该场所议题涉及反复出现的模式、社会结构、人类决策、心智模式或能动性问题的场景。慈悲系统觉察工具为可选项，应因情境需要而使用，而非默认套用。

典型链条：`place-based-inquiry-anchor` → `systems-awareness-iceberg` 或 `aspirational-systems-iceberg` → `mental-model-mapper` → `agency-circles-for-systems-action`。

## 提示词

```text
You are a place-based curriculum orchestrator. Your first responsibility is to make pathway options visible before committing to a design. Do not assume the educator knows the pathways.

Inputs:
Starting point: {{starting_point}}
Learner stage: {{learner_stage}}
Subject/curriculum content: {{subject_or_curriculum_content}}
Local place: {{local_place}}
Community knowledge holders: {{community_knowledge_holders}}
Constraints: {{constraints}}
Pathway choice: {{pathway_choice}}

Step 1: Present pathway options unless pathway_choice is already provided.
Include:
- Place-First Inquiry
- Curriculum-First Localisation
- Critical Place Inquiry
- Ecological Place Inquiry
- Place + Systems Pathway
For each pathway, state what it is for, what it produces, and when not to use it.

Step 2: Recommend the best-fit pathway based on the input. Explain why, and name the assumptions behind the recommendation.

Step 3: If no pathway_choice was provided, ask the educator to choose before producing the full design. If the user explicitly requested a full design anyway, continue with the recommended pathway and label it provisional.

Step 4: Once a pathway is selected, orchestrate the skill chain. For every step, specify:
- skill/tool to use
- purpose
- input it needs
- output it should produce
- handoff to the next step
- do-not-proceed-if check

Step 5: Produce the curriculum design sequence in teacher-usable language.

Return:

## Place-Based Curriculum Pathway Options
[Menu of pathways, with recommendation and choice prompt if needed]

## Recommended Pathway
[Best fit, assumptions, and alternatives]

## Orchestrated Skill Chain
[Step-by-step chain with handoffs]

## Place-Based Curriculum Design
[Only if a pathway is selected or provisional design is explicitly requested]

## Stop / Slow Down Checks
- [ ] Is the place a primary text, not a decorative hook?
- [ ] Are local/community knowledge holders treated as knowledge partners, not content props?
- [ ] Are cultural, Indigenous, historical, or access issues handled with humility?
- [ ] Does the design avoid asking students to act before they understand the place?
- [ ] Does assessment match the actual learning, not just the final product?
- [ ] Are student action and adult/community responsibility clearly distinguished?
```

## 常见误区

1. 把地方当作主题装饰，而非知识的源泉。
2. 在接触、观察与探究之前就急于转向行动。
3. 生硬地把课程内容硬塞进某个地方。
4. 单向索取社区故事而缺乏互惠回馈。
5. 即便探究主要是生态、历史或概念性的，也自动套用慈悲系统工具。
6. 因为单元感觉“很真实”就忽略了评估效度。

## 已知局限

1. **无法评估社区关系。** 本编排器无法判断拟议的本地知识持有者或社区伙伴是否愿意参与、是否适宜邀请或是否安全接触。这需要预先建立关系，本技能无法替代。
2. **不提供文化胜任力规程。** 本技能会标记何时需要文化、原住民或历史敏感性（批判性地方探究路径），但无法替代专科文化指导或社区协商。标记不等于流程本身。
3. **评估效度仅被标记，并未被核验。** 停止/放缓检查包含评估对齐，但核查评估是否真正测量了预期学习目标需要作为独立步骤使用 `assessment-validity-checker`。
4. **面对不熟悉的地方时效果下降。** 当教师对本地场所不够了解时，本技能无法从单薄的输入中生成有意义的设计。直接接触、本地研究与社区知识必须先于或与本编排并行开展。
