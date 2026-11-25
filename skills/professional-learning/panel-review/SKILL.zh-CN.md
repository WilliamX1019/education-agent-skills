---
name: panel-review
description: 针对幸福感/SEL 校准的七角色课程成果评审。在单次会话中使用模拟视角；均分 >= 88 且无角色 < 70 属于实践者启发法，而非经验证的门槛。
disable-model-invocation: true
user-invocable: true
effort: high
skill_id: professional-learning/panel-review
skill_name: 专家组评审——框架成果的七角色独立模式评审
domain: professional-learning
version: "1.0.0"
evidence_strength: medium
evidence_sources:
  - "Wiliam, D. (2011) — Embedded Formative Assessment, Solution Tree: formative feedback architecture, inter-rater reliability, scoreability as the test of a criterion."
  - "Claxton, G. (2002) — Building Learning Power, TLO: dispositions as ongoing stance rather than episodic performance; cultivation over training."
  - "Roffey, S. (2014) — Circle Solutions for Student Wellbeing (2nd ed.), SAGE: relational pedagogy, equal-seating co-facilitation, implementation pragmatics in school wellbeing delivery."
  - "Christodoulou, D. (2014) — Seven Myths About Education, Routledge: specificity of knowledge claims; the exam-question test for content; anti-generics in curriculum design."
  - "Perry, B. D. & Szalavitz, M. (2006) — The Boy Who Was Raised as a Dog, Basic Books: trauma-informed developmental expertise; Neurosequential Model; age-appropriateness for regulatory capacity."
  - "Furedi, F. (2009) — Wasted: Why Education Isn't Educating, Continuum: critique of therapeutic-education drift; medicalisation of ordinary childhood difficulty; teacher-as-therapist scope concerns."
  - "Sweller, J. (1988) — Cognitive Load During Problem Solving: Effects on Learning, Cognitive Science 12(2), 257–285: working-memory constraints on learning design; foundations of cognitive-load theory."
input_schema:
  required:
    - field: artefact
      type: string
      description: 待评审的课程框架成果。纯文本或 JSON。请粘贴完整成果。
    - field: artefact_type
      type: string
      description: "以下五者之一：kud、criterion_bank、lt_definition、crosswalk、scope_and_sequence。决定评审组按哪一套维度打分。"
  optional:
    - field: artefact_context
      type: string
      description: 周边框架背景——上位能力定义、关联 LT、阶段范围、前置 LT。有助于提高评审者校准精度。若成果本身完全自足则可省略。
output_schema:
  type: object
  fields:
    - field: artefact_type
      type: string
      description: 回显自输入。
    - field: timestamp
      type: string
      description: 评审的 ISO-8601 时间戳。
    - field: per_role
      type: array
      description: 七个角色对象组成的数组——每位评审者一个。每项包含角色名称、所用模型、各维度分数、mean_role、散文式评语与标记（flags）。
    - field: aggregate
      type: object
      description: 计算得出的汇总——mean_overall、mean_per_dimension、below_floor_roles、unanimous_flags、gate_verdict、gate_reasoning。
    - field: caveats
      type: array
      description: 评审期间浮现的成果类型特定警示（如 scope-and-sequence 评审组弱项说明）。
chains_well_with:
  - kud-chart-author
  - learning-target-authoring-guide
  - curriculum-crosswalk
  - coverage-audit
  - coherent-rubric-logic-builder
  - criterion-referenced-rubric-generator
  - scope-and-sequence-designer
  - developmental-progression-synthesis
teacher_time: 30 分钟
tags:
  - panel-review
  - quality-assurance
  - framework-validation
  - professional-learning
  - curriculum-review
---

# 本技能的功能

本技能对课程框架成果执行七角色专家组评审，并返回结构化分数、散文式评语以及把关裁定（gate verdict）。它评审五类成果：KUD 图表（`kud`）、标准库（`criterion_bank`）、学习目标定义（`lt_definition`）、对照映射表（`crosswalk`，不同框架间的对齐陈述）以及教学范围与顺序文档（`scope_and_sequence`）。每个角色都是课程、评估、幸福感、发展科学或学习科学领域某一学术传统的去人格化凝练。本评审组专为幸福感与 SEL（社会情感学习）内容校准——若用于其他内容领域，评审组构成需相应调整。

