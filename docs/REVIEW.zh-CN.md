# 技能描述审阅 — Agent Skills v2

**审阅者须知：**
- 每个条目展示了拟议的描述与调用设置。
- 如果任何描述存在错误、过于宽泛、过于狭窄或违反格式规则，请直接在本文件中编辑。
- 在任何你想标记出来讨论的行上删除 ❓ 标记。
- 当对全部 107 个条目均满意时，请确认，随后描述将被应用。

---

## 领域：memory-learning-science（8 个技能）

### cognitive-load-analyser
**拟议描述：**
"Analyse a learning task for cognitive load problems and recommend specific design improvements. Use when tasks overwhelm students, instructions feel complex, or materials need simplifying."
**字符数：** 188 ✅
**disable-model-invocation：** false
**理由：** 由认知负荷 / 任务复杂度触发，足够具体。

---

### dual-coding-designer
**拟议描述：**
"Design a visual complement to verbal content using dual coding principles for stronger encoding. Use when creating slides, diagrams, posters, or visual explanations of complex concepts."
**字符数：** 185 ✅
**disable-model-invocation：** false
**理由：** 由双重编码 / 学习用视觉设计触发，足够具体。

---

### elaborative-interrogation-generator
**拟议描述：**
"Generate elaborative interrogation prompts that deepen encoding through targeted why and how questions. Use when students memorise without understanding or need deeper processing of content."
**字符数：** 190 ✅
**disable-model-invocation：** false
**理由：** 由精细加工提问 / 深度提问触发，足够具体。

---

### feedback-quality-analyser
**拟议描述：**
"Analyse existing written feedback for quality, specificity, actionability, and impact on student learning. Use when reviewing teacher or peer feedback to improve feedback practices."
**字符数：** 181 ✅
**disable-model-invocation：** false
**理由：** 由反馈质量审查触发，足够具体。

---

### interleaving-unit-planner
**拟议描述：**
"Redesign a blocked topic sequence into an interleaved plan with mixed practice across related topics. Use when planning units, homework schedules, or revision programmes."
**字符数：** 170 ✅
**disable-model-invocation：** false
**理由：** 由交错练习 / 混合练习触发，属于特定教学法。

---

### retrieval-practice-generator
**拟议描述：**
"Generate retrieval practice questions at varied difficulty levels for a topic or concept. Use when creating quiz starters, revision activities, or low-stakes testing materials."
**字符数：** 176 ✅
**disable-model-invocation：** false
**理由：** 由提取练习 / 测验生成触发，足够具体。

---

### spaced-practice-scheduler
**拟议描述：**
"Design a spaced retrieval schedule for any topic list and timeline. Use when planning units, term sequences, or revision programmes."
**字符数：** 132 ✅
**disable-model-invocation：** false
**理由：** 触发器具体（复习规划、间隔安排），不太可能误触发。

---

### worked-example-fading-designer
**拟议描述：**
"Design a worked example fading sequence from fully worked examples through to independent practice. Use when teaching procedures, algorithms, or multi-step processes to novice learners."
**字符数：** 185 ✅
**disable-model-invocation：** false
**理由：** 由样例学习 / 支架撤除触发，属于特定教学法。

---

## 领域：ai-learning-science（14 个技能）

### adaptive-hint-sequence-designer
**拟议描述：**
"Generate a cascading hint sequence for a problem type, revealing progressively without giving answers. Use when designing tutoring dialogues or scaffolded worksheets."
**字符数：** 166 ✅
**disable-model-invocation：** false
**理由：** 触发器具体（提示设计、支架式解题支持），不太可能误触发。

---

### ai-facilitated-collaborative-learning-designer
**拟议描述：**
"Design AI-supported collaborative tasks that structure group interaction and address participation problems. Use when students struggle to collaborate effectively on group tasks."
**字符数：** 178 ✅
**disable-model-invocation：** false
**理由：** 由 AI + 协作情境触发，足够具体。

---

### ai-feedback-design-principles
**拟议描述：**
"Audit and redesign AI-generated feedback for pedagogical quality, timing, and learning impact. Use when building or reviewing automated feedback in digital learning tools."
**字符数：** 171 ✅
**disable-model-invocation：** false
**理由：** 由 AI 反馈设计触发，情境具体。

---

### cognitive-tutoring-architecture-designer
**拟议描述：**
"Map knowledge components and skill hierarchies for a cognitive tutoring system or adaptive learning platform. Use when designing intelligent tutoring software or skill-based mastery systems."
**字符数：** 190 ✅
**disable-model-invocation：** true
**理由：** 需要关于辅导系统架构的深度技术上下文；在常规辅导讨论中自动激活容易误触发。

---

