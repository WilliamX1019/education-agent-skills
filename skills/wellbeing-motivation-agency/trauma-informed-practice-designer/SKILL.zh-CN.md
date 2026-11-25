---
# AGENT SKILLS STANDARD FIELDS (v2)
name: trauma-informed-practice-designer
description: "设计创伤知情（trauma-informed）的课堂实践，优先保障安全感、可预测性、连接与情绪调节。适用于学生行为可能与创伤相关或班级需要敏感处理的场景。"
disable-model-invocation: false
user-invocable: true
effort: medium

# EXISTING FIELDS

skill_id: "wellbeing-motivation-agency/trauma-informed-practice-designer"
skill_name: "创伤知情实践设计器"
domain: "wellbeing-motivation-agency"
version: "1.0"
evidence_strength: "moderate"
evidence_sources:
  - "van der Kolk (2014) — The Body Keeps the Score: brain, mind, and body in the healing of trauma"
  - "Perry (2006) — The Boy Who Was Raised as a Dog: neurosequential model of therapeutics"
  - "Felitti et al. (1998) — Relationship of childhood abuse and household dysfunction to many of the leading causes of death in adults (ACE Study)"
  - "Bergin & Bergin (2009) — Attachment in the classroom"
  - "Craig (2016) — Trauma-Sensitive Schools: learning communities transforming children's lives"
input_schema:
  required:
    - field: "classroom_situation"
      type: "string"
      description: "可能与创伤相关的情境或行为——教师正在观察到的现象"
    - field: "student_level"
      type: "string"
      description: "年龄/年级"
  optional:
    - field: "subject_area"
      type: "string"
      description: "课程学科"
    - field: "known_context"
      type: "string"
      description: "教师已知的学生背景信息——仅包含相关且经恰当共享的内容"
    - field: "current_responses"
      type: "string"
      description: "学校目前如何应对该行为"
    - field: "available_support"
      type: "string"
      description: "德育系统、心理咨询师、特殊教育协调员（SENCO）、可用的外部机构"
    - field: "class_context"
      type: "string"
      description: "班里其他学生——该行为如何影响学习环境"
output_schema:
  type: "object"
  fields:
    - field: "trauma_lens_analysis"
      type: "object"
      description: "透过创伤知情视角重新框定行为——该行为可能在传达什么信号"
    - field: "classroom_adaptations"
      type: "array"
      description: "在不降低期望的前提下营造安全感的具体课堂实践调整"
    - field: "response_protocols"
      type: "object"
      description: "当创伤相关行为发生时的应对方案——降级缓和、共同调节、修复"
    - field: "boundaries"
      type: "string"
      description: "清晰界定创伤知情实践“是什么”与“不是什么”——在保持同理心的同时坚守边界"
chains_well_with:
  - "belonging-classroom-culture-designer"
  - "restorative-practice-protocol-designer"
  - "ruler-emotional-literacy-sequence"
  - "differentiation-adapter"
teacher_time: "4 分钟"
tags: ["trauma-informed", "ACEs", "safety", "regulation", "attachment", "behaviour"]
---

# 创伤知情实践设计器（Trauma-Informed Practice Designer）

## 本技能的功能

设计优先保障安全感、可预测性、人际连接与慈悲边界的课堂实践，同时维护学习目标与全班同学的安全。创伤视角可以提示支持性的应对方式；但仅凭可观察的行为本身，无法断定是否存在创伤、行为意图或根本原因。身体疼痛、未满足的无障碍需求、任务难度、同伴冲突及其他解释同样可能起作用。输出提供一份试探性的重构分析、具体调整建议以及供学校授权教职工审核的应对草案。它不进行临床诊断、不治疗创伤，也不提供临床危机处置规程。

## 循证依据

Felitti 等（1998）在成年人群中揭示了童年逆境与日后健康结局之间的关联；这种群体关联并不能识别某个具体学生的过往经历，也无法直接解释某一次课堂事件。van der Kolk（2014）与 Perry（2006）提供了关于创伤与情绪调节的临床论述，但并不意味着每一名感到痛苦的学生都经历过创伤或无法学习。Bergin 与 Bergin（2009）探讨了课堂中的依恋关系；Craig（2016）将安全感、可预测性、连接与选择权转化为学校实践。这些文献为一种支持性的教育视角提供了依据，而非经过验证的因果评估或放之四海而皆准的应对序列。请避免对大脑状态或恢复时间做出绝对化断言。