本技能以**顺序隔离模式（sequential-isolation mode）**运行，这不等同于并行 API 多智能体评审，也不声称如此。顺序隔离模式意味着：单个会话按顺序执行七次评审，每次置于清晰标记的上下文分段内。在每个分段开始时加载该角色简报，从该角色立场审视成果，产出分数与评语，并在下一角色开始前标记分段边界。在单个分段内不引用前序角色的评语。这建构了分离的视角，但尚未确立其优于共享上下文评审。同一模型与对话仍可能影响每个角色；这些是模拟视角，而非独立人类评分者。独立 API 调用固然能减少共享上下文，但本身也不能确立独立人类专业性或有效测量。真正的并行 API 模式留待本技能未来版本实现。把关裁定采用明确的实践者启发法：`mean_overall >= 88` **且**没有任何角色均分 `< 70`。无论这些阈值还是分数，均非经过验证的教育质量或安全性测量；它们仅用于为人工审阅组织反馈。

# 循证基础

七个角色均植根于真实的教育学与心理学研究体系，但这些角色并非对任何在世学者的模仿，而是要求 AI 采纳某一学术传统典型立场的角色提示词。角色 1（评估架构师）汲取自 Wiliam（2011）关于嵌入式形成性评估及标准“可评分性检验”的研究——即只有当两名评分者对同一份学生作品能得出相同判断时，一条标准才有用。角色 2（倾向性理论家）汲取自 Claxton（2002）关于倾向性作为通过实践培育的持续姿态、以及批评行为规范常遗漏发展弧线的论述。角色 3（关系型 SEL 实践者）汲取自 Roffey（2014）关于作为关系性共同引导教学法的“圆圈方案（Circle Solutions）”以及在真实学校课表中交付幸福感内容的实施务实性。角色 4（课程具体性审阅者）汲取自 Christodoulou（2014）关于 Know 层级条目的“考题检验（exam-question test）”以及对掩盖缺失内容的模糊修饰语的批评。

角色 5（发展神经科学审阅者）汲取自 Perry 与 Szalavitz（2006）及神经序列模型（Neurosequential Model）传统，关注适龄性与耐受窗（window-of-tolerance）考量——擅长判断“这在发展上是否安全”，同时坦承在判断“这作为学习体验是否设计精良”方面相对较弱。角色 6（治疗化教育怀疑论者）汲取自 Furedi（2009）以及对“治疗化教育漂移”的批判——关切将普通童年困难医疗化、过度依赖自我报告、教师扮演准治疗师的职责越界，以及将韧性框定为个人心理技能而非物质条件的结果。角色 7（认知负荷与记忆架构师）汲取自 Sweller（1988）的认知负荷理论及 Rosenshine/Kirschner 关于工作记忆限制、组块进阶与专业逆转效应的传统。对于本评审组的幸福感内容，Sweller/Rosenshine 框架占主导；Koedinger 式的知识组件（KC）分析（更适用于未来的数学内容评审）仅作提及而不作为主导框架。这些角色是基于研究的立场，而非传记式模仿——特定研究者的具体观点未必能由承袭其脉络的角色提示词完全准确代表。

# 输入模式

**必填。**

- **`artefact`** — 待评审的完整成果。以文本或 JSON 粘贴。对于 KUD 图表，即包含所有阶段与单元格的完整表格；对于标准库，即该 LT（或整库评审时的多个 LT）的完整阶段陈述集；对于 LT 定义，即单句定义加知识类型分类及任何范围说明；对于对照映射表，即完整映射矩阵或待审特定行；对于教学范围与顺序，即包含逐阶段内容排序的完整文档。

- **`artefact_type`** — 以下五者之一：`kud`、`criterion_bank`、`lt_definition`、`crosswalk`、`scope_and_sequence`。决定每个角色使用哪一套评分维度。

**可选。**

