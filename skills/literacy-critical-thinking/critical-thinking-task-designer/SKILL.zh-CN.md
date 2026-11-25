---
# AGENT SKILLS STANDARD FIELDS (v2)
name: critical-thinking-task-designer
description: "设计瞄准特定技能（如评估证据、识别假设或分析论证）的批判性思维任务。适用于将批判性分析嵌入学科课程时。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "literacy-critical-thinking/critical-thinking-task-designer"
skill_name: "批判性思维任务设计师"
domain: "literacy-critical-thinking"
version: "1.0"
evidence_strength: "strong"
evidence_sources:
  - "Paul & Elder (2008) — The Miniature Guide to Critical Thinking Concepts and Tools"
  - "Facione (1990) — Critical Thinking: a statement of expert consensus for purposes of educational assessment and instruction (Delphi report)"
  - "Willingham (2007) — Critical thinking: why is it so hard to teach?"
  - "Abrami et al. (2008) — Instructional interventions affecting critical thinking skills and dispositions: a meta-analysis"
  - "Ennis (1989) — Critical thinking and subject specificity: clarification and needed research"
input_schema:
  required:
    - field: "topic"
      type: "string"
      description: "批判性思维任务将嵌入其中的学科内容"
    - field: "student_level"
      type: "string"
      description: "年龄/年级及当前的思维水平"
    - field: "critical_thinking_focus"
      type: "string"
      description: "需要培养的具体批判性思维技能——例如评估证据、识别假设、分析论证、比较视角、察觉偏见"
  optional:
    - field: "subject_area"
      type: "string"
      description: "学科语境——批判性思维具有领域特定性"
    - field: "student_profiles"
      type: "array"
      description: "来自上下文引擎：先前的批判性分析经验、口头表达自信度"
    - field: "task_format"
      type: "string"
      description: "偏好的形式——书面、讨论、视觉或混合"
    - field: "time_available"
      type: "string"
      description: "任务可用时间"
output_schema:
  type: "object"
  fields:
    - field: "task"
      type: "object"
      description: "包含清晰指令、刺激材料与引导问题的批判性思维任务"
    - field: "critical_vs_surface_guide"
      type: "object"
      description: "区分批判性回答与浅层回答的标准，附每种回答的示例"
    - field: "teacher_prompts"
      type: "array"
      description: "用于将浅层回答推向真正批判性参与的追问提示"
    - field: "assessment_indicators"
      type: "string"
      description: "学生回答中表明真正批判性思维的可观察特征"
chains_well_with:
  - "socratic-questioning-sequence-generator"
  - "argument-structure-scaffold-generator"
  - "source-credibility-evaluation-protocol"
  - "discussion-protocol-selector"
  - "ai-output-critical-audit-designer"
teacher_time: "4 分钟"
tags: ["critical-thinking", "analysis", "evaluation", "domain-specific", "higher-order-thinking"]
---

# 批判性思维任务设计师

## 本技能的作用

设计一项要求真正批判性评价的任务——不仅仅是理解或回忆，而是评估证据、识别假设、分析竞争性视角或察觉偏见——并嵌入具体学科内容之中。关键在于，输出包含区分“批判性回答”与“浅层回答”的标准（以便教师分辨差异），以及将敷衍回答推向真正批判性参与的追问提示。AI 在此尤为有价值，因为设计真正需要批判性思维的任务（而不是“看起来”像需要批判性思维、实则仅靠回忆或表达个人观点就能应付的任务）是评估设计中最难的环节之一——许多标榜“批判性思维”的任务实际上考查的只是理解、对预设结构的服从，或未经评估地发表观点。

## 循证基础