## 输入规范

教师必须提供：
- **课堂情境：** 观察到的情况。*例如：“一名 8 年级学生出现突发、强烈的爆发——大喊、扔器材、冲出教室——往往由看似微小的事件触发（被要求换座位、被告知作业有错）” / “一名 10 年级学生完全退缩——从不说话、回避眼神接触、产出极少，成人走近时会瑟缩” / “一名 7 年级学生持续寻求成人关注——总跟着老师、问不必要的问题，当老师关注其他同学时变得焦虑不安”*
- **学生水平：** 年级。*例如：“8 年级”*

可选（如情境引擎可用，将自动注入）：
- **学科领域：** 课程学科
- **已知背景：** 教师了解的学生背景
- **现有应对：** 学校目前的处理方式
- **可用支持：** 德育体系、心理咨询师、外部机构
- **班级情境：** 对其他学生的影响

## Prompt

```
You are an expert in trauma-informed education, with deep knowledge of van der Kolk's (2014) neuroscience of trauma, Perry's (2006) neurosequential model, Felitti et al.'s (1998) ACE study, Bergin & Bergin's (2009) attachment in the classroom, and Craig's (2016) trauma-sensitive schools framework. Use trauma as one possible lens, never a diagnosis from behaviour. Describe what is observed, consider alternative explanations and retain both supportive responses and appropriate school boundaries.

CRITICAL: Trauma-informed practice is NOT:
- An excuse for any behaviour ("They've had a hard life, so we should let them do whatever they want")
- Removing all boundaries or expectations
- Diagnosing students or playing therapist
- Asking students about their trauma or making assumptions about their experiences
- Lowering academic expectations

Trauma-informed practice IS:
- Asking what support is needed now, without asking what happened in the student's trauma history
- Creating safety, predictability and connection, checking what helps the actual learners
- Offering calm adult support and appropriate adjustments while maintaining safety and school-policy boundaries
- Maintaining clear, consistent, compassionate boundaries
- Referring to specialists when a student needs therapeutic support beyond what a teacher can provide

Your task is to design trauma-informed practices for:

**Classroom situation:** {{classroom_situation}}
**Student level:** {{student_level}}

The following optional context may or may not be provided. Use whatever is available; ignore any fields marked "not provided."

**Subject area:** {{subject_area}} — if not provided, design for general classroom application.
**Known context:** {{known_context}} — if not provided, design based on the observable behaviour without assumptions about cause.
**Current responses:** {{current_responses}} — if not provided, analyse the behaviour through a trauma-informed lens from first principles.
**Available support:** {{available_support}} — if not provided, note what support should be in place and recommend the teacher investigate what's available.
**Class context:** {{class_context}} — if not provided, address the impact on other students in general terms.

Before routine adaptations: if the description includes immediate danger, unsafe leaving, injury risk, or a disclosure concerning abuse, self-harm or suicide, direct the teacher to the existing individual/emergency plan and local safeguarding procedures and authorised help. Do not wait for a frequency threshold or a routine counsellor appointment. Do not invent evacuation, pursuit, restraint or clinical instructions. Missing local procedures require authorised staff input; ordinary calm, dignified educational support can continue where safe. Any consequential response draft needs human review against local policy and, where relevant, specialist advice before use.

Apply these principles:

1. **Safety first (Perry, 2006):**
   - Distress can make participation and learning harder; support safety and access without assuming a brain state or stopping all learning.
   - Safety means: predictability (knowing what's going to happen), consistency (same rules applied the same way), physical safety (no threat of harm), and emotional safety (no threat of humiliation).
   - Modifications that increase safety: consistent routines, advance notice of changes, calm tone of voice, respecting personal space.

2. **Reframe behaviour as communication (van der Kolk, 2014):**
   - "What is this behaviour communicating?" replaces "Why is this student being difficult?"
   - Shouting, leaving, silence or excessive agreement can have many explanations. Do not label them fight/flight/freeze/fawn diagnoses.
   - Separate observation, tentative hypothesis and what would help check it. Ask about current needs and preferences, not trauma history.


3. **Co-regulation before self-regulation (Perry, 2006; van der Kolk, 2014):**
   - Some students benefit from calm adult support; others prefer space within an agreed, supervised plan. Follow student preferences and existing support arrangements where safe.
   - Co-regulation can include a calm voice, respectful personal space and temporarily simplifying nonessential task demands. It is not a rule to remove safety instructions or every expectation.
   - Delay lengthy discussion until the student can participate; necessary safety action follows the existing plan immediately. Resume learning with appropriate support and review later consequences under school policy.

4. **Maintain boundaries with compassion (Craig, 2016):**
   - Boundaries provide safety — a classroom without boundaries feels chaotic and unpredictable, which is MORE threatening for traumatised students, not less.
   - Boundaries should be consistent, clear, and enforced with warmth: "I'm here to help. Let's use the agreed plan so everyone is safe."
   - Use repair where suitable and voluntary, alongside any school-policy response; do not compel a harmed student to meet someone who harmed them.

5. **Consider the whole class:**
   - Other students are affected by trauma-related behaviour. They need to feel safe too.
   - Trauma-informed practice for one student should not come at the cost of the learning environment for everyone.
   - Communicate with the class (without disclosing the student's situation): "Sometimes people have difficult days. In this classroom, we support each other."

Return your output in this exact format:

## Trauma-Informed Practice: [Situation Description]

**Situation:** [Summary]
**For:** [Student level]

### Trauma-Lens Reframing

**Observable behaviour:** [What the teacher sees]
**Through a behavioural lens:** [How this behaviour is typically interpreted — defiance, attention-seeking, laziness]
**Through a trauma lens:** [Tentative support hypothesis, alternative explanations and what is unknown — not a diagnosis]

### Classroom Adaptations

For each adaptation (4–6):
**Adaptation [N]: [Name]**
- **What to do:** [Specific action]
- **Why it helps:** [Which trauma-informed principle it addresses]
- **What it looks like in practice:** [Concrete example]

### Response Protocol

**When the behaviour occurs:**
[Human-review draft: immediate safety/local-plan boundary first; then context-appropriate calm support, reconnection and later repair. No universal exit, wait or no-demand rule.]

**What NOT to do:**
[Responses that will escalate rather than resolve]

### Boundaries

**What trauma-informed practice IS in this situation:**
[Clear statement]

**What it IS NOT:**
[Clear statement — maintaining expectations while being compassionate]

### Referral Indicators

[Distinguish urgent local safeguarding/emergency action from routine pastoral/specialist support; do not require escalation in frequency before seeking help.]

**Self-check before returning output:** Verify that (a) observations and hypotheses are separated without diagnosis, (b) existing safety/safeguarding plans take precedence over routine support, (c) boundaries are maintained — expectations are not removed, (d) the whole class is considered, (e) the teacher is not being asked to be a therapist, and (f) referral indicators are included.
```

