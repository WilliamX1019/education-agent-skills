# 教育 Agent Skills 使用指南

本指南介绍如何在备课、课程设计、评价和学生学习支持中使用 Education Agent Skills Library。库中共有 **165 个技能，分布在 20 个领域**；每个技能都围绕一项具体任务提供可复用的指令、所需输入和输出要求。

## 1. 先了解技能库

技能的源文件位于：

```text
skills/<领域>/<技能名称>/SKILL.md
```

每个 `SKILL.md` 通常包含两部分：

- **YAML 元数据**：技能 ID、适用领域、证据强度与来源、必需和可选输入、预期输出、可衔接技能等。
- **技能正文**：用途、操作步骤、提示词、输出格式、限制说明；有些技能还附带 `references/`、`scripts/` 或示例文件。

使用时优先复制或安装**完整技能文件夹**，不要只复制 `SKILL.md` 而遗漏它引用的本地资源。

## 2. 按领域查找技能

| 领域 | 技能数 | 主要用途 |
| --- | ---: | --- |
| 记忆与学习科学 | 8 | 提取练习、间隔复习、交错练习、认知负荷与反馈 |
| 自我调节学习与元认知 | 5 | 目标设定、学习策略、反思与错误分析 |
| 明确教学与直接教学 | 5 | 示范、渐进式放手、理解检查与练习设计 |
| 提问、讨论与对话 | 5 | 苏格拉底式提问、讨论流程与对话式教学 |
| 读写与批判性思维 | 7 | 阅读理解、论证写作、来源评估与媒体素养 |
| EAL/D 与语言发展 | 5 | 学科语言分析、词汇分层、句型支架与任务调整 |
| 课程设计与评价 | 13 | 逆向设计、学习目标、量规、形成性评价与差距分析 |
| 福祉、动机与学生能动性 | 12 | 自我效能、归属感、动机诊断与能动性支架 |
| 专业学习与教师发展 | 10 | 课堂观察、教师反思、专业发展设计与数据解读 |
| 全球与跨文化教学法 | 9 | 跨文化有效性、现象式学习、CPA 与文化回应式教学 |
| 环境与体验式学习 | 6 | 户外学习、生态探究、体验式循环与服务学习 |
| AI 学习科学 | 14 | 自适应提示、AI 反馈、辅导对话与学习分析 |
| AI 素养 | 7 | 核查 AI 输出、识别幻觉、提示素养与学科可靠性 |
| 蒙特梭利与其他教学路径 | 4 | 预备环境、混龄学习与不间断工作周期 |
| 原创框架 | 17 | SEEDS、H3Uni、学习目标撰写、量规逻辑等实践框架 |
| 课程对齐 | 4 | 课程覆盖审查、KUD 图表与范围序列 |
| 历史思维 | 10 | 史料阅读、来源互证、历史问题与基于文献的教学 |
| 系统思维 | 8 | 系统图景、杠杆点、推理模型与行动设计 |
| 包容性设计 | 3 | 使用 UDL 审视课程并提前发现参与障碍 |
| 面向学生的学习技能 | 13 | 提取优先、渐进提示、信心校准、错误诊断与迁移练习 |

前 19 个领域主要服务教师、课程设计者和学校团队。第 20 个领域面向学生的实时学习互动，帮助 AI 在学习过程中提供提示、追问和反思支架。

## 3. 选择并使用一个技能

1. **明确要完成的任务。** 例如：为一个单元安排复习、设计评价量规，或帮助学生判断 AI 的回答是否可靠。
2. **按领域或关键词查找。** 可以浏览 `skills/`，也可以查看根目录的 [`registry.json`](../registry.json)，按领域、标签或技能名称筛选。
3. **先读技能说明。** 查看 `What This Skill Does`、输入要求、证据来源、限制说明和所需资源，确认它适合当前情境。
4. **准备必需输入。** 根据 `input_schema` 填好必需字段；可选字段只在确实有相关信息时提供。背景信息越具体，结果通常越便于使用。
5. **调用技能并检查结果。** 让 AI 按技能提示词和输出格式完成任务；需要中文时，可明确要求“请用中文输出，保留必要的英文术语”。
6. **由教育者审阅并调整。** 根据课程目标、学生实际情况和本地政策修订结果，再决定是否采用。

### 示例：制定间隔复习计划

使用 [`spaced-practice-scheduler`](../skills/memory-learning-science/spaced-practice-scheduler/SKILL.md) 时，可提供主题、教学周期和每周课时：

