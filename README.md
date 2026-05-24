# Claude Code 中文系统教程

这是一套面向中文用户的 Claude Code 系列教程，按主题分类介绍安装、日常开发、权限配置、自动化、MCP、子代理、记忆系统、GitHub 协作、安全实践和故障排查。

Claude Code 是 Anthropic 官方的命令行智能编程助手，适合在真实项目中完成代码阅读、修改、测试、提交、PR、排查和自动化协作。

## 适合读者

- 第一次使用 Claude Code 的开发者
- 希望把 Claude Code 纳入日常工程流的团队
- 想理解 hooks、MCP、skills、agents、memory 等高级能力的用户
- 需要建立安全、可审计 AI 编程流程的工程负责人

## 教程目录

### 基础入门

1. [认识 Claude Code](docs/01-introduction.md)
2. [安装与登录](docs/02-installation.md)
3. [第一个项目工作流](docs/03-first-workflow.md)
4. [常用命令与交互方式](docs/04-cli-commands.md)

### 工程实践

5. [项目上下文与 CLAUDE.md](docs/05-project-context.md)
6. [文件编辑、测试与验证](docs/06-edit-test-verify.md)
7. [Git、提交与 Pull Request 工作流](docs/07-git-github.md)
8. [权限、安全边界与审批](docs/08-permissions-security.md)

### 高级能力

9. [Hooks 自动化](docs/09-hooks.md)
10. [MCP 服务器集成](docs/10-mcp.md)
11. [Skills 技能系统](docs/11-skills.md)
12. [Agents 与子代理](docs/12-agents.md)
13. [Memory 记忆系统](docs/13-memory.md)
14. [计划模式、工作树与长任务](docs/14-advanced-workflows.md)

### 团队与生产化

15. [团队协作最佳实践](docs/15-team-practices.md)
16. [安全审查与防御性使用](docs/16-security-review.md)
17. [常见问题与排错](docs/17-troubleshooting.md)
18. [速查表](docs/18-cheatsheet.md)

## 推荐学习路径

### 新手路径

按顺序阅读 01 到 08，重点掌握：

- 如何启动 Claude Code
- 如何让它理解项目
- 如何安全修改代码
- 如何运行测试和提交变更

### 进阶路径

阅读 09 到 14，重点掌握：

- 用 hooks 自动执行检查
- 用 MCP 连接外部系统
- 用 skills 扩展能力
- 用 agents 并行探索大型代码库
- 用 memory 保留长期偏好和项目背景

### 团队落地路径

阅读 15 到 18，重点掌握：

- 如何定义团队规范
- 如何控制权限和风险
- 如何审查 AI 生成代码
- 如何排查常见问题

## 基本原则

使用 Claude Code 时，建议遵守以下原则：

1. **先理解，再修改**：让 Claude Code 阅读代码、解释现状，再动手。
2. **小步提交**：每次变更聚焦一个目标，便于 review 和回滚。
3. **验证真实行为**：测试通过不等于功能正确，尤其是前端和交互功能。
4. **谨慎授权**：只允许必要命令，危险操作必须确认。
5. **保留项目上下文**：用 CLAUDE.md 记录团队约定，而不是每次重复说明。
6. **把 AI 当协作者**：明确目标、边界、验收标准和风险偏好。

## 术语速览

| 术语 | 含义 |
| --- | --- |
| Claude Code | Anthropic 官方 CLI 编程助手 |
| CLAUDE.md | 项目级说明文件，记录架构、命令、约定 |
| Tool | Claude Code 可调用的能力，例如读文件、运行命令、编辑文件 |
| Permission | 工具调用权限控制，决定哪些操作需要用户批准 |
| Hook | 在特定事件前后执行的自动化脚本 |
| MCP | Model Context Protocol，用于连接外部工具和数据源 |
| Skill | 可安装/可调用的专用能力包 |
| Agent | 专门执行某类任务的子代理 |
| Memory | 跨会话保存用户偏好、项目背景和参考信息的机制 |
| Plan mode | 先调研并写计划，用户批准后再实现的模式 |

## 维护建议

这套文档可以随着 Claude Code 功能变化持续更新。建议团队在实践中补充：

- 本项目常用命令
- 权限白名单
- hooks 配置
- PR 模板
- 安全审查流程
- 常见问题记录