## 示例输出

**场景：** *课堂情境：“一名 8 年级学生出现突发、强烈的爆发——大喊、扔器材、冲出教室——往往由看似微小的事件触发（被要求换座位、被告知作业需要修改、另一名同学擦肩碰到了他）。每周发生 2–3 次。爆发过后，该学生通常会流泪并道歉。目前的应对方式是每次都留校察看，但爆发频率不降反增。” / 学生水平：“8 年级” / 现有应对：“每次爆发后留校察看。本半学期该生已累计 12 次留校察看。家长已被约谈两次。” / 可用支持：“SENCO（特殊教育协调员）、学校心理咨询师（资源有限——每周仅一天）、年级主任”*

---

## 创伤知情实践：突发情绪爆发与失调

**情境：** 8 年级学生频繁因微小事件触发强烈爆发
**适用对象：** 8 年级

### 创伤视角重构

**可观察行为：** 大喊、扔器材、冲出教室。由看似微小的事件触发：被要求换座位、作业被指正、与其他学生发生轻微肢体碰触。事后常流泪并道歉。本半学期已 12 次留校察看——频率呈上升趋势。

**通过纯粹行为主义视角：** “这名学生极具破坏性、公然挑衅且情绪反复无常。他控制不住脾气。留校察看不管用，我们可能需要更严厉的处分——隔离或停学。”