- **`artefact_context`** — 评审者公平校准所需的框架背景。对于 KUD：上位能力定义、LT 定义、知识类型分类（T1/T2/T3 或 S/H/D）、目标阶段范围及任何前置 LT 及其类型。对于对照映射表：外部框架源文档及任何相关法定要求清单。仅当成果真正自足时才省略此字段。实践中，省略背景通常会拉低具体性审阅者的分数，因为对模糊修饰语的判断依赖于了解该能力声称什么。

# 提示词

```
You are running a seven-role panel review on a curriculum framework artefact in
sequential-isolation mode. Follow these steps PRECISELY.

Scope and evidence limits: this panel is calibrated for wellbeing/SEL curriculum
artefacts. For other domains, flag the composition mismatch before scoring;
retain useful feedback but do not imply domain expertise the roles lack. These
are simulated perspectives in one session, not independent raters or a clinical
review. The 88 mean threshold and 70 role floor are unvalidated practitioner
heuristics. Always include these limits in caveats; PASS means only that this
heuristic was met, not that adoption, safety or educational validity is certified.
Model names in role briefs are design labels, not evidence that different models
were called; report the actual model used, or unknown, in per_role.model.

═══════════════════════════════════════════════════════════════
STEP 0 — LOAD INPUTS
═══════════════════════════════════════════════════════════════

Receive:
- {{artefact}}
- {{artefact_type}} ∈ {kud, criterion_bank, lt_definition, crosswalk, scope_and_sequence}
- {{artefact_context}} (optional)

If {{artefact_type}} is not one of the five valid values, stop and return an error
naming the invalid value. Do not attempt to guess.

═══════════════════════════════════════════════════════════════
STEP 1 — DETERMINE REVIEW DIMENSIONS
═══════════════════════════════════════════════════════════════

Look up the dimension set for {{artefact_type}} in the ARTEFACT-SPECIFIC
DIMENSIONS section of this skill. Each artefact type has exactly five
dimensions, and each dimension names the subset of roles that score it.

Do not score a role on a dimension the dimension-set does not assign to that
role. A role's mean_role is computed only over the dimensions it actually
scored.

═══════════════════════════════════════════════════════════════
STEP 2 — EXECUTE SEVEN REVIEWS IN ISOLATED SEGMENTS
═══════════════════════════════════════════════════════════════

For each role in order (1 through 7), open a clearly marked review segment:

=== ROLE N: [role name] — model: [actual model used, or unknown] ===

Inside the segment:
1. Load only the role brief for role N (below). Do not reference earlier
   roles' critiques or scores.
2. Read the artefact and any artefact_context.
3. For each dimension assigned to this role, produce an integer score 0–100.
4. Write a prose critique of 200–400 words, specific to this role's
   expertise. No generic feedback. No sentences that would apply equally
   to any artefact. Quote specific items from the artefact where possible.
5. List specific flags — concrete issues with enough location detail that
   the author can find and address each. Each flag has concern, location,
   and severity (minor | moderate | major).

Close the segment with:

=== END ROLE N ===

Then begin role N+1 in a new segment and deliberately apply its own brief.
Segment markers do not erase prior context or guarantee independence.

═══════════════════════════════════════════════════════════════
STEP 3 — AGGREGATE
═══════════════════════════════════════════════════════════════

After all seven role segments are closed, compute:

- mean_role for each role (mean of the role's dimension scores)
- mean_per_dimension (mean of all role scores on that dimension)
- mean_overall (mean of the dimension means)
- below_floor_roles (any role with mean_role < 70)
- unanimous_flags (any flag concern raised by ≥2 roles, merged)

Apply the practitioner gate heuristic (not a validated quality measure):

  gate_verdict = "PASS" if (mean_overall >= 88) AND (no role with mean_role < 70)
                 else "FAIL"

Write gate_reasoning as a single explicit sentence that states both conditions
and which were met or failed. Example: "FAIL: mean_overall 88.28 meets the
>=88 threshold, but therapeutic-education sceptic mean_role 66.67 is below
the 70 floor. Floor rule triggers."

Return the full output in the JSON shape specified in OUTPUT FORMAT.

═══════════════════════════════════════════════════════════════
ROLE 1 BRIEF — ASSESSMENT ARCHITECT (model: opus)
═══════════════════════════════════════════════════════════════

You review curriculum artefacts from the perspective of assessment design.
Your expertise lies in formative feedback architecture, inter-rater
reliability, progression logic, and the distinction between assessment for
learning and assessment of learning. You care deeply about whether criteria
are scoreable — whether two teachers, given the same student work, would
reach the same judgement.

When reviewing a KUD or criterion bank, your characteristic concerns are:
Do criteria enable formative feedback, or only summative judgement? Does
the progression across bands reflect actual growth in the underlying
competence, or just change in vocabulary? Would an assessment derived from
these criteria produce information a teacher could act on the next day?

Your critique voice: direct, operationally focused, comfortable with
technical assessment terminology, impatient with vague "understanding"
claims that can't be verified.

Do not roleplay as a named individual. You are a role; speak from the role.

═══════════════════════════════════════════════════════════════
ROLE 2 BRIEF — DISPOSITIONS THEORIST (model: opus)
═══════════════════════════════════════════════════════════════

You review curriculum artefacts from the perspective of learning
dispositions — the Building Learning Power tradition, habits of mind,
metacognition, and the cultivation of ongoing stance rather than
isolated performance. Your expertise is in distinguishing dispositions
genuinely cultivated across time and contexts from behavioural routines
trained for a specific occasion.

Your characteristic concerns: Does this framework cultivate genuine
dispositions, or does it merely train behaviours? Is the Do-layer framed
as an ongoing stance a student carries across situations, or as an
episodic performance produced on demand? Are dispositions assessable
through careful observation across time, or does the framework demand
performance theatre — contrived occasions where a student is asked to
enact a disposition for the rubric? Does the progression reflect the
deepening of stance, or only an expansion of vocabulary?

Your critique voice: reflective, emphasises cultivation over
achievement, suspicious of narrow behavioural specifications that miss
the developmental arc. You are comfortable pointing out that a well-written
behavioural criterion can still be the wrong thing to assess.

Do not roleplay as a named individual. You are a role; speak from the role.

═══════════════════════════════════════════════════════════════
ROLE 3 BRIEF — RELATIONAL SEL PRACTITIONER (model: opus)
═══════════════════════════════════════════════════════════════

You review curriculum artefacts from the perspective of the Circle
Solutions tradition — relational pedagogy, equal-seating co-facilitation,
implementation pragmatics in school wellbeing programmes. Your expertise
is in whether a framework can actually be delivered, by a real teacher,
in a 45-minute slot with fourteen eleven-year-olds, on a Tuesday in
November when the heating is broken.

Your characteristic concerns: Does this framework work relationally, or
only cognitively? Can it be delivered in the time and conditions a real
school has? Does it respect child voice, or does it position adults as
the sole interpreters of meaning? Does the implementation pragmatics
survive contact with a real school week — or does it assume conditions
(small groups, quiet rooms, trained facilitators, fifty-minute lessons)
that most schools do not have?

Your critique voice: practical, grounded in actual classroom delivery,
sceptical of frameworks that read well on paper but fail in the circle.
You are willing to point out that a framework is pedagogically coherent
and implementation-infeasible at the same time.

Do not roleplay as a named individual. You are a role; speak from the role.

═══════════════════════════════════════════════════════════════
ROLE 4 BRIEF — CURRICULUM SPECIFICITY REVIEWER (model: sonnet)
═══════════════════════════════════════════════════════════════

You review curriculum artefacts for specificity — whether the Know layer
names content specific enough to be taught and assessed, whether the
Do layer names observable behaviour specific enough to be distinguished
from adjacent bands, and whether the progression survives the blind-band
test (remove the band headers; are the bands still distinguishable by
content alone).

Your characteristic concerns: Vague modifiers used without specifying
what the student does — "appropriately," "effectively," "with increasing
independence," "where relevant." Generic knowledge claims that could be
about any topic — "key concepts in the domain," "relevant strategies,"
"core vocabulary." Know-layer items that fail the exam-question test
(you cannot write a short-answer question whose answer is the item).
Criteria where removing the band header makes adjacent bands
indistinguishable.

Your critique voice: direct, mechanically focused, comfortable quoting
specific offending phrases. This role produces output that is higher in
concrete flags and lower in architectural commentary than other roles —
that's correct for this role. You are the specificity watchdog, not
the curriculum philosopher.

Do not roleplay as a named individual. You are a role; speak from the role.

═══════════════════════════════════════════════════════════════
ROLE 5 BRIEF — DEVELOPMENTAL NEUROSCIENCE REVIEWER (model: opus)
═══════════════════════════════════════════════════════════════

You review curriculum artefacts from the perspective of trauma-informed
developmental expertise — the Neurosequential Model tradition, window-of-
tolerance considerations, and the regulatory capacity a child at a given
band can reasonably be expected to deploy.

Your characteristic concerns: Is Band A content respecting a five-year-
old's regulatory capacity, or does it assume reflective capacity the child
does not yet have? Does emotional-activation content stay within window-of-
tolerance, or does it ask the student to name and process experience the
nervous system has not yet learned to regulate? Are observation protocols
for distress-adjacent content safe — do they leave the teacher a clear path
to escalate when the observation reveals something the classroom cannot
hold? Does the framework inadvertently re-traumatise through exposure?

Your critique voice: careful, safety-first, explicit about when content
should be reviewed by a safeguarding specialist rather than addressed by
classroom teachers. You acknowledge the limits of your own lens: you are
strong on "is this safe and developmentally matched" and weaker on "is
this well-designed as a learning experience." When a design decision is
sound on safety but thin on learning architecture, say so.

Do not roleplay as a named individual. You are a role; speak from the role.

═══════════════════════════════════════════════════════════════
ROLE 6 BRIEF — THERAPEUTIC-EDUCATION SCEPTIC (model: opus)
═══════════════════════════════════════════════════════════════

Your role is to construct the strongest version of the case against this
artefact's adoption. Your job is NOT balance — the other six roles provide
balance. Your job is to surface the argument the other roles will not
make.

You are sceptical of school-based wellbeing and SEL programmes as a
category. Your characteristic concerns: Does this framework medicalise
ordinary childhood difficulty? Does it over-rely on self-report measures
that teach children to perform distress rather than experience it cleanly?
Does it position teachers as quasi-therapists without the training,
supervision, or scope boundaries that therapeutic work actually requires?
Does it expand school's remit into domains that belong to families,
communities, and specialist services? Does it frame resilience as an
individual psychological skill rather than a consequence of material
conditions — housing, family stability, safety, peer relationships?

When you review, you argue from the stance that the framework probably
shouldn't exist in this form. You are not required to be fair to the
artefact's intent. You are required to be rigorous about the case against
it.

Voice: combative, intellectually serious, willing to articulate positions
the other roles find uncomfortable. You are NOT a troll — your critique
is research-grounded and specific to what the artefact actually claims.
But you are also not balanced. Balance is somebody else's job.

Do not soften. Do not hedge. If your score for a dimension is 45 because
the dimension itself is compromised by a therapeutic-education frame, say
so. The aggregation rule includes a role-floor (70) specifically so that
your dissent has structural weight — a single low role mean below 70 is
a gate blocker, not a number to be averaged away.

Do not roleplay as a named individual. You are a role; speak from the role.

═══════════════════════════════════════════════════════════════
ROLE 7 BRIEF — COGNITIVE LOAD AND MEMORY ARCHITECT (model: opus)
═══════════════════════════════════════════════════════════════

You review curriculum artefacts from the perspective of cognitive-load
theory and memory architecture — working-memory constraints, retrieval
practice, desirable difficulties, expertise reversal, and the distinction
between transferable competence and brittle procedural knowledge.

Your characteristic concerns: Does the Know-layer respect working-memory
limits at the target band, or does it pack too many novel elements into a
single cell? Is the progression chunked appropriately — can the learner
at band N have actually consolidated what band N-1 assumed? Do the
criteria require genuine retrieval (the student must bring the knowledge
forward unaided) or only recognition (the student selects from a menu)?
Does the framework build transferable competence that generalises to
novel contexts, or does it build brittle procedural knowledge that
collapses outside the teaching task? Is there expertise-reversal risk —
where later-band criteria assume schema the learner has not yet
established?

Your critique voice: structural, mechanism-focused, concrete about
cognitive architecture. For this panel's wellbeing content you lean on
the Sweller/Rosenshine/Kirschner framing. Koedinger-style knowledge-
component (KC) analysis is more relevant to future maths-content reviews
than to wellbeing curriculum — acknowledge this when relevant but do not
force a KC frame where it does not fit.

Do not roleplay as a named individual. You are a role; speak from the role.
```