Paul & Elder (2008) 将批判性思维定义为“以改进思维为目的去分析和评估思维的艺术”，确立了八大思维要素（目的、问题、信息、推论、假设、概念、意涵、视角）与九大智识标准（清晰度、准确性、精确性、相关性、深度、广度、逻辑性、重要性、公正性）。Facione (1990) 主持的德尔菲共识项目将批判性思维界定为包含六项核心技能：阐释、分析、评估、推断、解释与自我调节。关键在于，Willingham (2007) 证明批判性思维不能作为通用技能孤立教授——它具有领域特定性（domain-specific）。一名能批判性评估历史史料的学生，未必能批判性评估科学主张，因为批判性思维需要深厚的领域知识来判断在每个领域中什么才算好证据、有效推理和合理替代解释。这具有深远启示：孤立地“教批判性思维”（作为独立技能）迁移效果微弱；将批判性思维嵌入特定领域内容才能产出更强效果。Abrami 等 (2008) 在一项元分析中证实了这一点：当批判性思维教学嵌入学科内容“并且”包含对批判性思维原则的显性教学时（即“混合”取向，效应量 0.94），效果最显著。Ennis (1989) 认为，尽管批判性思维兼具通用与领域特定成分，但有效教学必须落实领域特定成分——即学科内部关于证据与推理的标准。

## 输入模式

教师必须提供：
- **Topic（主题）：** 学科内容。*例如："The causes of the French Revolution" / "Whether nuclear energy should replace fossil fuels" / "The reliability of different types of historical evidence" / "How Shakespeare presents power in Macbeth"*
- **Student level（学生水平）：** 年级与当前思维水平。*例如："Year 11, can express opinions but struggle to support them with evidence or consider counter-arguments" / "Year 8, can identify basic arguments but don't spontaneously evaluate their strength"*
- **Critical thinking focus（批判性思维焦点）：** 具体批判性思维技能。*例如："Evaluating the strength of evidence" / "Identifying unstated assumptions" / "Comparing two competing interpretations" / "Detecting bias in a source" / "Distinguishing correlation from causation"*

可选（如上下文引擎可用则自动注入）：
- **Subject area（学科领域）：** 学科语境
- **Student profiles（学生档案）：** 先前批判性分析经验、口头自信度
- **Task format（任务形式）：** 书面、讨论、视觉或混合
- **Time available（可用时间）：** 任务分钟数

## Prompt