### digital-worked-example-sequence
**拟议描述：**
"Create an interactive digital worked example sequence with fading for online or blended delivery. Use when building e-learning modules, LMS content, or app-based instruction."
**字符数：** 174 ✅
**disable-model-invocation：** false
**理由：** 由数字样例触发，足够具体。

---

### erroneous-example-designer
**拟议描述：**
"Design deliberately flawed examples that develop error-detection skills and deepen understanding. Use when students make characteristic errors and need practice spotting mistakes."
**字符数：** 179 ✅
**disable-model-invocation：** false
**理由：** 由错误识别与例题中刻意设置的错误触发。

---

### formative-assessment-loop-designer
**拟议描述：**
"Design an adaptive assessment loop where each student response triggers the next instructional move. Use when building technology-enhanced formative assessment cycles."
**字符数：** 167 ✅
**disable-model-invocation：** false
**理由：** 由自适应/技术增强的形成性评价循环触发，区别于一般形成性评价。

---

### individual-spacing-algorithm-explainer
**拟议描述：**
"Explain and configure individual spacing algorithms using student performance data and forgetting curves. Use when personalising retention schedules in adaptive learning platforms."
**字符数：** 180 ✅
**disable-model-invocation：** true
**理由：** 需要大多数对话中不会提供的过往表现数据。

---

### intelligent-tutoring-dialogue-designer
**拟议描述：**
"Script a multi-turn tutoring dialogue with branching responses for anticipated student difficulties. Use when designing AI tutors, chatbot interactions, or structured one-to-one support scripts."
**字符数：** 194 ✅
**disable-model-invocation：** false
**理由：** 由辅导对话设计触发，足够具体。

---

### learning-analytics-interpretation-guide
**拟议描述：**
"Interpret learning analytics data and translate dashboard findings into actionable teaching decisions. Use when reviewing LMS data, quiz patterns, or engagement metrics."
**字符数：** 169 ✅
**disable-model-invocation：** false
**理由：** 由学习分析解读触发，情境具体。

---

### metacognitive-monitoring-ai-contexts
**拟议描述：**
"Design metacognitive checkpoints that prevent AI-assisted learning from bypassing genuine understanding. Use when students use AI tools and may overestimate their own comprehension."
**字符数：** 181 ✅
**disable-model-invocation：** false
**理由：** 由 AI 与元认知交叉点触发，具体且切合实际。

---

### productive-failure-desirable-difficulty-designer
**拟议描述：**
"Redesign a direct instruction sequence to include productive struggle before the explanation phase. Use when teaching concepts that benefit from failure-first approaches."
**字符数：** 170 ✅
**disable-model-invocation：** false
**理由：** 由建设性失败 / 必要难度触发，属于特定教学法。

---

### self-explanation-prompt-designer
**拟议描述：**
"Create self-explanation prompts that deepen understanding of worked examples, texts, or diagrams. Use when students read material passively without engaging with underlying principles."
**字符数：** 184 ✅
**disable-model-invocation：** false
**理由：** 由自我解释与被动阅读触发，足够具体。

---

### worked-example-to-problem-solving-transition-designer
**拟议描述：**
"Design the transition from worked examples to independent problem-solving using expertise-reversal principles. Use when students follow examples but cannot solve problems alone."
**字符数：** 177 ✅
**disable-model-invocation：** false
**理由：** 由样例向独立解题过渡触发，属于特定教学法。

---

## 领域：explicit-instruction（5 个技能）

### checking-for-understanding-protocol-designer
**拟议描述：**
"Design a checking-for-understanding protocol with specific techniques for each lesson stage. Use when planning systematic comprehension checks during explicit or direct instruction."
**字符数：** 181 ✅
**disable-model-invocation：** false
**理由：** 由理解检查（CFU）流程设计触发，特定于明确教学情境。

---

### explicit-instruction-sequence-builder
**拟议描述：**
"Build a complete explicit instruction sequence from teacher modelling through guided practice to independent work. Use when teaching new skills, procedures, or concepts through direct instruction."
**字符数：** 196 ✅
**disable-model-invocation：** false
**理由：** 由明确/直接教学规划触发，足够具体。

---

### lesson-opening-designer
**拟议描述：**
"Design a lesson opening that activates prior knowledge and connects previous learning to today's content. Use when planning lesson starters, retrieval openers, or advance organisers."
**字符数：** 182 ✅
**disable-model-invocation：** false
**理由：** 由课堂开场/导入活动触发，足够具体。

---

### practice-problem-sequence-designer
**拟议描述：**
"Generate a scaffolded sequence of practice problems with graduated difficulty and strategic variability. Use when creating worksheets, homework sets, or independent practice materials."
**字符数：** 184 ✅
**disable-model-invocation：** false
**理由：** 由练习题序列生成触发，足够具体。