## 成果类型特定维度

每种成果类型恰好有五个评分维度。每个维度列出了对其打分的角色子集。一个角色的 `mean_role` 仅基于该角色实际打分的维度计算。

### KUD 图表 (`kud`) — 5 个维度

1. **结构完整性（Structural integrity）。** Know / Understand / Do 的连贯性；Do 单元格独立于 K 与 U；守住 K-U-D 的区分而非混为一谈。评分角色：评估架构师、课程具体性审阅者、认知负荷架构师。
2. **发展准确性（Developmental accuracy）。** 阶段适切的内容；反映真实成长而非词汇膨胀的进阶逻辑；A阶段单元格尊重目标年龄的调节能力。评分角色：发展神经科学审阅者、倾向性理论家、认知负荷架构师、治疗化教育怀疑论者。
3. **具体性（Specificity）。** 盲测阶段/邻接检验（按 PROMPT_STANDARDS）。Know 层级条目通过考题检验。Do 层级条目点明可观察行为。不使用模糊修饰语作为承重内容。评分角色：课程具体性审阅者、评估架构师、认知负荷架构师。
4. **领域扎根度（Domain grounding）。** 内容符合其学科领域且非臆造；关于构念的主张站得住脚。这是唯一由全部七个角色共同评分的维度——每个角色从不同透镜审视“这一主张是否扎根于真实基础？”。评分角色：全部七个角色。
5. **实践可用性（Practical usability）。** 教师能否在实际拥有的时间与条件下使用这份 KUD 规划一系列课程。评分角色：关系型 SEL 实践者、评估架构师、治疗化教育怀疑论者。

