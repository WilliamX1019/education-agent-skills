# 安全 MCP 运行时与可复现包 — 2026-10-22
目标：在不修改教育内容的前提下，实施经审计的安全解析/运行时可靠性修复。
来源：Gareth：“let’s proceed with this build”；计划 `docs/audits/agent-skills-migration-plan.md` Q0/Q1/Q2-C3/P2 包新鲜度。
检出路径 `/Users/garethmanning/Github/education-agent-skills`；分支 `codex/agent-skills-standards-quality-2026-10-22`；基线 `6bbbce418f82e11044009c9f3b7373a354de5bd0`。
负责：构建者负责 `mcp-server/src/skill-loader.ts`、`tool-handler.ts`、`server.ts`、`oauth.ts`；`mcp-server/package{,-lock}.json`；必要的聚焦 `mcp-server/tests/*` 与包/`LICENSE`；若运维限制需澄清则包括 `docs/HOSTED_MCP_ACCESS.md`。
受保护：`skills/**`、`registry.json`、`src/skills.json` 内容、根目录文档/readme、插件清单、根目录测试。协调器正在编写独立简报；你并非独自工作。勿回退他人编辑。禁止子代理。
通读 `AGENTS.md`、计划相关章节、运行前阅读实际源码/测试。禁止学习者数据/密钥/托管调用/部署；禁止提交/推送/发布。本范围就本次仅限本地构建取代技能默认的提交/推送指令。
1 安全前置元数据：要求普通 `---` 起始/闭合、非执行式 YAML 解析器，拒绝 `js`/`javascript`/自定义标签/可执行分隔符。精确保留全部 165 条解析元数据与提取提示词。若不再需要则移除 `gray-matter`，而非降级。
2 依据最新注册表/安全通告证据，将 SDK 刷新至至少 1.32 的兼容修复版本及锁文件/传递依赖。安装前检查依赖生命周期钩子；绝不使用 `npm audit fix --force`。设置与 1 MiB 上限兼容的显式合理 `maxToolInputElements`。避免无关大版本升级。
3 将不安全的字符串替换替换为使用回调函数与字面量键对原始占位符 token 的单遍扫描，保持原有大小写不敏感行为；包含 `$&`、`{{literal}}`、正则键文本的输入不会被二次解释。保留现有输入摘要。
4 移除不受支持的 OAuth `client_id_metadata_document_supported` 通告；保留固定客户端流程。在不构建共享持久化的前提下记录单令牌对比家族吊销以及单实例重放限制。
5 添加 `prepack` 本地构建新鲜度检查与打包 CLI 临时冒烟测试（无 npm 发布、无网络模型调用）；确保无需绝对源路径。许可证仅复制现有条款，不重新授权。
检查：`mcp-server` 基线/最终 `npm run build` 与 `npm test` 并附摘要；解析器安全夹具 + 全部 165 项深度一致性；字面量占位符测试；合法最大/有界超限 SDK 测试；现有认证/协议计数 165 提示词 / 157 工具 / 12 仅显式；`npm audit --audit-level=high`；可行时 `npm pack` 至临时目录并执行打包 CLI 握手。
勿打印含凭据的环境/进程参数。所有启动的服务器/进程必须停止。
停止条件：同一问题连续失败两次、未批准的接口含义、需要付费服务/线上部署或不安全操作；报告具体阻塞项，保留安全的独立修复。
汇报 `docs/tasks/safe-mcp-runtime-2026-10-22-report.md`，包含结果、变更文件、命令/计数、实际依赖/通告结果、保留的一致性、剩余局限与回滚。禁止捏造验证。
