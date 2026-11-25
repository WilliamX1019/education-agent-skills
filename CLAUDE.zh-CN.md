# Education Agent Skills Library — Claude Code 入口指南

## 项目简介
跨 20 个领域、共 165 个循证教育技能，用于课程设计、备课规划、评价设计及面向学生的 AI 学习支持。采用 CC BY-SA 4.0 协议。支持 Claude Code、Claude.ai（通过 MCP）、OpenAI Codex 与 Hermes Agent。包含本地/自托管 MCP 源码、CoWork 插件（`.claude-plugin/`）、Codex 插件（`.codex-plugin/`）、便携版 Agent Skills 下载包以及 Hermes 选择性安装指南。由本库运营的公共 MCP 服务随 v3.1.0 退役，不再提供公开注册。

## 技术栈
TypeScript（77.9%）、Python（16.7%）。测试使用 Playwright。技能采用带有 YAML 前置元数据的结构化 Markdown（`SKILL.md`）。MCP 服务器位于 `mcp-server/` 子目录。通过 GitHub Actions 执行 CI。

## 测试命令
`npx playwright test`

## 会话开始时必读
1. `STATE.md` — 当前构建状态。若不存在，记录其缺失并继续，切勿凭猜测创建——应在会话结束时根据已验证的工作创建。
2. 本文件
3. `README.md` — 安装方式、技能格式、架构说明
4. `ARCHITECTURE.md` — 三层系统设计
5. `EVIDENCE.md` — 证据强度评级与方法论
6. `EXCLUSIONS.md` — 刻意排除的内容及原因

## 关键构建工作流
在新增或编辑**任何**技能后，提交前必须执行以下三步：
1. `python3 scripts/generate-registry.py` — 重新生成 `registry.json`
2. `cd mcp-server && npm run bundle-skills && cd ..` — 重新构建 `mcp-server/src/skills.json`
3. 暂存全部三个文件：`SKILL.md`、`registry.json` 以及 `mcp-server/src/skills.json`
如果打包产物与技能文件不同步，CI 将会失败。MCP 服务器提供的是预构建快照——未重新打包的修改即使在 Vercel 重新部署后也不会在线上生效。

## 20 个领域
`ai-learning-science`、`ai-literacy`、`curriculum-alignment`、`curriculum-assessment`、`eal-language-development`、`environmental-experiential-learning`、`explicit-instruction`、`global-cross-cultural-pedagogies`、`historical-thinking`、`inclusive-design`、`literacy-critical-thinking`、`memory-learning-science`、`montessori-alternative-approaches`、`original-frameworks`、`professional-learning`、`questioning-discussion`、`self-regulated-learning`、`student-learning`、`systems-thinking`、`wellbeing-motivation-agency`

## 核心规范
- 每个技能必须引用具名研究——不得存在没有证据基础的技能
- 证据强度评级：`strong`（强）、`moderate`（中等）、`emerging`（新兴）或 `original`（原创，如实标注）
- 强制要求 YAML schema 头部字段：`skill_id`、`domain`、`evidence_strength`、`evidence_sources`、`input_schema`、`output_schema`、`chains_well_with`
- 技能存放于 `skills/<domain>/<skill-name>/SKILL.md`
- 原创框架（第 15 领域）须清晰标注为“实践者原创（practitioner-originated）”
- 编排器/复合型技能（Orchestrator/composite skills）必须始终包含：Evidence Space（证据空间）、Component Evidence（组件证据）、Synthesis Evidence（综合证据）、Appropriate Use（适用范围）和 Dependency Maintenance（依赖维护）章节。在未经独立测试前，复合路径须始终标注为 `emerging`。

## 提交命令
`git add -A && git commit -m "[description]" && git push`

## STATE.md
在仓库根目录维护。会话结束时更新：已完成事项、已验证事项、下一步计划。将 `STATE.md` 与功能开发工作分开提交。

### Second Brain 保存规范
在任何产生重要提交或改变项目状态的会话结束后，通过 MCP（`secondbrain-lemon-alpha.vercel.app/mcp`）向 Second Brain 保存一条上下文记忆，说明已发布内容、变更点及下一步计划。每次保存必须包含：
1. 内容中的项目名称（例如："Strive: shipped new analytics dashboard"）
2. 内容最后一行写明 `"Source: [this repo name]"`
3. 在 `note` 字段中填写 `"project: [slug]"`

该记录将输入每 2 小时运行一次的项目实体编译器。如果保存内容中未提及项目名称，它将不会被编译进实体页面。
