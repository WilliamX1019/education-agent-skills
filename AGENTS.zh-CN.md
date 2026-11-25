# AGENTS.md — 面向本仓库代码代理的指南

本仓库是一个包含跨 20 个领域、共 165 个循证教育技能的技能库，已打包支持在 Claude Code、Claude.ai（通过 MCP）、OpenAI Codex、Hermes Agent 以及任何兼容 Agent Skills 的工具中使用。

## 技能结构

技能位于 `skills/<domain>/<skill-name>/SKILL.md`。请勿移动或重命名技能文件夹。

## 规范约定

- 完整保留所有 YAML 前置元数据（frontmatter）字段——请勿删除或重命名任何字段（`skill_id`、`domain`、`evidence_strength`、`evidence_sources`、`input_schema`、`output_schema`、`chains_well_with` 等）
- 保留证据引用——每条 `evidence_sources` 记录必须引用具名研究（作者、年份、研究发现）
- 请勿将循证指导弱化为泛泛的通用建议
- 在处理基础设施、测试或文档时，请勿修改 `SKILL.md` 的正文或前置元数据

## 测试命令

```bash
npm test
```

## 新增或编辑任何技能后的操作

MCP 服务器提供的是预构建快照——在重新构建并提交打包产物之前，对 `SKILL.md` 文件的修改不会在在线服务器上生效：

```bash
python3 scripts/generate-registry.py
cd mcp-server && npm run bundle-skills && cd ..
git add skills/<domain>/<skill-name>/SKILL.md registry.json mcp-server/src/skills.json
```

如果打包产物与技能文件不同步，CI 将会失败。
