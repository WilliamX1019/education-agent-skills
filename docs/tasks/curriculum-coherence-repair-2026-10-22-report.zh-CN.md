# 课程连贯性修复回执 — 2026 年 10 月 22 日

状态：**三个文本值已修复；范围内检查通过；独立复核待定。** 此为源码连贯性证据，而非模型输出试验、实证验证、集成或发布。

检出路径：`/Users/garethmanning/Github/education-agent-skills`；分支 `codex/agent-skills-standards-quality-2026-10-22`；继承基线 `6bbbce418f82e11044009c9f3b7373a354de5bd0` 连同先前的工作区编辑。负责人增量：仅限 `skills/curriculum-alignment/developmental-band-translator/SKILL.md` 中的两个现有输入描述值、`skills/memory-learning-science/retrieval-practice-generator/SKILL.md` 活跃输出模板中的一句话以及本回执。现有工作已保留。未发生任何子代理、提交、推送、部署、生成文件更新、完整测试套件运行、付费模型调用或托管请求。未启动任何服务器或后台进程。

## 授权与替代关系

已通读 `AGENTS.md`、`CLAUDE.md`、`STATE.md`、有界修复简报、原课程任务/报告、独立审阅回执、质量计划第 5 节以及两个受影响文件的全文。修复简报明确仅授权这两个阶段输入描述元数据值作为原始元数据冻结的例外，外加 MCP 提示词中的单句提取时机表述。初始独立审阅仅报告了两项实质性发现。

本回执**仅就这两个文件取代 `docs/tasks/curriculum-evidence-2026-10-22-report.md` 中的两个候选文件哈希以及连贯性/一致性推论**。该早期报告中披露的冻结阶段元数据与经限定的示例时机并未消除元数据/模板之间的冲突主张。其历史记录保持不变；其中的其他文件哈希与发现不在本次修复范围内。本回执在下方提供修正后的候选哈希与更窄的验证声明。独立验收仍待完成。

## 精确文本变更

1. `input_schema.required` → `progression_structure_json` → `description`：

   修改前：“The harness-produced progression_structure.json for the source. Must include band_labels, source_type, and age_range_hint (or per-band approximate_age_range). If both age-range fields are absent, the skill returns request_age_range_context in skill_flags and halts.”

   修改后：“The harness-produced progression_structure.json for the source. Must include band_labels and source_type. Use user_age_range_override first, otherwise native age_range_hint or per-band approximate_age_range; if neither exists for a flat competency/dispositional framework, use tentative descriptor-based mapping with low confidence and teacher review. Return request_age_range_context in skill_flags and halt only when no route supports a defensible mapping; do not invent ages.”

2. `input_schema.optional` → `user_age_range_override` → `description`：

   修改前：“Explicit age-range mapping supplied by the user when a source has no native band structure (flat list). Required only when the skill emits a request_age_range_context error.”

   修改后：“Explicit user-supplied age-range mapping, available on the first invocation or after request_age_range_context. Apply before native age ranges or flat-framework descriptor mapping; preserve native labels and ages, record user-supplied provenance in skill_flags, and flag conflicts with native ages for teacher review.”

3. 提取技能活跃 MCP 输出模板示例，仅第一句时机表述：

   修改前：“Use 3–7 days after initial teaching for optimal spacing effect.”

   修改后：“Use 3–7 days after initial teaching as a practical starting point; adapt timing to prior learning, retrieval success, retention goals and the timetable.”

   紧随其后的一句保持原样不变：“Re-use a subset at 2–4 weeks for a second retrieval opportunity.” 输出依然提供可执行的间隔与后续重温建议，同时允许灵活调整而不再断言存在普适最优解。

## 保留其余部分与检查

编辑前快照位于 `/tmp/curriculum-coherence-repair-before-20261022/{developmental-band-translator,retrieval-practice-generator}/SKILL.md`；其哈希与早期报告的候选哈希一致。一次性结构检查脚本 `/tmp/check-curriculum-coherence-repair-20261022.py` 使用 YAML 解析、原始文本相等性比对以及当前加载器的提示词提取模式，将快照与当前文件进行对比。它不通过关键词存在性测试编辑质量。

命令：`/tmp/education-skills-audit-20261022/venv/bin/python /tmp/check-curriculum-coherence-repair-20261022.py` — **首次运行即通过（PASS）**：