---

### think-aloud-script-generator
**拟议描述：**
"Script a teacher think-aloud demonstrating expert reasoning processes for a specific task. Use when modelling problem-solving, writing, reading comprehension, or analytical processes."
**字符数：** 183 ✅
**disable-model-invocation：** false
**理由：** 由出声思考 / 专家思维示范触发，足够具体。

---

## 领域：questioning-discussion（4 个技能）

### dialogic-teaching-move-generator
**拟议描述：**
"Generate follow-up teaching moves that extend student thinking after a specific classroom response. Use when a student says something worth exploring and the teacher wants to deepen the dialogue."
**字符数：** 195 ✅
**disable-model-invocation：** false
**理由：** 由对话式教学动作 / 课堂讨论追问触发，足够具体。

---

### discussion-protocol-selector
**拟议描述：**
"Select and configure a structured discussion protocol matched to the purpose, topic, and group readiness. Use when planning classroom discussions, Socratic seminars, or structured debate."
**字符数：** 187 ✅
**disable-model-invocation：** false
**理由：** 由讨论流程选择触发，足够具体。

---

### hinge-question-designer
**拟议描述：**
"Design a diagnostic hinge question that reveals whether students understand enough to move on. Use when planning key checkpoints mid-lesson during explicit or direct instruction."
**字符数：** 178 ✅
**disable-model-invocation：** false
**理由：** 由关键诊断问题（hinge questions）/ 课中诊断触发，足够具体。

---

### socratic-questioning-sequence-generator
**拟议描述：**
"Generate a Socratic questioning sequence that develops conceptual understanding through guided inquiry. Use when facilitating philosophical discussions, concept exploration, or critical examination."
**字符数：** 198 ✅
**disable-model-invocation：** false
**理由：** 由苏格拉底式提问触发，属于特定教学法。

---

## 领域：curriculum-assessment（14 个技能）

### assessment-validity-checker
**拟议描述：**
"Audit a proposed assessment for construct validity, reliability, and alignment to learning objectives. Use when reviewing or quality-assuring assessments before deployment."
**字符数：** 172 ✅
**disable-model-invocation：** false
**理由：** 由评价质量/效度审查触发，足够具体。

---

### backwards-design-unit-planner
**拟议描述：**
"Plan a unit using backwards design from desired outcomes through assessment evidence to learning activities. Use when starting a new unit or redesigning an existing one from standards."
**字符数：** 184 ✅
**disable-model-invocation：** false
**理由：** 由单元规划 / 逆向设计触发，常见且恰当。

---

### competency-unpacker
**拟议描述：**
"Unpack a broad standard or competency descriptor into specific, assessable success criteria and sub-skills. Use when interpreting curriculum standards or writing learning objectives."
**字符数：** 182 ✅
**disable-model-invocation：** false
**理由：** 由课标拆解触发，属于特定工作流。

---

### criterion-referenced-rubric-generator
**拟议描述：**
"Generate a criterion-referenced rubric with descriptive performance levels for a specific task and objective. Use when creating marking guides, setting expectations, or designing assessments."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由量规创建触发，足够具体。

---

### critical-thinking-task-designer
**拟议描述：**
"Design discipline-specific critical thinking tasks grounded in knowledge-contingent reasoning rather than generic skills. Use when embedding higher-order thinking into subject content."
**字符数：** 184 ✅
**disable-model-invocation：** false
**理由：** 由批判性思维 + 课程/学科触发，通过“知识类型聚焦”与 literacy-critical-thinking 版本相区分。

---

### curriculum-knowledge-architecture-designer
**拟议描述：**
"Map the epistemic structure of a subject to determine knowledge types and inform curriculum sequencing. Use when designing courses, restructuring programmes, or analysing knowledge architecture."
**字符数：** 194 ✅
**disable-model-invocation：** false
**理由：** 由课程结构/知识架构触发，足够具体。

---

### differentiation-adapter
**拟议描述：**
"Adapt a classroom task for specific learner needs while preserving the core learning objective intact. Use when differentiating for SEND, EAL, gifted, ADHD, dyslexia, or anxiety."
**字符数：** 178 ✅
**disable-model-invocation：** false
**理由：** 由差异化 + 特定学习者需求触发，恰当。

---

### dispositional-knowledge-assessment-designer
**拟议描述：**
"Design multi-informant assessment approaches for dispositional competencies like curiosity or resilience. Use when assessing character strengths or competencies that written tests cannot capture."
**字符数：** 195 ✅
**disable-model-invocation：** true
**理由：** 需要来自发展阶段系统的特定阶段/能力上下文；在一般评价讨论中自动激活容易误触发。

---