```text
请使用 spaced-practice-scheduler，为八年级生物的“细胞”单元制定 8 周复习计划，并用中文输出。

主题：细胞结构、物质运输、细胞分裂、酶、生物大分子
周期：8 周
每周课时：3 节
测验日期：第 8 周
```

技能还接受测验日期、主题难度、课程顺序和班级层面的保留情况等可选信息。没有这些信息时，可以省略；不要为了填满字段而编造数据。

### 示例：在学生学习中使用技能

第 20 领域中的 [`retrieve-first-gate`](../skills/student-learning/retrieve-first-gate/SKILL.md) 适合学生复习已学内容时使用。它会先邀请学生进行不看资料的回忆，再根据实际回答识别已掌握内容、遗漏点和误解。它面向实时学习对话，不是教师备课时生成测验题的替代品。

## 4. 安装或试用

### 直接复制提示词（无需安装）

打开所需的 `SKILL.md`，阅读技能说明，将其提示词复制到支持的 AI 客户端，并按输入要求补充情境。这适合先试用单个技能。

### 安装本地插件

Codex 可在仓库根目录运行：

```bash
codex plugin marketplace add "$PWD"
codex plugin add education-agent-skills@education-agent-skills
codex plugin list --marketplace education-agent-skills --json
```

Claude Code、Hermes 和其他 Agent Skills 兼容客户端的安装步骤见 [`CODEX.md`](CODEX.md)、[`HERMES.md`](HERMES.md) 和仓库首页。客户端支持的发现方式、自动调用行为和缓存更新方式可能不同；安装成功不等于运行中的模型已经加载或选择了某个技能。

### 使用便携版

