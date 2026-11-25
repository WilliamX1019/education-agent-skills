---
# AGENT SKILLS STANDARD FIELDS (v2)
name: wellbeing-learning-connection-mapper
description: "映射身心健康（wellbeing）举措与具体学业学习成果之间的循证关联。适用于论证身心健康项目投入、整合社会情感学习（SEL）或连接德育与教学工作的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/wellbeing-learning-connection-mapper"
skill_name: "身心健康与学习关联映射器"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "Fredrickson (2001) — The role of positive emotions in positive psychology: the broaden-and-build theory"
  - "Hattie (2009) — Visible Learning: student background factors affecting achievement"
  - "Roffey (2012) — Pupil wellbeing — teacher wellbeing: two sides of the same coin?"
  - "Durlak et al. (2011) — The impact of enhancing students' social and emotional learning: a meta-analysis"
  - "Seligman et al. (2009) — Positive education: positive psychology and classroom interventions"
input_schema:
  required:
    - field: "wellbeing_intervention"
      type: "string"
      description: "正在考虑或实施的身心健康实践或举措"
    - field: "school_context"
      type: "string"
      description: "学校的关键特征——学段、生源结构、当前挑战"
  optional:
    - field: "target_outcomes"
      type: "string"
      description: "学校希望达成的目标——例如降低焦虑、提高出勤率、提升投入度"
    - field: "current_data"
      type: "string"
      description: "来自情境引擎：出勤数据、行为数据、调研结果、学业成绩"
    - field: "stakeholder_audience"
      type: "string"
      description: "谁需要审阅这份论证——校董、高管团队（SLT）、家长、督学（Ofsted）"
    - field: "time_and_resources"
      type: "string"
      description: "可用的预算、教职工时间、培训承载力"
output_schema:
  type: "object"
  fields:
    - field: "evidence_map"
      type: "object"
      description: "从身心健康干预到具体学习成果的因果路径"
    - field: "mechanism_analysis"
      type: "string"
      description: "该干预预期**如何**改善学习——具体的心理机制"
    - field: "expected_outcomes"
      type: "array"
      description: "学生、班级和学校层面的预期成果及现实时间表"
    - field: "leadership_rationale"
      type: "string"
      description: "面向学校领导者的清晰、循证的陈述，连接身心健康举措与学业成果"
chains_well_with:
  - "perma-based-lesson-designer"
  - "belonging-classroom-culture-designer"
  - "trauma-informed-practice-designer"
  - "ruler-emotional-literacy-sequence"
teacher_time: "4 分钟"
tags: ["wellbeing", "positive-psychology", "broaden-and-build", "SEL", "school-leadership", "evidence-rationale"]
---

# 身心健康与学习关联映射器（Wellbeing-Learning Connection Mapper）

## 本技能的功能

映射一项身心健康举措与具体学习成果之间的可能关联，使学校领导者能够审慎**评估**而非自动背书该项投入。严格区分针对特定干预的直接证据、宏观理论、相关性发现以及本地观察。因果路径是一组有待检验的假设；其中某些箭头可能是未知的、存在反证的或缺乏支持的，而一份站得住脚的输出完全可能建议调整或否决该举措。输出包括机制分析、前提条件、附带不确定性说明的预期结果以及一份领导力论证草案。切勿为了显得有说服力而捏造本地事实、时间表或效应量估计。

## 循证依据

Fredrickson（2001）提出了“拓展与建构理论”（broaden-and-build theory），作为积极情绪与认知资源的一种解释视角；这是一种可能机制，而非任何自选身心健康举措都能改善学习的证明。Durlak 等（2011）综合了以学校为基础的 SEL 研究，并在相应证据子集中报告了学业增益；但这些结果不能在缺乏匹配证据的情况下直接套用到不同的干预（如某项具体的修复性实践）上，也不能直接用来预测某所本地学校的效果。Hattie（2009）综合了与学业成绩相关的各类影响因素；相关性效应并不直接验证某个具体项目。Roffey（2012）探讨了学生与教师福祉，Seligman 等（2009）探讨了积极教育与课堂干预。请保留每项文献的来源属性、适用情境与局限性，包括零效应、负效应或不确定发现。上述文献均不能将本技能生成的图谱直接验证为一套完整的因果干预方案。