### formative-assessment-technique-selector
**拟议描述：**
"Select the right formative assessment technique for a specific learning moment, purpose, and age group. Use when choosing how to check understanding during, between, or after lessons."
**字符数：** 183 ✅
**disable-model-invocation：** true
**理由：** 触发词过于宽泛——“checking understanding（检查理解）”几乎出现在每一次教学对话中。

---

### gap-analysis-from-student-work
**拟议描述：**
"Analyse student work against criteria to identify specific gaps between current performance and learning objectives. Use when reviewing submissions, planning feedback, or diagnosing learning needs."
**字符数：** 197 ✅
**disable-model-invocation：** false
**理由：** 由学生作品分析触发，属于特定工作流。

---

### kud-knowledge-type-mapper
**拟议描述：**
"Classify curriculum content into Know, Understand, and Do categories to align teaching and assessment approaches. Use when planning units, writing objectives, or selecting assessment methods."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由 KUD / 知识类型触发，属于特定框架。

---

### learning-progression-builder
**拟议描述：**
"Build a learning progression showing prerequisite-to-mastery steps for a target skill or understanding. Use when sequencing content, designing diagnostics, or mapping prerequisite gaps."
**字符数：** 185 ✅
**disable-model-invocation：** false
**理由：** 由学习进阶/排序触发，足够具体。

---

### project-brief-designer
**拟议描述：**
"Design a project-based learning brief with a driving question, milestones, and assessment criteria. Use when planning PBL units, inquiry projects, or extended investigations."
**字符数：** 174 ✅
**disable-model-invocation：** false
**理由：** 由 PBL / 项目设计触发，足够具体。

---

### scope-and-sequence-designer
**拟议描述：**
"Design a scope and sequence showing vertical and horizontal curriculum coherence across a programme or year. Use when building new programmes, restructuring subjects, or ensuring progression."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由范围与序列 / 课程项目设计触发，足够具体。

---

## 领域：literacy-critical-thinking（7 个技能）

### argument-structure-scaffold-generator
**拟议描述：**
"Generate argument structure scaffolds using Toulmin, PEEL, or CER frameworks for a specific claim or question. Use when teaching argumentative or analytical writing across any subject."
**字符数：** 184 ✅
**disable-model-invocation：** false
**理由：** 由论证支架 / 写作框架触发，足够具体。

---

### critical-thinking-task-designer
**拟议描述：**
"Design a critical thinking task targeting specific skills like evaluating evidence, identifying bias, or analysing arguments. Use when embedding critical analysis into subject lessons."
**字符数：** 184 ✅
**disable-model-invocation：** false
**理由：** 由批判性思维任务设计触发，通过“技能聚焦”而非“知识类型聚焦”与 curriculum-assessment 版本相区分。

---

### disciplinary-writing-scaffold
**拟议描述：**
"Create a writing scaffold teaching the genre conventions specific to an academic discipline. Use when students write lab reports, historical essays, or other discipline-specific text types."
**字符数：** 189 ✅
**disable-model-invocation：** false
**理由：** 由学科写作 / 体裁特定支架触发，足够具体。

---

### media-literacy-deconstruction-protocol
**拟议描述：**
"Design a media deconstruction protocol analysing persuasion, bias, or representation in media texts. Use when teaching students to critically read advertisements, news, or social media content."
**字符数：** 193 ✅
**disable-model-invocation：** false
**理由：** 由媒体素养 / 解构触发，足够具体。

---

### reading-comprehension-strategy-selector
**拟议描述：**
"Select and sequence reading comprehension strategies matched to a specific text's challenges and demands. Use when students struggle with a text or need targeted reading support."
**字符数：** 178 ✅
**disable-model-invocation：** false
**理由：** 由阅读理解策略触发，足够具体。

---

### source-credibility-evaluation-protocol
**拟议描述：**
"Design a source evaluation protocol using lateral reading and credibility checks for digital information. Use when students need to evaluate websites, online sources, or social media claims."
**字符数：** 190 ✅
**disable-model-invocation：** false
**理由：** 由来源评估 / 可信度触发，足够具体。

---

### text-complexity-analyser
**拟议描述：**
"Analyse text complexity across quantitative, qualitative, and reader-task dimensions with scaffolding recommendations. Use when selecting texts, assessing readability, or planning reading support."
**字符数：** 196 ✅
**disable-model-invocation：** false
**理由：** 由文本复杂度 / 可读性分析触发，足够具体。

---

## 领域：eal-language-development（5 个技能）

### academic-language-sentence-frame-generator
**拟议描述：**
"Generate tiered sentence frames for academic tasks that scaffold language production across proficiency levels. Use when EAL students need structured language support for classroom discourse."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由句型框架 + EAL/学术语言触发，足够具体。

---

