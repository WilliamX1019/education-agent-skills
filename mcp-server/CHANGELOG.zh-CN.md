# 更新日志

## 0.3.0

- **混合架构**：技能同时注册为 MCP 工具（共 111 个：107 个技能 + 4 个元工具）和 MCP 提示词（107 个）。工具可在 Claude.ai 和未来的编排器中使用；提示词则适用于 Claude Desktop 及支持展示提示词的客户端。
- 技能工具返回结果采用指令包装框架，使调用它的 Claude 模型直接执行该技能，而非输出原始提示词文本。
- 未提供的可选 `{{placeholder}}` 参数会被替换为 `[not provided]`，而不会以原始模板语法的形式出现。

## 0.2.0

- 将 107 个技能从工具迁移至 MCP 提示词。保留 4 个元工具（`list_skills`、`get_skill_details`、`find_skills`、`suggest_skills`）。因 Claude.ai 界面不展示 MCP 提示词，该变更在 v0.3.0 中回退。

## 0.1.0

- 首次发布。通过 stdio 传输提供 111 个 MCP 工具（107 个技能 + 4 个元工具）。
- 支持使用 Streamable HTTP 传输及无状态 JSON 响应模式的 Vercel 部署。
- 技能加载器在启动时解析上级仓库 Markdown 文件中的 YAML 前置元数据。
- 提供 `SKILLS_FILTER` 环境变量用于限制加载的领域范围。
- Playwright 测试套件：9 项测试，覆盖启动、领域分组、技能推荐、提示词组装、输入校验、名称冲突与领域过滤。