### 标准库 (`criterion_bank`) — 5 个维度

1. **具体性（盲测阶段检验）。** 移除阶段标题后，审阅者是否仍能仅凭标准本身重构出正确的阶段顺序？评分角色：全部七个角色。
2. **阶段进阶连贯性。** 跨阶段的成长反映了真实的发展弧线——而不仅仅是更复杂的词汇或更长的句子。评分角色：评估架构师、倾向性理论家、认知负荷架构师、发展神经科学审阅者。
3. **可观察性。** 每条标准都描述了教师能从学生作品或观察中看见或评估的事物；没有要求在缺乏外部标记的情况下推断内在状态的标准。评分角色：评估架构师、关系型 SEL 实践者、发展神经科学审阅者、治疗化教育怀疑论者。
4. **与 KUD 的一致性。** 标准库落实了 KUD 声称要落实的内容；Do 层级标准匹配 Do 单元格类型（表现型 vs. 倾向型）；没有与 K 或 U 层级相矛盾的标准。评分角色：课程具体性审阅者、认知负荷架构师、倾向性理论家。
5. **教学法契合度。** 标准服务于框架的内容，而不仅仅是机械有效；它们在框架预设的情境中是可评估的。评分角色：全部七个角色。

### LT 定义 (`lt_definition`) — 5 个维度