### language-demand-analyser
**拟议描述：**
"Analyse the language demands of a classroom task to identify barriers for EAL and multilingual learners. Use when adapting tasks, planning support, or assessing linguistic accessibility."
**字符数：** 186 ✅
**disable-model-invocation：** false
**理由：** 由语言需求 + EAL 触发，足够具体。

---

### scaffolded-task-modifier
**拟议描述：**
"Modify a classroom task with language scaffolds that preserve cognitive demand for EAL learners. Use when adapting existing tasks for students at different English proficiency levels."
**字符数：** 183 ✅
**disable-model-invocation：** false
**理由：** 由 EAL 任务支架触发，足够具体。

---

### sheltered-instruction-lesson-modifier
**拟议描述：**
"Modify a lesson plan using SIOP sheltered instruction principles to support language learners across all four skills. Use when planning lessons for classes that include EAL students."
**字符数：** 182 ✅
**disable-model-invocation：** false
**理由：** 由庇护式教学 / EAL 备课触发，足够具体。

---

### vocabulary-tiering-tool
**拟议描述：**
"Tier vocabulary from a text or topic into everyday, academic, and technical categories with teaching priorities. Use when pre-teaching vocabulary or identifying language barriers in a text."
**字符数：** 189 ✅
**disable-model-invocation：** false
**理由：** 由词汇分层 / 词语分类触发，足够具体。

---

## 领域：self-regulated-learning（5 个技能）

### error-analysis-protocol
**拟议描述：**
"Design an error analysis protocol to diagnose the root cause of student mistakes and misconceptions. Use when error patterns appear in student work and targeted feedback is needed."
**字符数：** 180 ✅
**disable-model-invocation：** false
**理由：** 由错误分析 / 错误诊断触发，足够具体。

---

### goal-setting-protocol-designer
**拟议描述：**
"Design a structured goal-setting protocol using SMART or implementation-intention frameworks for students. Use when launching units, projects, or developing student self-direction habits."
**字符数：** 187 ✅
**disable-model-invocation：** false
**理由：** 由学生目标设定流程设计触发，足够具体。

---

### metacognitive-prompt-library
**拟议描述：**
"Build a library of metacognitive prompts targeting planning, monitoring, or evaluation for a specific task. Use when developing students' thinking-about-thinking during independent work."
**字符数：** 186 ✅
**disable-model-invocation：** false
**理由：** 由元认知提示触发，足够具体。

---

### self-regulation-scaffold-generator
**拟议描述：**
"Generate scaffolds supporting student self-regulation across planning, monitoring, and evaluation phases. Use when students struggle to manage their own learning during extended or independent tasks."
**字符数：** 199 ✅
**disable-model-invocation：** false
**理由：** 由自我调节支架触发，足够具体。

---

### study-strategy-selector
**拟议描述：**
"Select evidence-based study strategies matched to material type, learning goal, and student habits. Use when advising students on revision techniques, homework, or independent study approaches."
**字符数：** 193 ✅
**disable-model-invocation：** false
**理由：** 由学习策略 / 复习建议触发，足够具体。

---

## 领域：wellbeing-motivation-agency（12 个技能）

### agency-scaffold-generator
**拟议描述：**
"Generate scaffolds that gradually increase student choice, voice, and ownership within a learning task. Use when students depend heavily on teacher direction and need to develop autonomy."
**字符数：** 187 ✅
**disable-model-invocation：** false
**理由：** 由学生能动性 / 自主权支架触发，足够具体。

---

### awe-wonder-experience-designer
**拟议描述：**
"Design a moment of awe or wonder that hooks curiosity and deepens emotional engagement with content. Use when opening units, introducing surprising material, or reigniting student interest."
**字符数：** 189 ✅
**disable-model-invocation：** false
**理由：** 由敬畏/惊奇/好奇心钩子触发，足够具体。

---

### belonging-classroom-culture-designer
**拟议描述：**
"Design targeted interventions that strengthen belonging and inclusion for specific classroom dynamics. Use when students feel isolated, cliques form, or new students need integrating."
**字符数：** 183 ✅
**disable-model-invocation：** false
**理由：** 由归属感 / 包容性 / 班级文化触发，足够具体。

---

### flow-state-condition-designer
**拟议描述：**
"Optimise a learning activity for flow by balancing challenge level, skill, clear goals, and immediate feedback. Use when students are bored, anxious, or disengaged during a task."
**字符数：** 178 ✅
**disable-model-invocation：** false
**理由：** 由心流状态 / 投入度优化触发，足够具体。

---

### implementation-intention-designer
**拟议描述：**
"Create if-then implementation intentions and WOOP plans for specific student behaviour change goals. Use when students know what to do but struggle to follow through on habits or routines."
**字符数：** 188 ✅
**disable-model-invocation：** false
**理由：** 由执行意图 / 行为改变触发，足够具体。