## 输入规范

教师或学校领导者必须提供：
- **身心健康干预：** 正在考虑或实施的项目。*例如：“在每天清晨引入 10 分钟正念练习” / “实施修复性实践以替代留校察看” / “对全体教职工开展创伤知情方法培训” / “在 7 年级全面推行品格优势项目”*
- **学校情境：** 学校状况。*例如：“1,200 人的中学，高贫困地区，40% 学生享受补助（Pupil Premium），停学率高于平均水平，学业成绩良好但学生心理健康问卷得分下降”*

可选（如情境引擎可用，将自动注入）：
- **目标成果：** 学校希望达成的目标
- **当前数据：** 出勤、行为、调研、学业数据
- **受众对象：** 需要审阅论证的对象
- **时间与资源：** 预算、教职工承载力

## Prompt

```
You are an expert in wellbeing and learning science, with deep knowledge of Fredrickson's (2001) broaden-and-build theory, Durlak et al.'s (2011) meta-analysis of SEL programmes, Hattie's (2009) research on student background factors and achievement, and Seligman et al.'s (2009) positive education model. Assess possible connections without presuming a causal benefit. Explain mechanisms and uncertainty clearly for school leadership, including when the evidence does not support adoption.

IMPORTANT: The rationale must be honest. Do not overstate the evidence. Where evidence is strong, say so. Where it is emerging or contested, say that too. School leaders who discover that their evidence base was exaggerated will lose trust in the entire wellbeing agenda. Honest, calibrated evidence is more persuasive than hype.

Your task is to map the wellbeing-learning connections for:

**Wellbeing intervention:** {{wellbeing_intervention}}
**School context:** {{school_context}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Target outcomes:** {{target_outcomes}} — if absent, offer candidate outcomes to investigate, not predicted benefits.
**Current data:** {{current_data}} — if absent, mark local baseline and trends unknown and propose proportionate aggregated/non-identifying data; never invent incident histories or demand identifiable learner records.
**Stakeholder audience:** {{stakeholder_audience}} — if not provided, design the rationale for school senior leadership.
**Time and resources:** {{time_and_resources}} — if not provided, note resource requirements and flag where investment is needed.

Apply these evidence-based principles:

1. **Test the proposed causal pathway (Fredrickson, 2001; Durlak et al., 2011):**
   - Don't just state "wellbeing improves learning." Show the MECHANISM.
   - Intervention → immediate psychological effect → medium-term behavioural change → learning outcome.
   - For each link state supported, plausible/indirect, contradicted or unknown; cite the actual evidence type/context and identify missing links. Separate causal evidence from association or theory. No supported pathway is a valid finding; retain null/negative findings and consider rejection or adaptation.
   - Be specific: which ASPECT of wellbeing? Which ASPECT of learning?

2. **Distinguish proximal and distal outcomes:**
   - Proximal: possible changes in student experience, behaviour, engagement or attendance, which may be absent or adverse.
   - Distal: possible changes in academic outcomes, exam results or progress; these need separate evidence and cannot be assumed from proximal change.
   - Use intervention-specific evidence for timelines; otherwise state unknown. A chosen review date is a planning decision, not a forecast of benefit.

3. **Identify necessary conditions for impact:**
   - Most wellbeing interventions only work under specific conditions: staff buy-in, consistent implementation, sufficient dosage, alignment with school culture.
   - Poor implementation may affect outcomes, but even well-delivered initiatives can show no benefit or harm; do not use implementation as an automatic excuse for negative findings.

4. **Address the sceptic's question (Hattie, 2009):**
   - "This takes time from teaching — how does it improve results?"
   - The answer must be evidence-based and specific, not ideological.
   - If the evidence is weak for a particular claim, say so and suggest what other evidence exists.

5. **Provide the leadership rationale:**
   - A clear, jargon-free draft for human factual/source review before a headteacher presents it. Label local statements observed/reported, proposed or unknown; keep caveats in the delivered rationale.
   - Structured as: the problem → the intervention → the evidence → the expected outcomes → the conditions for success.

Return your output in this exact format:

## Wellbeing-Learning Connection Map: [Intervention Name]

**Intervention:** [Description]
**School context:** [Summary]

### Causal Pathway

[Proposed links with status, evidence type/source/context and missing evidence for every arrow; no supported pathway is an acceptable result]

### Mechanism Analysis

[How the intervention might affect learning, distinguishing theory, association, intervention evidence and supplied local observations, with null/negative/unknown findings retained]

### Expected Outcomes

**Proximal outcomes:**
[Supported expectations or unknown; positive, null and adverse possibilities and what to measure]

**Distal outcomes:**
[Supported expectations or unknown; distinguish academic outcomes from participation/enjoyment]

**Timing and review:**
[Source-backed timeline if available; otherwise unknown, with a separately labelled proposed review date]

### Conditions for Impact

[What must be in place for the intervention to work — implementation requirements, staff training, dosage, consistency]

### Leadership Rationale

[Draft for authorised human review of local facts, source applicability, resource trade-offs and uncertainty before presentation or investment; distinguish observed/reported, proposed and unknown]

### Honest Caveats

[What the evidence does NOT show, where claims are uncertain, what could go wrong]

**Self-check before returning output:** Verify that (a) each proposed link has an honest evidence type, status and missing-link check, (b) outcome/timing uncertainty and null/negative findings remain visible, (c) the evidence is accurately represented — not overstated, (d) conditions for impact are specified, and (e) the leadership rationale is clear and retains caveats and human factual review; no local facts, transferred effects or timelines are invented.
```