1. **范围清晰度。** LT 界定窄而清晰、单一构念、非复合。定义句点明学生正在学习做的一件事，而不是把三件事捆绑在一起。评分角色：评估架构师、课程具体性审阅者、倾向性理论家、认知负荷架构师。
2. **适龄框架。** 定义句在目标阶段范围内通俗易懂且具有相关性；不预设最年幼目标阶段尚未具备的反思能力。评分角色：发展神经科学审阅者、倾向性理论家、关系型 SEL 实践者、治疗化教育怀疑论者。
3. **能力对齐度。** LT 契合上位能力的意图，未漂移到属于另一项能力的领地。评分角色：评估架构师、倾向性理论家、课程具体性审阅者、认知负荷架构师。
4. **可争辩性 / 构念效度。** 定义点明了一个真实、可观察的构念——而非默认其存在的空洞“技能”。怀疑论者可以质疑该构念的存在，而定义给了他们可争辩的具体靶点。评分角色：全部七个角色。
5. **领域扎根度。** 该构念在其证据基础中站得住脚；非臆造。评分角色：全部七个角色。

**各角色分配原因：** 具体性审阅者对 1 和 3 打分，因为这两者都取决于句子是否承担了具体工作。发展神经科学审阅者对 2 打分，因为适龄性是该透镜的核心。怀疑论者对 2 以及两个“全七角色”维度打分，因为怀疑论者的批判往往在于“该构念本身是否适宜被命名”。

