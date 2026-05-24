# 10. MCP 服务器集成

MCP 是 Model Context Protocol，用于把 Claude Code 连接到外部工具和数据源。通过 MCP，Claude Code 可以访问 GitHub、数据库、文档系统、监控平台、内部 API 等。

## MCP 解决什么问题

没有 MCP 时，Claude Code 主要依赖本地文件和 shell 命令。

有 MCP 后，可以接入：

- GitHub issue / PR
- Jira / Linear
- Confluence / Notion
- 数据库
- 日志和监控
- 云平台
- 内部服务

## MCP 的基本概念

| 概念 | 含义 |
| --- | --- |
| MCP Server | 暴露工具和资源的服务 |
| Tool | 可调用操作，例如查询 issue |
| Resource | 可读取资源，例如文档或记录 |
| Client | Claude Code 作为 MCP 客户端调用 server |

## 适合接入 MCP 的场景

### 需求和任务系统

让 Claude Code 读取 issue、任务描述、验收标准。

```text
读取这个 Linear ticket，总结需求和待确认问题。
```

### GitHub 协作

读取 PR 评论、CI 状态、review 反馈。

```text
查看 PR 评论，列出需要修改的点。
```

### 文档系统

读取内部设计文档或 API 规范。

```text
根据设计文档检查当前实现是否一致。
```

### 数据库和监控

用于排查问题，但要严格控制权限。

```text
查询最近 1 小时相关错误日志，只读操作。
```

## 安全注意事项

MCP 可能连接敏感系统，必须控制：

- 认证方式
- 访问范围
- 只读/写权限
- 审计日志
- 输出脱敏
- 是否允许生产环境操作

不要给 Claude Code 默认写入生产系统的权限。

## 配置建议

### 使用最小权限 token

为 MCP server 准备专用 token，只授予必要范围。

### 区分环境

开发、测试、生产使用不同配置。

### 明确工具名称

工具描述要清晰，避免 Claude Code 误用。

### 对写操作加审批

例如创建 issue、评论 PR、修改数据库等，应需要用户确认。

## MCP 与 WebFetch 的区别

| 能力 | WebFetch | MCP |
| --- | --- | --- |
| 公网页面 | 适合 | 也可 |
| 私有系统 | 通常不适合 | 适合 |
| 认证 | 有限 | 可定制 |
| 写操作 | 不适合 | 可实现但需谨慎 |
| 结构化工具 | 弱 | 强 |

## 常见 MCP 用例

- GitHub PR 管理
- Jira ticket 查询
- Postgres 只读查询
- Sentry 错误查询
- Datadog 指标查询
- 内部知识库搜索
- 云资源只读查看

## 设计 MCP 工具的好习惯

- 工具名表达动作和对象
- 参数明确且有限
- 默认只读
- 输出结构化
- 错误信息清晰
- 对敏感字段脱敏
- 写操作要求确认或二次验证

## 提示词示例

```text
使用 GitHub MCP 查看当前 PR 的 review 评论，按文件归类，不要修改代码。
```

```text
用监控 MCP 查询 checkout API 最近 30 分钟错误率，只读查询。
```

```text
根据文档 MCP 中的支付 API 规范，检查本地实现是否有字段不一致。
```