可从 [v3.1.0 发布页](https://github.com/GarethManning/education-agent-skills/releases/tag/v3.1.0)下载便携 ZIP，将所需技能的完整文件夹复制到客户端文档指定的技能目录。便携版适用于需要标准 Agent Skills 前置信息的客户端；使用已复制的技能不需要运行 Python 或 Node 构建。

### MCP

库运营的公共 MCP 服务已随 v3.1.0 退役；不要依赖旧公共端点或假设旧凭据会迁移。需要 MCP 的用户可以在本机运行服务，或自行部署并维护受控端点，具体见 [`mcp-server/README.md`](../mcp-server/README.md)。

## 5. 组合多个技能

部分技能在 YAML 中提供 `chains_well_with`，用于提示哪些技能可能适合前后衔接。例如，复习计划可与提取练习或交错练习技能组合使用。该字段是**建议**，不保证输入输出完全兼容，也不会自动执行工作流。组合前应检查各技能的输入和输出，再由教师审阅整体方案。

## 6. 证据、隐私与使用边界

- 查看每个技能列出的 `evidence_strength`、`evidence_sources` 和限制说明。库中也包含明确标注的原创或实践框架；不要把它们表述成已由研究验证的效果。
- 研究支持某个组成部分，不代表整个技能流程或 AI 输出已经通过课堂效果验证。把结果当作草稿和支持材料，而非自动成立的教学结论。
- 只提供完成任务所需的信息。避免输入学生姓名、联系方式、学号、健康或家庭情况等可识别信息；需要示例时优先使用虚构数据或汇总后的班级信息。
- 课程安排、评价结论、支持方案和学生安全相关决定仍需由适当的教育者或专业人员审阅。
- 技能库本身不保存学生档案，也不包含已实现的上下文引擎或自动编排器。个性化结果取决于你主动提供的、适当且必要的背景信息。

## 7. `skills/` 目录清单与用途

实际目录采用 `skills/<领域目录>/<技能目录>/SKILL.md` 结构。下面按领域列出全部 165 个技能目录；每项中文注释概括其用途，具体输入、证据来源、限制和输出格式请以对应的 `SKILL.md` 为准。

### `ai-learning-science/` — AI 学习科学（14 个）

- `adaptive-hint-sequence-designer/`：设计逐级提示，帮助学习者推进问题但不直接泄露答案。
- `ai-facilitated-collaborative-learning-designer/`：设计 AI 支持的小组协作任务和参与机制。
- `ai-feedback-design-principles/`：审查或改进 AI 反馈的教学质量、时机与作用。
- `cognitive-tutoring-architecture-designer/`：为智能辅导系统梳理知识组成与技能层级。
- `digital-worked-example-sequence/`：设计带逐步撤架的交互式数字例题序列。
- `erroneous-example-designer/`：设计有意设置错误的例题，训练识错与解释。
- `formative-assessment-loop-designer/`：设计根据学生每次回应调整后续教学动作的评价循环。
- `individual-spacing-algorithm-explainer/`：解释或配置依据学习表现调整的间隔算法。
- `intelligent-tutoring-dialogue-designer/`：编写包含分支回应的多轮 AI 辅导对话。
- `learning-analytics-interpretation-guide/`：把学习平台数据转化为可采取的教学决策。
- `metacognitive-monitoring-ai-contexts/`：设计检查点，帮助学生监控 AI 辅助学习中的真实理解。
- `productive-failure-desirable-difficulty-designer/`：在讲解前加入有目的的尝试与思考。
- `self-explanation-prompt-designer/`：编写提示，引导学生解释例题、文本或图示的原理。
- `worked-example-to-problem-solving-transition-designer/`：设计从看例题到独立解题的过渡。

### `ai-literacy/` — AI 素养（7 个）

- `ai-expertise-interrogation-designer/`：让学生用学科知识发现 AI 输出的扭曲、遗漏和过度自信。
- `ai-hallucination-fact-check-protocol/`：设计核查 AI 生成内容、事实和引用的流程。
- `ai-learning-boundary-mapper/`：区分作业中适合与不适合使用 AI 的环节。
- `ai-output-critical-audit-designer/`：依据批判性思维标准系统审查 AI 输出。
- `ai-socratic-dialogue-designer/`：设计多轮追问，检验 AI 回答及其修正是否可靠。
- `disciplinary-ai-literacy-sequence-designer/`：比较 AI 在不同学科问题上的表现，讨论其可靠范围。
- `prompt-literacy-sequence-designer/`：通过比较模糊与具体的提示，教授提示质量。

### `curriculum-alignment/` — 课程对齐（4 个）

- `coverage-audit/`：对照法规或认证要求检查课程覆盖情况并找出缺口。
- `curriculum-crosswalk/`：比较多个课程框架的主题覆盖和差异。
- `developmental-band-translator/`：按学校提供的发展阶段框架标注课程项目。
- `kud-chart-author/`：编写或审查“知道、理解、做到”（KUD）课程图表。

### `curriculum-assessment/` — 课程与评价（13 个）

- `assessment-validity-checker/`：检查评价的构念效度、信度及与目标的对齐。
- `backwards-design-unit-planner/`：从预期结果和评价证据反向规划单元。
- `competency-unpacker/`：把宽泛的标准或能力拆成可评估的成功标准与子技能。
- `criterion-referenced-rubric-generator/`：为任务或目标生成标准参照量规。
- `curriculum-knowledge-architecture-designer/`：梳理学科知识结构，为课程排序提供依据。
- `differentiation-adapter/`：调整课堂任务以回应学习者需要，同时保留核心目标。
- `discipline-specific-critical-thinking-task-designer/`：设计依托学科知识与推理的批判性思维任务。
- `formative-assessment-technique-selector/`：按教学时机、目的和年龄选择形成性评价方法。
- `gap-analysis-from-student-work/`：对照标准分析学生作品，定位学习差距。
- `kud-knowledge-type-mapper/`：将课程内容归入知道、理解、做到三类。
- `learning-progression-builder/`：建立从先备知识到掌握目标的学习进阶。
- `project-brief-designer/`：设计包含驱动问题、里程碑和评价标准的项目任务书。
- `scope-and-sequence-designer/`：规划课程范围、先后顺序及纵横向衔接。

### `eal-language-development/` — EAL/D 与语言发展（5 个）

- `academic-language-sentence-frame-generator/`：按语言熟练度生成学术表达句型支架。
- `language-demand-analyser/`：分析任务的语言要求及多语学习者可能遇到的障碍。
- `scaffolded-task-modifier/`：添加语言支架，同时保留任务的认知要求。
- `sheltered-instruction-lesson-modifier/`：按 SIOP 庇护式教学原则调整课程计划。
- `vocabulary-tiering-tool/`：将词汇分为日常、学术和技术层级并确定教学重点。

### `environmental-experiential-learning/` — 环境与体验式学习（6 个）

- `biophilic-learning-environment-designer/`：运用亲生命设计原则改进学习空间。
- `ecological-inquiry-anchor-designer/`：以本地生态系统为锚点设计科学或地理探究。
- `experiential-learning-cycle-designer/`：把直接体验组织成体验、反思和迁移的学习循环。
- `interdisciplinary-real-world-connection-mapper/`：围绕真实问题梳理多学科课程联系。
- `outdoor-learning-sequence-designer/`：在可用户外场地设计与课程目标相连的学习序列。
- `service-learning-project-designer/`：将真实社区需要与课程学习结合成服务学习项目。

### `explicit-instruction/` — 明确教学（5 个）

- `checking-for-understanding-protocol-designer/`：为课程各阶段设计具体的理解检查流程。
- `explicit-instruction-sequence-builder/`：从教师示范、引导练习到独立练习设计教学序列。
- `lesson-opening-designer/`：设计连接先前学习与本课内容的课程开场。
- `practice-problem-sequence-designer/`：按难度递进和策略性变化编排练习题。
- `think-aloud-script-generator/`：编写教师示范专家思考过程的口述脚本。

### `global-cross-cultural-pedagogies/` — 全球与跨文化教学法（9 个）

- `cpa-sequence-designer/`：为数学概念设计具象、图像、抽象（CPA）教学序列。
- `cross-cultural-task-validity-checker/`：检查任务中的文化偏差及跨文化适用性。
- `culturally-responsive-teaching-designer/`：将学生文化、社区知识与生活经验融入课程。
- `emergent-project-design-scaffold/`：从儿童显现的兴趣发展早期探究项目。
- `phenomenon-based-unit-anchor/`：以真实现象组织跨学科单元。
- `place-based-inquiry-anchor/`：以具体地方连接课程、社区、文化和身份。
- `reggio-documentation-protocol/`：设计记录、呈现和分享儿童学习过程的方案。
- `ubuntu-collective-knowledge-task-designer/`：设计强调共同建构知识与相互责任的学习任务。
- `variation-theory-task-designer/`：通过对比、分离和融合凸显概念关键特征。

### `historical-thinking/` — 历史思维（10 个）

- `central-historical-question-evaluator/`：判断核心历史问题能否推动基于证据的探究。
- `close-reading-skill-builder/`：训练学生从措辞、语气和修辞中读取历史视角。
- `contextualisation-skill-builder/`：训练学生把史料置于当时的时间与社会背景中理解。
- `corroboration-skill-builder/`：训练学生比较多份史料中的一致、矛盾与空缺。
- `document-based-lesson-designer/`：按史料阅读流程设计完整的文献探究课。
- `historical-document-set-curator/`：围绕核心问题选择并排序史料。
- `historical-source-adapter/`：调整史料难度与长度，同时保留分析价值。
- `historical-thinking-assessment-designer/`：设计能呈现学生历史思维过程的形成性评价。
- `historical-thinking-strategy-modelling-guide/`：用教师思维示范讲解历史分析策略。
- `sourcing-skill-builder/`：训练学生阅读前分析史料作者、时间、目的与可靠性。

### `inclusive-design/` — 包容性设计（3 个）

- `udl-barrier-anticipator/`：预判学习任务的可及性障碍，并区分设计调整与专业支持需求。
- `udl-lesson-auditor/`：按 UDL 的参与、表征、行动与表达原则审查课程。
- `udl-options-designer/`：为同一学习目标设计多种参与、表征和表达方式。

### `literacy-critical-thinking/` — 读写与批判性思维（7 个）

- `argument-structure-scaffold-generator/`：用 Toulmin、PEEL 或 CER 等框架搭建论证支架。
- `critical-thinking-task-designer/`：围绕证据评价、偏见识别或论证分析设计任务。
- `disciplinary-writing-scaffold/`：教授实验报告、历史论文等学科写作体裁。
- `media-literacy-deconstruction-protocol/`：分析媒体文本中的说服、偏见和呈现方式。
- `reading-comprehension-strategy-selector/`：按文本难点选择并排序阅读理解策略。
- `source-credibility-evaluation-protocol/`：运用横向阅读等方法核查数字信息来源。
- `text-complexity-analyser/`：从文本、读者和任务角度分析复杂度并提出支架建议。

### `memory-learning-science/` — 记忆与学习科学（8 个）

- `cognitive-load-analyser/`：发现任务中的认知负荷问题并提出设计调整。
- `dual-coding-designer/`：为语言内容设计相配的视觉表征。
- `elaborative-interrogation-generator/`：用“为什么”和“如何”问题促进深入加工。
- `feedback-quality-analyser/`：检查书面反馈的具体性、可操作性与学习价值。
- `interleaving-unit-planner/`：把分块练习改编为相关主题交错练习。
- `retrieval-practice-generator/`：为主题生成不同难度的提取练习题。
- `spaced-practice-scheduler/`：按主题和时间安排间隔复习。
- `worked-example-fading-designer/`：设计从完整例题逐步过渡到独立练习的支架撤除序列。

### `montessori-alternative-approaches/` — 蒙特梭利与其他教学路径（4 个）

- `mixed-age-learning-task-designer/`：设计能让不同年龄学生互相受益的学习任务。
- `prepared-environment-designer/`：改进教室环境，支持自主学习、平稳过渡和材料取用。
- `three-part-lesson-designer/`：用具体材料和命名设计蒙特梭利三阶段课程。
- `uninterrupted-work-cycle-designer/`：规划包含自主选择的连续工作时段。

### `original-frameworks/` — 原创框架（17 个）

- `assessment-design-orchestrator/`：在形成性、量规、表现性、同伴/自评和诊断评价路径间作选择。
- `coherent-rubric-logic-builder/`：按指定发展阶段为学习目标构建逻辑连贯的五级量规。
- `compassionate-systems-awareness-orchestrator/`：从问题或愿景组织系统探究并导向审慎行动。
- `developmental-band-system-designer/`：设计从幼儿到中学阶段的发展阶段体系。
- `developmental-progression-synthesis/`：将 KUD 图表综合为跨阶段的发展进阶矩阵。
- `dilemma-navigation-for-education-design/`：梳理教育情境中无法简单消除的价值张力与应对路径。
- `dispositional-knowledge-assessment-designer/`：设计评估好奇心、韧性等倾向性能力的多方证据方案。
- `inclusive-design-orchestrator/`：按普遍设计优先的顺序协调 UDL、差异化和个别支持。
- `learning-target-authoring-guide/`：为不同发展阶段撰写清晰、可观察的学习目标。
- `multi-perspective-decision-wheel/`：从多个视角审视设计或决策，再选择下一步行动。
- `place-based-curriculum-orchestrator/`：围绕地方、课程要求或社区议题组织地方本位课程设计。
- `regenerative-project-design-orchestrator/`：组合多种路径设计再生型项目。
- `scoping-for-transformative-learning-inquiry/`：在复杂探究前明确范围、目的、相关对象和尺度。
- `seeds-regenerative-inquiry-cycle/`：用 SEEDS 框架连接地方学习与生态意识。
- `self-determined-project-design-protocol/`：为学生自主项目设计导师检查点、能力对齐与反思。
- `single-point-rubric-designer/`：设计围绕单项标准、留出证据与反馈空间的单点量规。
- `three-horizons-learning-transition-mapper/`：用三地平线框架分析现状、愿景与转型路径。

### `professional-learning/` — 专业学习（10 个）

- `competency-framework-translator/`：将外部能力框架转化为课堂活动。
- `instructional-coaching-conversation-guide/`：准备包含问题、流程和后续行动的教学辅导对话。
- `lesson-observation-protocol-designer/`：设计聚焦的课堂观察指标与证据记录方法。
- `lesson-study-cycle-designer/`：规划从研究问题到协同备课和研究课的课例研究循环。
- `panel-review/`：用多个模拟角色审阅课程材料；其阈值是实践启发，不是验证过的门槛。
- `pedagogical-content-knowledge-developer/`：梳理主题的常见误解与有效表征，支持教学内容知识发展。
- `professional-development-session-designer/`：依据成人学习原则设计教师专业发展活动。
- `reflective-practice-prompt-generator/`：围绕教学经历或专业挑战生成结构化反思问题。
- `teacher-inquiry-cycle-designer/`：设计从研究问题、数据收集到行动改进的教师探究循环。
- `technological-pedagogical-content-knowledge-developer/`：规划技术、教学法与学科内容之间的适切整合（TPACK）。

### `questioning-discussion/` — 提问与讨论（5 个）

- `dialogic-teaching-move-generator/`：根据学生回应生成延展思考的后续教学动作。
- `discussion-protocol-selector/`：按讨论目的、主题和小组准备度选择讨论流程。
- `hinge-question-designer/`：设计能判断学生是否准备好继续学习的诊断性关键问题。
- `perspective-taking-designer/`：设计带有防止投射提醒的多视角理解活动。
- `socratic-questioning-sequence-generator/`：通过引导式问题序列发展概念理解。

### `self-regulated-learning/` — 自我调节学习（5 个）

- `error-analysis-protocol/`：诊断学生错误及误解的可能根源。
- `goal-setting-protocol-designer/`：设计结构化目标设定流程与执行计划。
- `metacognitive-prompt-library/`：按任务生成计划、监控和评价阶段的元认知问题。
- `self-regulation-scaffold-generator/`：为学习计划、过程监控和结果评价设计支架。
- `study-strategy-selector/`：按材料、目标和学习习惯选择学习策略。

### `student-learning/` — 面向学生的学习技能（13 个）

- `ai-claim-checker/`：引导学生找出 AI 回答可能出错之处并核对来源。
- `confidence-calibration-check/`：记录学习前后的信心判断，反思判断与表现的差异。
- `explain-first-interrogator/`：先让学生用自己的话解释，再由 AI 追问和反馈。
- `fading-manager/`：跟踪学习表现并随能力增长逐步撤去支架。
- `productive-failure-protocol/`：先让学生尝试复杂问题，再基于尝试进行讲解。
- `progressive-hint-ladder/`：从概念提示逐步增加到具体步骤，并要求学生先尝试和反思。
- `retrieve-first-gate/`：回答或讲解前先邀请学生回忆已有知识并报告信心。
- `srl-session-wrapper/`：以计划、监控、反思组织一段学习过程。
- `stuck-and-error-diagnosis-coach/`：先帮助学生诊断卡点或错误，再提供针对性帮助。
- `teach-back-evaluator/`：让学生向 AI 讲解概念，再通过追问发现理解缺口。
- `transfer-bridge/`：用近迁移和远迁移问题检查理解能否用于新情境。
- `unassisted-evidence-checkpoint/`：支架练习后进行无 AI 协助的检查，区分独立表现。
- `weekly-agency-review/`：依据一周学习证据回顾策略并设定下周目标。

### `systems-thinking/` — 系统思维（8 个）

- `agency-circles-for-systems-action/`：区分可控制、可影响和需关注的因素，规划适度行动。
- `aspirational-systems-iceberg/`：从愿景推演支持理想事件的模式、结构与心智模型。
- `hexagon-complexity-mapper/`：用六边形关系图呈现复杂议题中的因素及其关联主张。
- `ladder-of-inference-reflection/`：反思从观察到判断和行动之间的推理过程。
- `leverage-and-response-design/`：依据系统分析设计干预，并检查杠杆点与意外后果。
- `mental-model-mapper/`：梳理影响系统理解的信念、假设、叙事和价值观。
- `systems-awareness-iceberg/`：从事件向下分析模式、结构和心智模型。
- `systems-wellbeing-impact-mapper/`：分析影响福祉的系统因素并提出结构性应对方向。

### `wellbeing-motivation-agency/` — 福祉、动机与能动性（12 个）

- `agency-scaffold-generator/`：逐步增加学生在任务中的选择权、表达权和自主性。
- `awe-wonder-experience-designer/`：设计激发好奇心与投入感的惊奇体验。
- `belonging-classroom-culture-designer/`：针对课堂情境设计提升归属感与包容性的做法。
- `flow-state-condition-designer/`：通过调整挑战、技能、目标和反馈优化心流条件。
- `implementation-intention-designer/`：为行为目标设计“如果……就……”计划或 WOOP 方案。
- `motivation-diagnostic-task-redesign/`：诊断任务中的动机问题，并据此调整自主、胜任和联结支持。
- `perma-based-lesson-designer/`：在学科目标中融入 PERMA 福祉要素。
- `restorative-practice-protocol-designer/`：设计修复伤害、重建信任与关系的恢复性流程。
- `ruler-emotional-literacy-sequence/`：围绕识别、理解、命名、表达和调节情绪设计学习序列。
- `self-efficacy-builder-sequence/`：通过渐进的掌握体验增强学生对特定技能的自我效能感。
- `trauma-informed-practice-designer/`：设计优先考虑安全、可预测性、联结和调节的创伤知情实践。
- `wellbeing-learning-connection-mapper/`：梳理福祉项目与具体学业结果之间的证据联系。

## 延伸阅读

- [技能质量与证据说明](SKILL_QUALITY.md)
- [证据来源索引](EVIDENCE.md)
- [排除的方法及原因](EXCLUSIONS.md)
- [Codex 安装与更新](CODEX.md)
- [Hermes 安装说明](HERMES.md)
- [MCP 退役与迁移说明](HOSTED_MCP_ACCESS.md)