```
You are an expert in critical thinking pedagogy, with deep knowledge of Paul & Elder's (2008) critical thinking framework, Facione's (1990) Delphi consensus on critical thinking skills, Willingham's (2007) research on domain-specificity of critical thinking, and Abrami et al.'s (2008) meta-analysis of critical thinking interventions. You understand that critical thinking is NOT a generic skill that can be taught in isolation — it must be embedded in domain-specific content, because what counts as good evidence, valid reasoning, and fair evaluation differs by discipline.

Your task is to design a critical thinking task for:

**Topic:** {{topic}}
**Student level:** {{student_level}}
**Critical thinking focus:** {{critical_thinking_focus}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, infer the most likely discipline from the topic and embed critical thinking within that discipline's standards of evidence and reasoning.
**Student profiles:** {{student_profiles}} — if not provided, design for a mixed-ability class where most students can express opinions but few spontaneously evaluate the quality of their own reasoning.
**Task format:** {{task_format}} — if not provided, design a written task with the option for discussion extension.
**Time available:** {{time_available}} — if not provided, design for approximately 20 minutes.

Apply these evidence-based principles:

1. **Domain-specific, not generic (Willingham, 2007; Ennis, 1989):**
   - The task must be embedded in the specific subject content — not a generic "critical thinking exercise."
   - The critical thinking required should reflect how experts in this discipline actually think: how historians evaluate sources, how scientists evaluate evidence, how literary critics analyse texts, how mathematicians verify reasoning.
   - The task should require domain knowledge to complete — a student who thinks critically but knows nothing about the topic should struggle, because critical thinking without knowledge is empty.

2. **Require genuine evaluation, not just opinion (Paul & Elder, 2008):**
   - The task must require students to EVALUATE — weigh evidence, assess reliability, consider alternatives, identify weaknesses — not just STATE an opinion.
   - "Do you agree with X?" is NOT a critical thinking question (it invites unsupported opinion).
   - "How strong is the evidence for X? What would need to be true for the opposite to be the case?" IS a critical thinking question (it requires evaluation).
   - Tasks should have no obvious "right answer" that students can guess from the teacher's tone — the answer depends on the quality of reasoning, not the position taken.

3. **Include criteria for distinguishing critical from surface responses (Facione, 1990):**
   - Provide clear examples of what a surface-level response looks like vs. what a critical response looks like for THIS specific task.
   - Surface responses typically: restate the question, express unsupported opinion, describe rather than evaluate, list rather than analyse, agree with the most obvious interpretation.
   - Critical responses typically: evaluate the quality of evidence, identify unstated assumptions, consider alternative explanations, acknowledge complexity, qualify claims appropriately.

4. **Provide follow-up prompts that push toward depth (Abrami et al., 2008):**
   - Most students will initially produce surface responses. The follow-up prompts should push them deeper.
   - "What evidence supports that?" / "What would someone who disagrees say?" / "How confident are you, and why?" / "What would change your mind?"
   - These prompts are more effective than simply marking the response as "not deep enough."

5. **The "mixed" approach (Abrami et al., 2008):**
   - Make the critical thinking skill EXPLICIT — tell students what they're practising and why.
   - "Today we're practising evaluating the strength of evidence. This means looking at EACH piece of evidence and asking: how reliable is this? How relevant is this? How sufficient is this?"
   - Don't just give the task — teach the thinking process the task requires.

Return your output in this exact format:

## Critical Thinking Task: [Topic]

**For:** [Student level]
**Subject:** [Discipline]
**CT focus:** [Critical thinking skill]
**Time:** [Minutes]

### The Task

**Explicit CT framing:** [1–2 sentences telling students what critical thinking skill they're practising and what it means]

**Stimulus material:** [The text, data, scenario, or source students will work with — or a description of what to provide]

**Task instructions:** [Clear instructions that require evaluation, not just opinion]

**Guiding questions:** [Scaffolded questions that structure the critical thinking process]

### Critical vs. Surface Response Guide

**A surface-level response looks like:**
[Specific example of a surface response to THIS task — showing what to watch for]

**A critical response looks like:**
[Specific example of a critical response to THIS task — showing what genuine critical thinking produces]

**The key difference:** [What separates surface from critical in this specific context]

### Teacher Follow-Up Prompts

[5–6 prompts the teacher can use when students produce surface responses — each designed to push thinking deeper without giving the answer]

### Assessment Indicators

[What to look for in student responses that indicates genuine critical thinking — specific, observable features, not vague descriptions like "shows depth"]

**Self-check before returning output:** Verify that (a) the task is embedded in domain-specific content, not generic, (b) the task requires genuine evaluation, not just opinion or recall, (c) the surface vs. critical examples are specific and clearly different, (d) follow-up prompts push toward critical thinking without providing the answer, (e) a student cannot answer the task well through recall alone — domain knowledge is necessary but not sufficient, and (f) the task has no obvious "right answer" that rewards guessing the teacher's preference rather than reasoning.
```

## 示例输出

**场景：** *Topic: "Whether the atomic bombing of Hiroshima was justified" / Student level: "Year 10, can express strong opinions on this topic but tend to argue from emotion rather than evidence — they say 'it was wrong because killing civilians is always wrong' or 'it was right because it ended the war' without evaluating the evidence for either position" / Critical thinking focus: "Evaluating the strength of competing arguments — weighing evidence for and against a historical judgement" / Subject area: "History"*

---

## 批判性思维任务：广岛原子弹轰炸

**适用对象：** 十年级历史
**学科：** 历史
**批判性思维焦点：** 评估竞争性论证的强度——权衡支持与反对某项历史评判的证据
**时间：** 25 分钟

### 任务设计

**显性批判性思维框定：**
"Today we're practising a specific critical thinking skill: evaluating the STRENGTH of arguments, not just agreeing or disagreeing. This means looking at the evidence each side uses and asking: how reliable is this evidence? How relevant? Does it actually support the conclusion? Strong critical thinkers can explain why an argument is weak even when they agree with the conclusion, and why an argument is strong even when they disagree."

**刺激材料：**

发给学生两段简短的论证节选（每段 150–200 词）：

**论证 A —— “轰炸具有正当性”：**
"By August 1945, the Japanese military had shown it would fight to the last man. The battles of Iwo Jima and Okinawa cost over 100,000 Allied casualties and demonstrated that an invasion of Japan would result in unprecedented loss of life. Military planners estimated that Operation Downfall — the planned invasion of Japan — would cost between 250,000 and 1,000,000 Allied casualties and potentially millions of Japanese deaths, both military and civilian. The atomic bomb ended the war in days, without an invasion. While the civilian deaths at Hiroshima were devastating, the alternative — a prolonged invasion — would almost certainly have killed more people on both sides. President Truman faced a terrible choice, but chose the option that likely saved the greatest number of lives overall."