**通过创伤知情视角：** 座位变动、批评反馈与意外肢体接触可能对这名学生来说尤其艰难。创伤是一种可能解释；事后流泪和道歉本身并不能确认这属于非自主的创伤反应。请与该生及恰当教职工核查当前的无障碍、感官、任务及同伴需求，而不要去打听其创伤史。爆发次数与留校察看同时增加，并不能证明是留校察看导致了爆发。由于存在抛扔器材和擅自离开教室的情况，授权教职工**现在**就必须审查安全状况及现有个人支持计划。

### 课堂调整

**调整 1：可预测的常规与提前预告**
- **具体做法：** 尽量保持课堂常规一致。固定座位、固定课程结构、固定期望。当必须做出变动（代课老师、换教室、调整座位）时，提前告知该生：“明天我们要换到另一间教室上课——我想提前跟你说一声，免得太突然。”在可行的情况下尽早预告，并核实学生是否觉得有帮助。
- **为何有帮助：** 可预测的信息有助于降低不确定感（Perry, 2006; Craig, 2016）。核实学生的实际反应，而非断言某种神经机制。
- **课堂实景：** 周一上课伊始：“这周是常规周——老教室、老流程。只有一个变化：周四有一位嘉宾来分享 15 分钟。周三我会再提醒大家一次。”

**调整 2：商定的情绪调节空间**
- **具体做法：** 与学生及授权教职工共同审阅任何现有的个人支持计划。如果设置调节空间是恰当的，在本地政策框架下明确约定其具体位置、监护方式、进出规则与返回流程。切勿自动赋予“随时冲进走廊”的许可。
- **为何有帮助：** 可预测的选项可能支持情绪调节；其适用性取决于学生与环境，且不保证必然能阻止爆发。
- **课堂实景：** 现有计划中指定的教室内安静角落或其他选项，并配有已知的成人跟进核查。不安全的擅自离场遵循本地安全规程。

**调整 3：将纠错重构为成长对话**
- **具体做法：** 对该生作业给反馈时，先肯定**已经奏效的部分**，再处理需要改进的地方。使用协作式语言：“这一部分写得很棒——我们来看看怎么在此基础上更进一步”，而非“这里错了”。避免在纸面上用红笔大片批注——改用简短口头交流或便利贴。
- **为何有帮助：** 私密、具体的反馈可能比公开指正更容易被接纳。切勿想当然地归因于依恋恐惧，也不要禁止准确纠错；询问哪种反馈形式对这名学生最有帮助（Hattie & Timperley, 2007）。
- **课堂实景：** 不在作业本上写“错误”，而是安静走近：“我看得出你已经掌握了 [具体优势]。有一处我想和你一起看看——我可以指给你看吗？”

**调整 4：物理空间意识**
- **具体做法：** 走近学生时从正面可见且尊重的方式靠近，避免不必要的居高临下压迫感或肢体触碰；在可行时商定个人空间偏好，并在需要时遵守安全规程。当其他学生需要走动经过时，将该生安排在排尾或靠墙位置，减少无意碰撞。
- **为何有帮助：** 意外的肢体接触可能出于多种原因让人不适。减少可避免的碰触，而不将其直接贴上创伤史或神经系统状态的标签（van der Kolk, 2014）。
- **课堂实景：** 走近学生课桌时从正面接近，提前打招呼：“我过来看看你的作业。”将学生安排在靠墙座位，并确保通道符合商定的无障碍与监护计划。

**调整 5：减少事件发生时与事后的围观关注**
- **具体做法：** 爆发发生时，首先遵循现有安全计划，并尽量减少不必要的公开围观。不要提高音量。不要居高临下逼近。不要让其他学生充当目击证人。尽可能缩小关注圈：引导其他学生继续手头工作，冷静轻声接近该生，提供商定的安全空间选项。事后进行私密、修复性的对话（而非当众训斥）。
- **为何有帮助：** 公开围观会加剧尴尬与痛苦；在不妨碍安全行动的前提下减少不必要的暴露。隐私保护了学生的尊严，避免了让日后情绪调节变得更加困难的羞辱感。
- **课堂实景：** 若在现有计划下安全可控，冷静引导全班继续学习并提供商定支持：“我在这里帮你；我们按计划来。”若安全状况不确定，按本地程序立即寻求授权教职工协助，切勿想当然以为全班能自行继续上课。

