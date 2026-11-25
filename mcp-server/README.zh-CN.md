# Education Skills MCP 服务器

将 [Education Agent Skills](https://github.com/GarethManning/education-agent-skills) 技能库暴露为可调用工具与提示词的 MCP 服务器。涵盖跨 20 个领域的 165 个循证教育技能，以及 4 个发现工具。

由本库运营的公共 MCP 服务随 [v3.1.0](../docs/releases/v3.1.0.md) 退役；不再提供公开注册。请使用本地 stdio 或自行运营经认证的 HTTP 端点。现有仅支持远程连接的客户端需要更换为自建端点或受支持的本地/手动使用路径；凭据与客户端设置不会自动迁移。详见[迁移指南](../docs/HOSTED_MCP_ACCESS.md)与 [Codex 配置](../docs/CODEX.md)。

## 架构

所有技能均注册为提示词（Prompts）。允许模型调用的技能同时注册为工具（Tools）：

- **工具（Tools）**（共 157 个：153 个技能 + 4 个元工具）— 适用于 Claude.ai 及任意 MCP 客户端。标记为 `disable-model-invocation: true` 的 12 个技能刻意未注册为工具。
- **提示词（Prompts）**（165 个）— 所有技能均保持可发现且可用于显式提示词调用，包括上述 12 个不作为模型自动调用工具的技能。

### 元工具（始终作为工具提供）

| 工具 | 用途 |
|------|------|
| `list_skills` | 按领域分组浏览所有技能 |
| `get_skill_details` | 获取特定技能的完整元数据（证据来源、schema、串联信息） |
| `find_skills` | 按标签、领域、证据强度或自由文本搜索 |
| `suggest_skills` | 用自然语言描述教学问题，获取 3–5 个相关技能推荐 |

## 本地运行（stdio）

```bash
cd mcp-server
npm ci
npm run build
npm start
```

请在同时包含 `skills/` 和 `mcp-server/` 的源码检出目录中运行以上命令，并确保已安装 Node.js 与 npm。`npm ci` 会安装锁定版本的依赖；`npm start` 以 stdio 模式运行并保持连接，直到客户端关闭或你按下 Ctrl-C。本地 stdio 无需配置 Vercel、Bearer 令牌、OAuth 密钥、公共基础 URL 或邮件服务商。你的 AI 客户端自身的模型/数据处理条款仍然适用。

对于支持基于命令的 stdio 的桌面端 MCP 客户端，可将其指向构建后的源码服务器：

```json
{
  "mcpServers": {
    "education-skills": {
      "command": "node",
      "args": ["/absolute/path/to/mcp-server/dist/index.js"]
    }
  }
}
```

## 开发命令

```bash
npm run dev          # 使用 tsx 运行（无需构建步骤）
npm run build        # 编译 TypeScript
npm test             # 运行 Playwright 测试套件
npm run bundle-skills # 重新生成用于 Vercel 部署的 src/skills.json
```

## 自托管 HTTP

对于仅接受远程 MCP 的客户端（包括仅支持远程连接的 Claude 连接器），请使用支持相关路由的平台部署你自己的保留 `api/` 处理程序副本，并配置你自己的规范 HTTPS 源站、认证机制与经批准的客户端重定向地址。源码中包含 Vercel 路由配置，但本仓库的 `vercel.json` 设置了 `git.deploymentEnabled: false`：Git 推送不会自动触发 Vercel 部署。运营者必须主动选择并授权自己的部署流程。参见 [Vercel 的 Git 配置文档](https://vercel.com/docs/project-configuration/git-configuration)。GitHub 下载或本地安装无需任何托管部署。

使用 Streamable HTTP 将你的远程客户端连接到**你自己的源站加上 `/mcp`**。客户端必须支持服务器的认证流程；本地测试成功并不代表真实的 OAuth 连接一定可用。请勿将已退役的公共源站或旧服务凭据用作自托管配置。

在你的分支中启用注册/邮件功能前，请将 `src/access.ts` 中的遗留公共注册常量替换为你自己的访问申请 URL，并审阅 `api/request-access.ts`：发件人显示名称、回复地址、邮件正文及文档链接均保留了原运营者的品牌信息。请配置你自己的已验证发件人与邮件服务商参数。仅靠环境变量无法修改所有遗留的品牌/联系字符串。在向他人提供服务前，请发布你自己的隐私声明并测试完整流程。这些源码路由仍保留供自托管者使用；公共技能库注册服务已退役。

### 环境变量

以下 HTTP/认证/邮件配置仅适用于自托管端点，不适用于本地 stdio。

| 变量 | 说明 |
|------|------|
| `SKILLS_FILTER` | 用于本地 `dist/index.js` 源文件加载器的可选领域过滤器；并非托管访问设置。 |
| `MCP_PUBLIC_BASE_URL` | 托管端点所需的规范 HTTPS 源站。绝不信任请求中的 `Host` 头。 |
| `MCP_TOKEN_SIGNING_SECRET` | 用于新签发 30 天有效期访问令牌的必需私有随机密钥（至少 32 字节）。现有已签名令牌仍与其签发配置保持兼容。 |
| `MCP_OAUTH_SIGNING_SECRET` | 可选的独立随机 OAuth 密钥（至少 32 字节）。新 OAuth 凭据会使用它；验证时也接受令牌签名密钥。 |
| `MCP_OAUTH_REDIRECT_URIS` | 可选的以逗号/换行分隔的精确重定向白名单（在 Claude 回调之外额外允许的地址）。 |
| `MCP_REVOKED_TOKEN_HASHES` | 可选的以逗号/换行分隔的单个访问或刷新凭据的 SHA-256 哈希列表，用于在不轮换全局密钥的情况下吊销特定凭据。 |
| `MCP_ACCESS_TOKEN_HASHES` / `MCP_ACCESS_TOKENS` | 用于运营者签发的哈希/明文令牌的兼容输入。新签发均采用带过期时间的签名令牌。 |
| `RESEND_API_KEY` | 仅在你启用访问邮件投递时需要。服务商失败会返回错误，而不会暴露服务商详情、申请者数据或凭据片段。 |
| `MCP_FROM_EMAIL` | 启用访问邮件时你自己的已验证发件地址；源码中的回退值为服务商测试地址。 |

托管 OAuth 要求使用 S256 PKCE 与经批准的回调地址。授权码经过加密与认证，绑定至客户端和重定向地址，10 分钟后过期，并在当前服务实例内拒绝重放。新的刷新凭据经过加密，30 天后过期，并在使用时轮换。Bearer 凭据仅通过 `Authorization` 请求头接受。

该实现未引入持久化的共享存储。速率限制与一次性重放缓存均为每个无服务器实例尽最大努力（best-effort）维护；无法完全排除请求被路由到另一活跃实例时的重放可能。短生命周期、加密、PKCE 绑定、精确重定向校验、凭据轮换及单个吊销列表在不假装具备全局有状态存储的前提下降低了这一残余风险。

## 技能工具的工作原理

1. 教师（或 Claude）携带必需参数调用技能工具
2. 服务器加载该技能的循证提示词模板
3. `{{placeholder}}` 占位符被替换为传入的值；未提供的可选参数变为 `[not provided]`
4. 组装后的提示词被包装在指令框架中，并作为工具结果返回
5. 调用该工具的 Claude 模型遵循指令并生成结构化输出

## 许可证

[CC BY-SA 4.0](https://creativecommons.org/licenses/by-sa/4.0/) — 详见 [LICENSE](../LICENSE)。