**论证 B —— “轰炸不具有正当性”：**
"By August 1945, Japan was already on the verge of surrender. Its navy was destroyed, its cities were being firebombed, and the Soviet Union had just declared war. American intelligence intercepted Japanese diplomatic cables showing that significant factions within the Japanese government were seeking peace terms. The US chose to drop the bomb not primarily to end the war but to demonstrate American power to the Soviet Union at the start of the Cold War, and to justify the $2 billion cost of the Manhattan Project. The bombing of Hiroshima killed approximately 80,000 people instantly and tens of thousands more from radiation — the vast majority civilians. Alternative options existed: a demonstration bombing on an uninhabited island, or modified surrender terms allowing Japan to keep the Emperor (which was eventually permitted anyway)."

**任务指令：**

"Do NOT write about whether YOU think the bombing was justified. Instead, evaluate the ARGUMENTS.

For EACH argument (A and B):
1. What is the strongest piece of evidence used? Why is it strong?
2. What is the weakest piece of evidence or reasoning? Why is it weak?
3. What is ONE thing this argument ASSUMES without proving?
4. What would this argument need to be MORE convincing?

Then: Which argument is BETTER SUPPORTED by its evidence — regardless of whether you agree with its conclusion? Explain your reasoning."

**引导问题：**
- "For Argument A: The casualty estimate for the invasion ranges from 250,000 to 1,000,000. What does that range tell you about the reliability of this evidence?"
- "For Argument B: The argument claims the bomb was dropped 'to demonstrate American power to the Soviet Union.' What evidence is provided for this motivation? Is it sufficient?"
- "Both arguments use casualty numbers. Which argument's numbers are more verifiable? Why does that matter?"
- "What information would you need, that NEITHER argument provides, to make a stronger judgement?"

### 批判性回答 vs. 浅层回答指南

**浅层回答示例：**
"Argument A is stronger because it makes a good point about how many people would have died in an invasion. The bomb saved lives in the long run. Argument B is weaker because it tries to make America look bad by saying they only did it for political reasons."

*为何属于浅层：* 学生把关于轰炸的个人“观点”伪装成了对论证的“评估”。他们赞同 A、反对 B，但并未真正评估证据质量。对论证 B 的评语暴露出学生是根据结论（不喜欢该结论）来评判，而非根据证据强度。其中完全没有对假设、可靠性或充分性的分析。

**批判性回答示例：**
"Argument A's strongest evidence is the casualty figures from Iwo Jima and Okinawa — these are real battles with documented casualties that genuinely suggest an invasion would be costly. However, its weakest point is the invasion casualty estimate of '250,000 to 1,000,000' — that range is enormous, which suggests the number is speculative rather than reliable. If the estimate could be anywhere from a quarter million to a million, we can't confidently claim the bomb 'saved' a specific number of lives. The argument also ASSUMES there were only two options — bomb or invade — without considering the alternatives that Argument B raises (demonstration, modified terms).

Argument B's strongest evidence is the intercepted diplomatic cables showing Japan was seeking peace — if this is true and verifiable, it fundamentally weakens the case that the bomb was necessary. However, its claim about the bomb being used primarily to impress the Soviet Union is asserted but not well evidenced — the argument states it as if it's established fact, but it's actually a contested interpretation among historians. The argument would be more convincing if it cited specific historians or documents supporting this motivation.

Overall, both arguments have significant weaknesses. Argument A relies on speculative casualty figures and a false binary. Argument B makes a strong point about alternatives but overstates its case about Soviet motivation. Neither argument alone is sufficient to settle the question."

*为何属于批判性：* 学生按每段论证自身的证据条件进行评估，而非因结论而赞同/反对。他们指出了具体的强弱点、分析了隐含假设（二元选择）、评估了证据可靠性（推测性数字、有争议的阐释），并得出了有限定的评判。他们没有在“轰炸是否正当”上选边，而是在“论证质量”上给出了有理有据的判断。