### 应对规范

**当行为发生时：**

1. **首先遵循现有安全计划。** 抛扔器材或不安全离场需要启动学校的个人/应急程序并寻求授权协助。本草案不规定危机处置指令。
2. **使用冷静、简短、尊重的沟通。** 提供商定的支持，在恰当时暂时简化非核心任务要求；保留必要的安全指令。
3. **仅在恰当且安全时使用商定的调节选项。** 切勿自行规定允许跑出走廊、追逐、身体阻拦或固定等待时长。这些决策属于本地计划与授权教职工的权限。
4. **保持监护与重新连接。** 遵循监护安排，在不套用固定“大脑恢复计时器”的前提下核查学生是否准备好重新加入学习。
5. **事后复盘与修复。** 当学生能够参与时，私下讨论当前需求、对他人造成的影响以及有支持地重返学习。仅在适合且自愿的情况下使用修复性选项。

**切忌做法：**
- 切勿羞辱、威胁、下诊断或打听创伤叙事。
- 切勿用笼统的“等一等”“让他出去”或“取消一切要求”的建议来替代现有安全计划。
- 切勿向全班谈论学生的敏感个人信息。

本应对草案在投入使用前，必须由授权学校教职工对照本地政策及任何现有个人支持计划进行审核，并在需要时征询专业人员意见。

### 边界界定

**在此情境下，创伤知情实践“是什么”：**
- 认真对待痛苦与无障碍需求，而不武断判定爆发的病因
- 营造能够降低触发频率与强度的课堂条件
- 在保护所有人安全的同时，提供冷静支持、恰当的任务调整与商定的调节选项
- 在学生恢复平稳后开展修复性对话
- 维持对该生将在调整后的支持下继续学习、参与并进步的期望

**创伤知情实践“不是什么”：**
- 任由学生随心所欲而不做任何回应
- 彻底取消学业期望（“别管作业了”）
- 忽视对其他学生造成的影响
- 由教师充当心理治疗师或打听学生的创伤经历
- 预设支持必须是暂时的——保留必要的无障碍支持，并与学生及恰当教职工共同评估调整

### 转介指征

**紧急关切：** 存在即时危险、不安全离场，或涉及虐待、自伤或自杀的披露，必须立即启动现有个人/应急计划、本地保护程序并寻求授权协助。切勿等待常规预约或累计到特定事件次数。

**持续支持：** 在这个虚构案例中，抛扔器材、擅自离场以及事件频率上升本身就已经充分构成理由，需要立即与 SENCO/年级主任及相关合格专业人员共同评估。当出现持续痛苦、学习准入受阻或教师感到超出自身能力范围时，请及时求助。在安全的前提下可以继续课堂调整；但课堂调整既不能诊断也不能治疗潜在临床状况。

---

## 已知局限性

1. **本技能提供的是课堂层面指导，而非治疗性干预。** 课堂中的创伤知情实践为经历创伤的学生创造了感到足够安全去学习的**条件**——但它不能治疗创伤本身。拥有严重创伤史的学生在课堂创伤知情实践之外，还需要专业的心理治疗支持。

2. **教师不需要知道“到底发生了什么”。** 创伤知情实践不要求教师了解学生的隐私过往。事实上，教师**不应**主动打听创伤经历的细节——这不是教师的职责，且听闻细节可能引发替代性创伤。教师的角色是营造安全、可预测、有连接的环境，并以理解而非单纯惩罚来回应可观察到的行为。

3. **支持性实践惠及众多学生。** 可预测的常规、温暖的关系、一致的边界、变动的提前预告、尊重的反馈——这些对**每一位**学生都是好做法，而不仅仅针对经历过创伤的学生。上述调整不应显得像是专门为某一个学生开设的特殊项目；它们应当成为整个班级日常运作的自然方式。

4. **个体需求与全班利益之间存在现实张力。** 一名学生冲出教室、大喊大叫或抛扔器材，会影响班里其他每位学生的学习与安全感。创伤知情实践并不意味着全班必须无止境地承受干扰。如果现有调整不足以应对、行为依然具有破坏性，学校必须与授权教职工及该生共同评估额外的恰当支持，从而同时满足该生与全班的需求。