## 示例输出

**场景：** *身心健康干预：“引入全校性修复性实践方法，取代现行的基于留校察看的行为制度” / 学校情境：“城市中学，900 名学生，45% 享受补助（Pupil Premium），定期停学率高于平均水平，行为问题是教职工调研中的首要关切，相当数量的学生存在童年不良经历（ACEs）” / 目标成果：“减少停学、提高出勤率、改善课堂学习环境” / 受众对象：“校董——其中几人对‘在行为问题上心软’能否改善成绩持怀疑态度”*

---

## 身心健康与学习关联映射图：全校性修复性实践

**干预措施：** 拟议采用全校性修复性方法替代现行基于留校察看的制度；任何政策变更均需经授权领导层审查。
**学校情境（本虚构场景中报告）：** 城市中学，900 名学生，45% 享受补助，停学率高于平均水平且教职工对行为问题感到担忧。未提供本地事件趋势、出勤基线或结果评估。切勿据此推断任何单个学生存在创伤。

### 因果路径

| 拟议链条 | 状态与证据类型 | 缺失环节 / 核查项 |
|---|---|---|
| 修复性方法 → 更安全的人际关系 | 在此处属于“合理但间接”：未提供针对修复性实践的专门研究文献与实施细节；一般关系文献仅作背景依据 | 获取适用的干预研究；评估各方同意、权力不对称、保护机制与教职工承载力 |
| 更少的停学 → 更多的课堂准入机会 | 条件性推理，而非实测的本地效应 | 确认停学率是否真正改变、可获得的教学质量如何，以及教室是否依然安全 |
| 更安全的关系/课堂准入 → 学业学习 | “合理但间接”：Hattie（2009）提供了宏观学业背景，但并不证明本具体项目的效果 | 分别测量课堂准入、教学质量与学业成果；考虑其他同期变量 |
| 本修复性实施方案 → 学业增益 | 基于所提供证据处于**未知**状态 | Durlak 等（2011）的 SEL 发现不能用来估算这一修复性项目的效应量 |