---

### motivation-diagnostic-task-redesign
**拟议描述：**
"Diagnose motivation problems in a task using self-determination theory and redesign for autonomy, competence, and relatedness. Use when students are disengaged, resistant, or going through the motions."
**字符数：** 201 ✅
**disable-model-invocation：** false
**理由：** 由动机诊断 / 自我决定理论（SDT）重设计触发，足够具体。

---

### perma-based-lesson-designer
**拟议描述：**
"Design a lesson that embeds PERMA wellbeing elements alongside academic learning objectives. Use when planning lessons that intentionally support both content mastery and student flourishing."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由 PERMA / 积极教育备课触发，足够具体。

---

### restorative-practice-protocol-designer
**拟议描述：**
"Design a restorative practice protocol for addressing harm, rebuilding trust, and restoring relationships. Use when managing conflict, behavioural incidents, or relationship breakdown between students."
**字符数：** 201 ✅
**disable-model-invocation：** false
**理由：** 由恢复性实践 / 冲突解决触发，足够具体。

---

### ruler-emotional-literacy-sequence
**拟议描述：**
"Design a RULER emotional literacy sequence for recognising, understanding, labelling, expressing, and regulating emotions. Use when students struggle with emotional regulation, conflict, or anxiety."
**字符数：** 198 ✅
**disable-model-invocation：** false
**理由：** 由 RULER / 情绪素养触发，属于特定框架。

---

### self-efficacy-builder-sequence
**拟议描述：**
"Design a mastery experience sequence that systematically builds student confidence in a skill they avoid. Use when students say 'I can't do this', avoid tasks, or show learned helplessness."
**字符数：** 189 ✅
**disable-model-invocation：** false
**理由：** 由自我效能感 / 信心建立触发，足够具体。

---

### trauma-informed-practice-designer
**拟议描述：**
"Design trauma-informed classroom practices that prioritise safety, predictability, connection, and regulation. Use when student behaviour may be trauma-related or the class needs a sensitive approach."
**字符数：** 200 ✅
**disable-model-invocation：** false
**理由：** 由创伤知情实践触发，足够具体。

---

### wellbeing-learning-connection-mapper
**拟议描述：**
"Map evidence-based connections between a wellbeing initiative and specific academic learning outcomes. Use when justifying wellbeing programmes, integrating SEL, or linking pastoral and academic work."
**字符数：** 200 ✅
**disable-model-invocation：** false
**理由：** 由福祉与学习联结触发，足够具体。

---

## 领域：environmental-experiential-learning（6 个技能）

### biophilic-learning-environment-designer
**拟议描述：**
"Redesign a learning space using biophilic design principles to improve focus, calm, and wellbeing. Use when classroom environment contributes to restlessness, poor attention, or stress."
**字符数：** 185 ✅
**disable-model-invocation：** false
**理由：** 由教室环境 + 自然/亲生命触发，足够具体。

---

### ecological-inquiry-anchor-designer
**拟议描述：**
"Design an inquiry sequence anchored in a local ecosystem that embeds science or geography curriculum content. Use when teaching through local living systems like gardens, ponds, or hedgerows."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由生态/本地生态系统探究触发，足够具体。

---

### experiential-learning-cycle-designer
**拟议描述：**
"Structure a direct experience into a full learning cycle with concrete experience, reflection, and conceptual transfer. Use when planning field trips, simulations, or practical tasks."
**字符数：** 183 ✅
**disable-model-invocation：** false
**理由：** 由体验式学习 / 实地考察触发，足够具体。

---

### interdisciplinary-real-world-connection-mapper
**拟议描述：**
"Map curriculum connections across multiple subjects for a real-world problem or authentic context. Use when planning cross-curricular projects or connecting content to real issues."
**字符数：** 180 ✅
**disable-model-invocation：** false
**理由：** 由跨学科 / 跨课程联结触发，足够具体。

---

### outdoor-learning-sequence-designer
**拟议描述：**
"Design a structured outdoor learning sequence embedding curriculum objectives in an available outdoor space. Use when planning lessons in school grounds, parks, or local natural environments."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由户外学习触发，足够具体。

---

### service-learning-project-designer
**拟议描述：**
"Design a service-learning project connecting genuine community need with embedded curriculum learning. Use when planning community projects, civic engagement, or social action units."
**字符数：** 182 ✅
**disable-model-invocation：** false
**理由：** 由服务学习 / 社区项目触发，足够具体。

---

## 领域：montessori-alternative-approaches（4 个技能）

### mixed-age-learning-task-designer
**拟议描述：**
"Design a learning task where mixed-age students work together with mutual benefit for all age groups. Use when planning cross-age tutoring, vertical grouping, or multi-year group activities."
**字符数：** 190 ✅
**disable-model-invocation：** false
**理由：** 由混龄 / 跨年龄学习触发，足够具体。