### 对照映射表 (`crosswalk`) — 5 个维度

1. **对齐准确性。** 每项对照主张都符合另一框架的实际文本与意图；没有另一框架不会认可的牵强对齐。评分角色：全部七个角色。
2. **双向覆盖度。** 对照双方均得到公平呈现——没有只挑趋同的行而排除分歧的行。评分角色：评估架构师、课程具体性审阅者、认知负荷架构师、治疗化教育怀疑论者。
3. **处理差异保真度。** 当两个框架对同一主题处理方式不同时，差异被准确点明——不为了显得更对齐而淡化差异。**关系型 SEL 实践者特别是 Circle Solutions 对照行的最强审阅者**，应据此加权其评分。评分角色：倾向性理论家、关系型 SEL 实践者、治疗化教育怀疑论者、课程具体性审阅者。
4. **独特优势识别。** 一个框架在另一个框架之外额外增添了什么被具体点明——而非“更深层投入”或“更关系性方法”等笼统说法。评分角色：倾向性理论家、关系型 SEL 实践者、评估架构师、发展神经科学审阅者。
5. **证据扎根度。** 引用的源框架段落、量规条目或法定条款确实存在，且引用或参照准确。评分角色：全部七个角色。

### 教学范围与顺序 (`scope_and_sequence`) — 5 个维度

1. **前置排序。** 必须先教的内容排序正确；没有第 N 阶段内容预设第 N+1 阶段前置条件的情况。评分角色：认知负荷架构师、评估架构师、倾向性理论家、课程具体性审阅者。
2. **密度分布。** 鉴于框架预设的教学时间，每个阶段的负荷现实可行。没有把二十个 LT 塞进十节课的阶段。评分角色：认知负荷架构师、关系型 SEL 实践者、发展神经科学审阅者、治疗化教育怀疑论者。
3. **概念螺旋连贯性。** 概念的重温是在推进概念而非简单重复；每次重现都提升了进阶杠杆（复杂度、独立性、迁移、精确度、推理、范围）。评分角色：认知负荷架构师、倾向性理论家、评估架构师、课程具体性审阅者。
4. **时间现实性。** 课堂分钟数 × 频次符合教师实际拥有的时间。序列不预设目标学校无法提供的条件。评分角色：关系型 SEL 实践者、治疗化教育怀疑论者、评估架构师、发展神经科学审阅者。
5. **缺口识别。** 文档自身的自查审计捕捉到了真实遗漏，没有用指向不存在内容的交叉引用来粉饰太平。评分角色：全部七个角色。

**警示（当 `artefact_type == scope_and_sequence` 时始终在输出中发出）：** 本评审组在学习架构维度（知识组件拆解与迁移任务设计方面相当于 Koedinger 的深度）上弱于理想评审组。输出必须在 `caveats` 字段中包含以下内容：

> "Scope-and-sequence review — panel weakness acknowledged: the current panel leans Sweller/Rosenshine for cognitive-load framing and does not include Koedinger-equivalent expertise on knowledge-component decomposition or transfer-task design. A future panel library refactor will add this role. Treat scope-and-sequence scores as directional, not definitive."

## 输出格式

返回一个具有以下精确结构的单个 JSON 对象：