### 机制分析

可能的机制包括修复伤害的机会以及改善获得教学的机会。这些机制的实现需要恰当的自愿参与及有效的保护措施；绝不能强迫受伤害的学习者与伤害自己的人会面。对话本身未必能自动提升安全感或促进学习，在某些权力不对称情境下甚至可能并不恰当。Fredrickson 的理论提供了关于情绪的背景视角，并非支持修复性政策的直接证据。人际关系与出勤率即使改善，也未必带来学习提升；整条因果链在此处仍属未确立状态。

### 预期成果

**近期成果：** 再犯率、停学率、出勤率以及学习者/教职工体验可能会改善、保持不变或恶化。针对本拟议实施方案，目前没有可支撑的效应量估计。

**远期成果：** 对学业的影响**未知**。一项 SEL 元分析不能用来证明这一不同干预必然带来预期学业增益。

**时间表与复盘：** 见效时间表**未知**。领导层可以在遵循常规保护与政策要求的前提下，决定在约定的试用期后进行复盘；该复盘日期是一项规划决策，而非基于研究的“见效时间预测”。一旦出现负面证据应及时叫停或调整，切勿以“处于预设的实施低谷期”为由硬撑。

### 产生影响的前提条件

审查与本地政策的兼容性、受过培训的引导师、恰当的自愿参与机制、持续的保护与安全保障、教职工时间成本、资源权衡以及领导层支持。培训时长必须依据所选方案与学校情境确定，切勿编造最低小时数。采用可比口径收集适度且聚合的非识别性基线与跟进数据；本论证不需要可识别个人身份的事件叙事。除出勤率与停学率外，还需同步监测再犯率与报复行为。仅仅“实施到位”本身并不足以证明产生了正面影响。

### 领导力论证草案

“**已知报告：** 我们的背景描述显示停学率高于平均水平且教职工担忧行为问题。但目前并未提供三年期重复事件趋势，也没有本地证据证明现行制度直接导致了这些结果。

**拟议方案：** 我们正在考虑引入面向问责与修复的修复性方法，但前提是经过安全性、自愿适用性、政策与资源审查。在决定投入之前，我们需要查阅适用的修复性研究并制定可行的实施计划。

**未知部分：** 现有证据尚不能确立本地学业收益、停学率下降百分比或见效所需时间。一般性的 SEL 研究发现不能作为本项目的效果预估。我们应当横向比较不同方案（包括微调或暂不采用），并在决策中如实保留零效应或负面发现。”

这是一份草案：在正式呈报或做出投资决策前，授权学校领导者必须核实本地事实、文献适用性、政策与成本。

### 坦诚的局限性说明

该机制看似合理，但尚未在本校情境下得到证实。停学人数减少本身并不足以证明校园更安全、学习更好或身心更健康；报告口径的变化同样会改变记录在案的事件数量。请分别监测保护状况、课堂参与度与学习成果。无论贴上“修复性”的标签，还是撰写一份自信满满的论证，都无法直接确立有效性；且学校政策纪律处分可以与恰当的修复性工作并存。

---

## 已知局限性

1. **关联映射图展示的是“理论路径”，而非必然保证的结果。** 每一环都需要各自接受评估；其中某些环节可能是未知的、存在反证的或缺失的。图谱完全可能得出“拟议路径或投资缺乏足够支撑”的结论。

2. **本工具生成的是论证与评估框架，而非实施计划。** 合理的论证不同于充分的采纳决策或落地执行方案。本技能应与实施规划和教职工培训配合使用——仅靠论证本身无法带来改变。

3. **不同身心健康干预的证据强弱不一。** 使用者必须自行核查拟议干预的证据评估与文献适用性，但客观而言，某些干预（如校园正念项目）的证据争议性远大于另一些干预（如系统性 SEL 项目）。本工具应当如实标示证据局限，而不是对所有干预一视同仁地鼓吹。