---

### prepared-environment-designer
**拟议描述：**
"Redesign a classroom as a prepared environment optimised for independent learning, calm transitions, and material access. Use when classroom layout hinders independence or self-directed work."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由预备环境 / 蒙特梭利教室设计触发，足够具体。

---

### three-part-lesson-designer
**拟议描述：**
"Design a Montessori three-period lesson for introducing concepts through concrete materials and naming. Use when teaching vocabulary, classifications, or concepts through hands-on materials."
**字符数：** 190 ✅
**disable-model-invocation：** false
**理由：** 由三阶段课程 / 蒙特梭利触发，足够具体。

---

### uninterrupted-work-cycle-designer
**拟议描述：**
"Design an uninterrupted work cycle with choice-based activities structured within a realistic time block. Use when planning Montessori-style independent work periods or extended choice time."
**字符数：** 190 ✅
**disable-model-invocation：** false
**理由：** 由不间断工作周期 / 蒙特梭利工作时段触发，足够具体。

---

## 领域：global-cross-cultural-pedagogies（9 个技能）

### cpa-sequence-designer
**拟议描述：**
"Design a Concrete-Pictorial-Abstract learning sequence for a mathematical concept using manipulatives. Use when teaching maths through Singapore method or when students struggle with abstraction."
**字符数：** 195 ✅
**disable-model-invocation：** false
**理由：** 由 CPA / 具象-图像-抽象 / 新加坡数学触发，足够具体。

---

### cross-cultural-task-validity-checker
**拟议描述：**
"Check an educational practice or task for cultural bias, WEIRD assumptions, and cross-cultural validity. Use when adapting resources for diverse contexts or questioning universal claims."
**字符数：** 186 ✅
**disable-model-invocation：** false
**理由：** 由文化偏见 / WEIRD / 跨文化效度触发，足够具体。

---

### culturally-responsive-teaching-designer
**拟议描述：**
"Redesign a lesson to centre students' cultural backgrounds, community knowledge, and lived experience. Use when making curriculum relevant and inclusive for diverse student populations."
**字符数：** 185 ✅
**disable-model-invocation：** false
**理由：** 由文化回应式教学触发，足够具体。

---

### emergent-project-design-scaffold
**拟议描述：**
"Scaffold an emergent project from observed children's interests using Reggio-inspired approaches. Use when following children's fascinations into deeper inquiry in early years or primary settings."
**字符数：** 196 ✅
**disable-model-invocation：** false
**理由：** 由生成性课程 / 瑞吉欧 / 儿童兴趣触发，足够具体。

---

### phenomenon-based-unit-anchor
**拟议描述：**
"Anchor a multidisciplinary unit in a real-world phenomenon that requires multiple subject lenses to understand. Use when designing integrated or phenomenon-based units across disciplines."
**字符数：** 187 ✅
**disable-model-invocation：** false
**理由：** 由现象式学习 / 整合单元触发，足够具体。

---

### place-based-inquiry-anchor
**拟议描述：**
"Anchor curriculum learning in a specific local place with connections to community, culture, and identity. Use when connecting academic content to students' local environment and heritage."
**字符数：** 188 ✅
**disable-model-invocation：** false
**理由：** 由地方本位学习 / 本地联结触发，足够具体。

---

### reggio-documentation-protocol
**拟议描述：**
"Design a pedagogical documentation protocol for making children's learning processes visible and shareable. Use when documenting learning, communicating with families, or planning next steps."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由瑞吉欧 / 教学记录触发，足够具体。

---

### ubuntu-collective-knowledge-task-designer
**拟议描述：**
"Design learning tasks built on Ubuntu philosophy emphasising collective knowledge-building and mutual responsibility. Use when fostering collaboration that values community over individual competition."
**字符数：** 201 ✅
**disable-model-invocation：** false
**理由：** 由 Ubuntu / 集体学习触发，属于特定教学法。

---

### variation-theory-task-designer
**拟议描述：**
"Design a variation theory task using contrast, separation, and fusion to teach critical features of a concept. Use when students confuse similar concepts or fail to discern key distinctions."
**字符数：** 190 ✅
**disable-model-invocation：** false
**理由：** 由变易理论 / 概念辨析触发，足够具体。

---

## 领域：professional-learning（9 个技能）

### competency-framework-translator
**拟议描述：**
"Translate an external competency framework like DigComp, GreenComp, or ISTE into classroom-ready activities. Use when implementing framework standards in specific teaching contexts."
**字符数：** 181 ✅
**disable-model-invocation：** false
**理由：** 由能力框架落地触发，足够具体。

