# 便携版 Agent Skills 配置文件与客户端安装 — 2026-10-22
目标：在不修改扩展源文件的前提下，交付全部 165 个现有技能的确定性、可通过官方校验器的导出包，并修正 Codex 本地安装/显式控制与 CI 校验。
来源：Gareth“let’s proceed with this build”；`agent-skills-migration-plan.md` S0/S1/C0/C1 与质量计划第 4/5/7 节。
检出路径 `/Users/garethmanning/Github/education-agent-skills` 分支 `codex/agent-skills-standards-quality-2026-10-22`。基线 `6bbbce4`；先前的运行时安全工作包为当前状态，予以保留。
负责文件：`scripts/export-standard-skills.py`（新建）；`scripts/validate-standard-skills.py`（若有用则新建）；`tests/test_standard_export.py` 或等效测试；`.agents/plugins/marketplace.json`；12 个 `skills/**/agents/openai.yaml` 附属文件；`.github/workflows/validate.yml`；`.gitignore`；需要时的 `requirements` 标准校验文件；`docs/CODEX.md`。
受保护文件：现有 `SKILL.md` 正文/前置元数据、README 引导（后续文档工作包）、`mcp-server` 源码/包/测试、`registry.json`、生成打包产物、先前审计产物。你并非独自工作；绝不回退他人修改。禁止子代理/提交/推送/发布/部署，禁止修改真实 Codex/Claude 设置。
通读 `AGENTS.md` 与相关计划；调用前先检查位于 `/tmp/education-skills-audit-20261022/standard/skills-ref` 的实际官方参考工具源码。Python 工具环境 `/tmp/education-skills-audit-20261022/venv` 已导入 `skills_ref` 与 PyYAML。固定上游 `69ef37e9424c0a7ea9dd2293b559e43ec8176379` `skills-ref 0.1.0`。
1 导出生成被忽略的 `dist/agent-skills/<slug>/SKILL.md`。仅包含标准 `name`/`description`/`license` 与字符串值命名空间元数据；完整原始富元数据保存在 `references/education.json` 中，并在原始正文前添加确定性 schema 指引；正文后缀按字节保留。完整保留当前元数据/ID、CC-BY-SA-4.0 与 `LICENSE`。不扁平化规范源文件编辑。
2 安全复制技能本地的 `references`/`scripts`/`assets`/`agents` 附属文件，拒绝路径穿越/符号链接逃逸与重复名称。新授权的未追踪资源也必须一并复制。拒绝破坏性覆盖任意用户目录；仅安全替换由导出器自身拥有的输出。相同源文件产生确定性输出；源文件内容哈希标识工作区编辑，而非宣称仅 Git HEAD 为被评估内容。
3 测试验证 165 个唯一目录；完整元数据往返；原始正文保留；许可证/资源/附属文件复制；重复运行哈希一致；独立复制的技能可正常工作；畸形/冲突/路径穿越测试夹具。官方校验通过 165/165 外加 `to-prompt` 165。添加使用精确上游提交的固定官方工具 CI 门禁；项目校验保持独立；勿静默让扩展源文件在官方校验器下亮绿灯。
4 市场 `source.path` 设为 `./`；现有清单保持领域数组不变。仅为 12 个源文件 `disable=true` 技能创建 `agents/openai.yaml` `policy.allow_implicit_invocation: false`。确保附属文件复制到便携配置文件；其余 153 个技能无误设策略。测试等价性。
5 `docs/CODEX`：实际注册 + `codex plugin add education-agent-skills@education-agent-skills`；已测试 CLI 版本、新会话/重载行为、领域数组正确、源对比便携选择，且更新说明避免假定插件缓存自动刷新。已核验当前 `codex 0.163.0-alpha.11.1` 帮助。仅在隔离的 `CODEX_HOME`/配置/缓存中测试注册/添加/列表，不复制凭据、不付费执行或触及真实设置；若需登录则勿称其已验证。
6 CI 只读权限；可行时将 Actions 固定到独立核验的修订版；固定 Python 工具依赖；导出+往返+官方门禁；不新增外部部署工作流。保留现有源文件/打包产物/测试。勿放宽测试/跳过实际缺陷。
检查：自身测试、若触及预期则跑根目录测试、运行导出两次比对一致性、官方校验 165 与 `to-prompt`；明确记录隔离 Codex 命令结果。汇报 `docs/tasks/portable-standard-profile-2026-10-22-report.md`（五句话摘要加命令/计数/局限）。停止所有后台进程。
同一问题连续失败两次或需未批准的契约/真实安装变更时停止；保留具体证据并保持独立进展。禁止付费 API/模型调用。
