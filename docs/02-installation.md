# 02. 安装与登录

本章介绍 Claude Code 的安装、登录和初始检查。不同系统的具体命令可能会变化，实际以官方文档和当前 CLI 输出为准。

## 前置条件

建议准备：

- macOS、Linux、WSL 或受支持的 Windows 环境
- Node.js 或官方安装方式所需运行时
- Git
- 一个 Anthropic / Claude 账号
- 可访问目标代码仓库的权限

## 安装思路

Claude Code 通常通过官方推荐方式安装。安装完成后，你应该能在终端中运行：

```bash
claude --version
```

如果命令不存在，检查：

- 安装是否成功
- 终端是否重新打开
- PATH 是否包含 Claude Code 可执行文件目录
- 当前 shell 配置是否生效

## 登录

首次使用通常需要登录：

```bash
claude
```

CLI 会引导你完成认证。某些环境可能需要浏览器打开登录页面，远程服务器或 WSL 环境下要注意浏览器跳转和回调地址。

## 在项目中启动

进入项目目录后运行：

```bash
claude
```

Claude Code 会以当前目录作为主要工作目录。建议始终在仓库根目录启动，这样它能正确读取：

- Git 状态
- package.json、pyproject.toml、go.mod 等项目文件
- CLAUDE.md
- 测试配置
- 项目脚本

## 初始检查命令

进入 Claude Code 后，可以先问：

```text
这个项目是什么技术栈？先只阅读，不要修改文件。
```

也可以让它检查：

```text
查看项目里是否有 CLAUDE.md、README、测试命令和 lint 命令。
```

## 常见目录选择

| 场景 | 推荐启动位置 |
| --- | --- |
| 单仓库项目 | 仓库根目录 |
| monorepo | monorepo 根目录，或目标 package 目录 |
| 只改前端 | 前端应用根目录 |
| 只改后端 | 后端服务根目录 |
| 文档项目 | 文档根目录 |

如果从错误目录启动，Claude Code 可能无法找到 Git 仓库、测试命令或项目说明。

## API Token 与环境变量

有些工作流会用到环境变量，例如 GitHub token、云服务 token 或内部工具 token。

原则：

- 不要把 token 写入仓库
- 不要让 Claude Code 打印完整 token
- 使用最小权限 token
- 定期轮换 token
- 对生产环境 token 更谨慎

如果需要使用环境变量，可以让 Claude Code 只检查变量是否存在，而不是输出值：

```text
检查 GITHUB_TOKEN 是否存在，不要打印它的内容。
```

## 安装后的验证

建议验证以下能力：

1. 能启动 Claude Code
2. 能读取当前项目文件
3. 能查看 Git 状态
4. 能运行一个只读命令
5. 能在用户批准后创建或修改测试文件
6. 能运行测试命令

## 团队安装建议

团队落地时，可以统一：

- 推荐版本
- 项目 CLAUDE.md
- 权限策略
- hooks 策略
- 常用 MCP 配置
- 禁止事项清单

这样能减少每个成员重复配置的成本。