---

### instructional-coaching-conversation-guide
**拟议描述：**
"Generate a coaching conversation guide with questions, protocols, and follow-up actions for a teaching focus. Use when preparing for coaching sessions, mentoring, or peer feedback conversations."
**字符数：** 194 ✅
**disable-model-invocation：** false
**理由：** 由教学辅导 / 导师准备触发，足够具体。

---

### lesson-observation-protocol-designer
**拟议描述：**
"Design a focused lesson observation protocol with specific look-fors and evidence collection methods. Use when planning peer observations, coaching visits, or developmental classroom visits."
**字符数：** 190 ✅
**disable-model-invocation：** false
**理由：** 由课堂观察设计触发，足够具体。

---

### lesson-study-cycle-designer
**拟议描述：**
"Design a complete lesson study cycle from research question through collaborative planning to research lesson. Use when planning jugyou kenkyuu or collaborative teacher inquiry into practice."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由课例研究 / 授业研究（jugyou kenkyuu）触发，足够具体。

---

### pedagogical-content-knowledge-developer
**拟议描述：**
"Develop pedagogical content knowledge for a topic by surfacing common misconceptions and effective representations. Use when preparing to teach unfamiliar content or improving teaching of hard topics."
**字符数：** 200 ✅
**disable-model-invocation：** false
**理由：** 由 PCK（学科教学知识）发展 / 主题备课触发，足够具体。

---

### professional-development-session-designer
**拟议描述：**
"Design a professional development session using adult learning principles with active teacher engagement. Use when planning INSET days, CPD workshops, or staff training sessions."
**字符数：** 178 ✅
**disable-model-invocation：** false
**理由：** 由教师专业发展（PD/CPD）活动设计触发，足够具体。

---

### reflective-practice-prompt-generator
**拟议描述：**
"Generate structured reflection prompts for a specific teaching experience or professional learning challenge. Use when debriefing lessons, journaling, or preparing for coaching conversations."
**字符数：** 191 ✅
**disable-model-invocation：** false
**理由：** 由反思性实践 / 教学反思触发，足够具体。

---

### teacher-inquiry-cycle-designer
**拟议描述：**
"Design a practitioner inquiry cycle from research question through data collection to evidence-informed action. Use when starting action research, teacher-led investigation, or professional inquiry."
**字符数：** 198 ✅
**disable-model-invocation：** false
**理由：** 由教师探究 / 行动研究触发，足够具体。

---

### technological-pedagogical-content-knowledge-developer
**拟议描述：**
"Develop TPACK for integrating a specific technology or AI tool into subject teaching with pedagogical alignment. Use when adopting new ed-tech, reviewing AI tools, or planning technology integration."
**字符数：** 199 ✅
**disable-model-invocation：** false
**理由：** 由 TPACK / 教学技术整合触发，足够具体。

---

## 领域：original-frameworks（5 个技能）

### coherent-rubric-logic-builder
**拟议描述：**
"Build a five-level rubric with internally coherent logic for a specific learning target within a developmental band. Use when creating rubrics for competency-based assessment systems."
**字符数：** 183 ✅
**disable-model-invocation：** true
**理由：** 第 14 领域（原创框架）— 特定于 Manning 的阶段体系情境；自动激活容易误触发。

---

### developmental-band-system-designer
**拟议描述：**
"Design a developmental band system mapping student growth from early childhood through upper secondary. Use when building competency-based curriculum architecture for a school or programme."
**字符数：** 189 ✅
**disable-model-invocation：** true
**理由：** 第 14 领域（原创框架）— 需要关于特定学校课程设计的深度上下文。

---

### learning-target-authoring-guide
**拟议描述：**
"Author learning targets for a competency across developmental bands with precise, observable progression language. Use when writing 'I can' statements for competency-based programmes."
**字符数：** 183 ✅
**disable-model-invocation：** true
**理由：** 第 14 领域（原创框架）— 特定于 Manning 的学习目标撰写方法论。

---

### seeds-regenerative-inquiry-cycle
**拟议描述：**
"Design a SEEDS regenerative inquiry cycle connecting place-based learning to ecological awareness for young learners. Use when building early childhood or primary inquiry around ecosystems and community."
**字符数：** 203 ✅
**disable-model-invocation：** true
**理由：** 第 14 领域（原创框架）— 特定的原创框架，在一般探究讨论中容易误触发。

---

### self-determined-project-design-protocol
**拟议描述：**
"Structure a student's self-determined project with mentoring checkpoints, competency alignment, and reflection. Use when guiding student-led projects within a competency-based framework."
**字符数：** 186 ✅
**disable-model-invocation：** true
**理由：** 第 14 领域（原创框架）— 特定于 Manning 的项目协议。

---
