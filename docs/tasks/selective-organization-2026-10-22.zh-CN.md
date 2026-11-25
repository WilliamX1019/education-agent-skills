# 选择性技能组织 — 2026-10-22
目标：在不改变教学法/输入/输出行为的前提下，减少最大指南中不必要的激活源文件体量；为 20 项提示性候选记录有理有据的结论。
来源：Gareth 构建授权与 `docs/audits/skill-quality-improvement-plan-2026-10-22.md` 第 4 节/第 2 阶段/附录 B。技能并非生来就太长。
检出路径 `/Users/garethmanning/Github/education-agent-skills`；分支 `codex/agent-skills-standards-quality-2026-10-22`。先前内容修复必须已通过独立审阅。你并非独自工作；勿回退他人修改。禁止子代理/提交/推送/部署/付费调用/真实学生数据。
负责：8 个最大文件及其新建的技能本地参考资料：`original-frameworks/{learning-target-authoring-guide,dispositional-knowledge-assessment-designer}`；`professional-learning/{panel-review,pedagogical-content-knowledge-developer,technological-pedagogical-content-knowledge-developer}`；`curriculum-assessment/{scope-and-sequence-designer,kud-knowledge-type-mapper,curriculum-knowledge-architecture-designer}`。路径均为 `skills/<domain>/<slug>/SKILL.md`。仅当有明确强收益时才可选处理 `KUDchartauthor`，否则保持其新修正的正文不变。
不做其他 `SKILL` 编辑。通读受影响完整文件、量规/保留记录及先前修复报告。默认原始前置元数据字节不变。绝不将执行所需的关键例外/输出契约/研究移出 MCP 核心。既有方法/schema/ID/名称不变。保留所有引用。
仅当源激活收益明确时，才将扩展示例/研究阐释移至 `references/worked-examples.md` 或类似描述性文件，并附清晰的相对 `readwhen` 指引。如有帮助，在主文件中保留紧凑代表性示例；无强制模板。除已验收的修复外，原样保留移动的文本。禁止新建 `SKILL.md` 文件、兄弟/根目录运行时依赖、隐藏资源服务器或不可访问的 MCP 参考。链接从技能根目录引用；完整文件夹复制/导出必须正常工作。
对于纯源文件移动，MCP 当前提取的 Prompt/System Prompt 必须保持精确不变。为每个编辑技能捕获修改前后提取提示词哈希；若有意缩减 `dispositionalassessment` 的 5,789 token 核心，须将所有核心方法/输出/安全边界保留在内联，记录每项有意变更与精确方法一致性；勿新增组件选择器必需输入或移除现有输出。若收益不确定，宁可保留 MCP 提示词也不要强行凑 5k 配额。
针对全部 20 条附录 B 提示性记录，基于实际正文/核心比率与内容写出 `edited`/`noclearbenefit`/`deferred` 结论及理由。当拆分会增加碎片化时，接近阈值的十四个较小正文可保留；并非 20 个都需要编辑。禁止为了数字搞一刀切删减。
检查：解析所有源文件；修改前后前置元数据一致性；纯源文件移动时 MCP 提示词一致性；移动内容保留；每个新相对链接存在；无路径逃逸；完整文件夹选择性复制；导出复制参考资料（协调现有导出测试）。工作包完成后由协调器重新生成视图。勿修改索引/打包产物或便携生成输出。
汇报 `docs/tasks/selective-organization-2026-10-22-report.md`，包含全部 20 项处置、精确源与资源映射、可用时的修改前后正文/核心 token 代理（tiktoken `o200k` 而非 Claude）、任何核心变更与局限。标明实际检查与人工阅读的区别。仅对存在未决含义/接口的增量停止；保留最小候选。