- 两个 YAML 头部均能正常解析。在仅移除两处获批的描述值后，阶段元数据在语义上完全一致；原始头部行比对仅发现那两行描述发生了变化。每个键、类型、必需/可选位置、默认值、ID、引用、输出与调用控制均得以保留。
- 阶段转换器的整个 Markdown 正文与提取出的活跃 MCP 提示词按字节完全一致。现有步骤、示例、来源原始表述规则、映射方法、低置信度/教师审阅标志以及最大跨度 LT 聚合均保持完整。
- 提取技能的整个文件与修改前快照完全相同，仅存在前述那一句替换。其原始头部/schema/引用按字节完全一致。其活跃提示词仅相差那一句。初学者/热身识别例外、所教来源核查、自检项、示例与局限性均保持精确不变。
- 两个文件中所有模板变量的出现次数及其顺序均未改变。两个活跃提示词均成功提取且非空；Markdown 代码块围栏配对平衡。

命令：`git diff --check -- skills/curriculum-alignment/developmental-band-translator/SKILL.md skills/memory-learning-science/retrieval-practice-generator/SKILL.md docs/tasks/curriculum-coherence-repair-2026-10-22-report.md` — **通过（PASS）**。由于报告为新增/未追踪文件，还直接检查了其尾随空格/制表符及文件末尾换行符。未针对三个文本值重跑完整基准测试或全套测试。

## 虚构文本走查

以下为基于现有步骤与修正后描述的推理阅读，而非运行时/模型测试或学习者观察。

- **原生年龄，常规案例：** 具备必需 `band_labels`/`source_type`、原生年龄 5–11 且无覆盖映射的进阶结构走原生年龄路径。对照学校阶段 A 5–7 / B 7–9 / C 9–11，保留 A/B/C 歧义、低置信度与教师审阅。元数据不再要求走与核心不同的路径。
- **首次调用即提供覆盖映射及冲突：** 用户在首次调用时即提供 8–10 映射。两处描述均立即允许该用法；第 1 步在原生范围之前应用它。原生标签与年龄保持不变，用户来源记录在 `skill_flags` 中，与原生年龄的任何冲突均触发教师审阅。无需先强制触发错误。
- **无年龄或覆盖的扁平框架：** 具备合适描述子的胜任力/倾向性来源进入保守的描述子路径。指派结果标注为暂定、低置信度且需教师审阅。模糊的描述子会保留所有合理候选阶段并请求教师上下文；不捏造年龄常模。
- **不支持的来源：** 既无原生年龄、无覆盖映射又无合理描述子路径的非扁平来源请求 `request_age_range_context`、不做标注并中止。必需的进阶输入本身仍为字符串；缺失的内部年龄不会变成新的强制 schema 字段。
- **提取练习，常规案例：** 规划复习的教师可从教学后 3–7 天起步，并在 2–4 周时重用部分题目。活跃输出模板现已与示例及局限性表达相同的实用/可调定位。
- **提取练习，时机或初学者边界：** 课表中断、回忆较弱或不同的记忆保持目标均可在不与“最优”声明相矛盾的前提下调整首次间隔。初学者仍可获得标注清楚的识别类热身支持；仅提供主题的答案仍作为待教师对照所教材料核查的学科知识草案。这些既有核心规则保持不变。

在此有界增量中不存在未决的教育/接口含义或失败的修复循环。描述子映射与课堂时机仍需要教育者专业判断；本源码检查仅确立内部连贯性。协调器负责独立复核以及后续所有重新生成、集成与分发工作。

## 精确 SHA-256 回执

| 文件 | 修复前 | 修复后 |
|---|---|---|
| `skills/curriculum-alignment/developmental-band-translator/SKILL.md` | `1aa99b15c4e3c932543f5d12fd41536e6ccb2be27939e7cbd607c8aeb8c83205` | `57d1d93eccdc656dcc37fef5901aea76b66919ee46996b9f2a36b0de44d172b2` |
| `skills/memory-learning-science/retrieval-practice-generator/SKILL.md` | `efaa81eda3c33e47ab898556d2d93a40022f09f479375421dd736557dd341f28` | `e55101e427042173034785a11d3acc42d0532c27317d46bf0b89870ac092feeb` |

阶段转换器正文（修复前后）：`531e927b6ba55a72c5b40576c7e4ef9c9ead23fc00a3d77f1d543d7ac028ff92`。

阶段转换器活跃提示词（修复前后，去除首尾空白的加载器提取结果）：`0acbe4e274495bb9749e167e75a876d4f73c35d36fc77c0eddc0dd122cf712d5`。

提取练习原始头部（修复前后，含分隔符）：`174593f3b99b935d8bc97c073866777277e9e6abb06249471d6bc5488106751b`。

提取练习活跃提示词修复前：`81788d36208be40f6fc6566a125d12b0fd38d3e74e2a515f852734606b639670`；修复后：`77a689b150b3c009e03635805a796147fa7c85bab429eeab18c378fd51b775fe`。