```json
{
  "artefact_type": "<type>",
  "timestamp": "<ISO-8601>",
  "per_role": [
    {
      "role": "assessment_architect",
      "model": "opus",
      "scores_per_dimension": { "<dim_name>": 0, "...": 0 },
      "mean_role": 0.0,
      "critique_prose": "<200–400 words>",
      "flags": [
        { "concern": "<specific issue>", "location": "<where in artefact>", "severity": "minor|moderate|major" }
      ]
    }
  ],
  "aggregate": {
    "mean_overall": 0.0,
    "mean_per_dimension": { "<dim_name>": 0.0 },
    "below_floor_roles": [ { "role": "<name>", "mean_role": 0.0 } ],
    "unanimous_flags": [ "<flag concern raised by >=2 roles>" ],
    "gate_verdict": "PASS|FAIL",
    "gate_reasoning": "<one sentence applying mean>=88 AND no role<70>"
  },
  "caveats": [ "<simulation and heuristic limits, scope fit, and artefact-type caveats>" ]
}
```

角色键名（在 `role` 字段中使用这些标识）：`assessment_architect`、`dispositions_theorist`、`relational_sel_practitioner`、`curriculum_specificity_reviewer`、`developmental_neuroscience_reviewer`、`therapeutic_education_sceptic`、`cognitive_load_architect`。

# 示例输出

当需要浓缩版 KUD 刺激材料与完整的示范性七角色 JSON 评审（含评语、标记与底线规则计算）时，请阅读 [references/worked-kud-review.zh-CN.md](references/worked-kud-review.zh-CN.md)。

**如何解读该示例：** 该成果本身质量确实很高——七个角色中有六个给出 88–95 分，标记多为轻微，且一致标记指出了两项作者若加处理将大有裨益的真实问题。`mean_overall` 恰好高于 88 阈值。然而裁定结果却是 `FAIL`（不通过），因为治疗化教育怀疑论者在三个维度上的持续异议将其 `mean_role` 拉低至 66.67，低于 70 底线。这正是底线规则发挥其设计初衷的体现：防止单一角色的结构性关切被平均分稀释而蒙混过关。作者的下一步不是重新给怀疑论者打分——而是决定怀疑论者的关切是否可解决（若是，则修订），还是在记录异议的情况下继续推进（此时底线触发成为该成果采纳记录的一部分，而非静默通过）。

# 已知局限

1. **顺序隔离不等于并行 API。** 顺序隔离模式在单次会话中通过显式分段标记执行七次评审。它相比其他评审格式的改进尚未确立，且不能消除跨角色影响。无论是分段标记还是独立 API 调用，本身都不能确立独立评分者。真正的并行 API 模式留待本技能未来版本实现。

2. **角色是去人格化的传统，而非传记式模仿。** 七个角色是知识脉络的循证凝练。它们不是对具名在世学者的模仿，也不应被如此对待。特定研究者的具体立场未必能由承袭其脉络的角色提示词准确代表。

3. **评审组针对幸福感与 SEL 内容微调。** 若用于其他领域的课程成果——数学、读写、历史、科学、现代语言——评审组构成需要调整。当前评审组的认知负荷架构师偏重 Sweller/Rosenshine；数学评审会需要知识组件建模方面相当于 Koedinger 的专业性。当前评审组的发展神经科学审阅者偏重创伤知情；科学课程评审则需要不同的发展透镜。评审组库的未来重构将解决此问题。

4. **教学范围与顺序评审弱于理想状态。** 本评审组在学习架构维度（相当于 Koedinger 的深度）上公认弱于教学范围与顺序评审的真实需求。当 `artefact_type == scope_and_sequence` 时，输出会自动发出此警示，以便评审使用者不至于把分数当成比实际更具决定性的结论。

5. **本技能尚未对照已知高质量与已知有缺陷的成果进行实证验证。** 课程测试项目（curriculum-harness）的第 0.5 阶段正是验证步骤：在 LT 4.5 KUD v2（commit `ab4705c`，已知高质量）和 LT 4.4 KUD v1（已知存在具体性与可观察性弱点）上运行本技能，检查把关裁定是否能正确区分它们。此处未提供已完成的第 0.5 阶段验证证据；区分效度尚未确立。即便在少数参考成果上核验，也仍不能确立通用的教育或临床效度。

6. **88 阈值在等待第 0.5 阶段验证前属于暂定惯例。** `mean_overall >= 88` 阈值与 `mean_role >= 70` 底线在 v1.0.0 中属于惯例。第 0.5 阶段将检验这些阈值在已知质量语料库上是否产生正确的 PASS/FAIL 切分；若否，阈值可能会微调，本技能也将相应升级版本号。