**核心区别：** 浅层回答评估的是结论（我同意哪个立场？）；批判性回答评估的是证据与推理（每段论证对其结论的支撑有多扎实？）。最清晰的指标在于学生能否在自己赞同的论证中挑出弱点，并在自己反对的论证中承认强点。

### 教师追问提示

当学生产出浅层回答时使用：

1. **当学生发表观点而非评估时：** "I can see you agree with Argument A. But put that aside — pretend you disagree with it. What's the weakest part of Argument A's EVIDENCE? Can you find a problem with it even though you agree with the conclusion?"

2. **当学生因不喜欢结论而否定论证时：** "You said Argument B is weak. But look at the evidence about the intercepted cables — if Japanese leaders were already seeking peace, what does that do to Argument A's claim that the bomb was necessary? Can you evaluate the EVIDENCE separately from the conclusion?"

3. **当学生只列举证据而不评估时：** "You've identified three pieces of evidence from Argument A. But are they all equally strong? Which one is the most RELIABLE — meaning, which one could you actually verify? And which one is the most SPECULATIVE?"

4. **当学生未识别隐含假设时：** "Both arguments make assumptions that they don't prove. Argument A assumes there were only two options — bomb or invade. What other options might have existed? If those options were realistic, how does that affect Argument A's reasoning?"

5. **当学生只下结论不给推理时：** "You said Argument A is stronger. Convince me. Point to a SPECIFIC piece of evidence in A that is more reliable or relevant than the corresponding evidence in B."

6. **当学生回避复杂性时：** "You've picked a winner. But let me push you — what is the ONE strongest point the losing argument makes? If the winning argument had to respond to that point, what would they say? Can they?"

### 评估指标

在学生回答中寻找这些表明真正批判性思维的具体特征：

| 指标 | 具体表现 | 展现的批判性思维技能 |
|---|---|---|
| **证据评估** | 学生评论具体证据的“可靠性”或“可核验性”（例如 "the casualty range is too wide to be reliable"） | 分析 |
| **假设识别** | 学生点出论证未经证明就默认的前提（例如 "this assumes there were only two options"） | 推断 |
| **将证据与结论剥离** | 学生能指出自己赞同论证中的弱点，或自己反对论证中的强点 | 评估 |
| **有限定的评判** | 学生使用审慎表达："arguably"、"on balance"、"more convincing but not conclusive" | 自我调节 |
| **识别缺失信息** | 学生追问 "What would we need to know?"，而非全盘照收所给论证 | 分析 |
| **反事实推理** | 学生思考 "What if X were different?"——例如 "If the alternatives were realistic, then..." | 推断 |

**如果学生一项都未展现：** 很可能停留在观点/回忆层面。使用追问提示推动深入。

**如果学生展现 2–3 项：** 正在支架支持下参与批判性思维。可逐步撤除提示。

**如果学生展现 4 项以上：** 已能独立进行批判性思考。可挑战他们："Now write a THIRD argument that's stronger than both — what evidence and reasoning would it use?"

---

## 已知局限性

1. **批判性思维具有领域特定性（Willingham, 2007）。** 能够批判性评估历史论证的学生，未必能将该技能迁移到评估科学主张上，因为证据标准不同。本任务培养的是“特定领域内”的批判性思维——它不会自动产出泛化的“批判性思考者”。教师应当明确教授批判性思维原则如何应用于各自的具体学科。

2. **该任务要求具备足够的领域知识。** 对二战一无所知的学生，无论一般推理能力多强，都无法批判性评估关于广岛的论证。批判性思维任务必须放置在单元的恰当时机——在学生掌握了足以开展评估的知识“之后”，而非之前。过早设置批判性思维任务只会产出无知的主观臆断，而非批判性分析。

3. **学生可能将“批判性（critical）”与“负面否定（negative）”混淆。** 批判性思维意味着评估推理质量——并不意味着攻击、全盘否定或刻意唱反调。部分学生一听到“批判性思考”，就会不加评估地批评一切。批判性 vs. 浅层回答指南有助于教师识别这一模式，但仍需持续示范什么是真正的批判性评估：公正、基于证据，并愿意承认相反立场中的合理力量。
