# 11. Skills 技能系统

Skills 是 Claude Code 的专用能力包。它们把某类任务的流程、知识和工具调用方式封装起来，让 Claude Code 在特定场景下更可靠。

## Skill 适合什么场景

- 重复性流程
- 有固定规范的任务
- 需要专门知识的任务
- 团队希望标准化的操作

例如：

- 初始化 CLAUDE.md
- 审查 PR
- 安全审查
- 配置 hooks
- 运行并验证应用
- Claude API 开发指导

## 使用方式

Skills 通常通过 slash command 触发：

```text
/review
```

```text
/security-review
```

```text
/init
```

也可以用自然语言触发某些技能，例如：

```text
帮我审查这个 PR。
```

## Skills 与普通提示词的区别

| 对比 | 普通提示词 | Skill |
| --- | --- | --- |
| 适用范围 | 任意任务 | 特定任务 |
| 流程稳定性 | 依赖模型判断 | 更标准化 |
| 团队复用 | 较弱 | 强 |
| 工具使用 | 临时决定 | 可内置流程 |

## 发现 Skills

如果你想知道是否有某类 skill，可以问：

```text
有没有适合配置键盘快捷键的 skill？
```

或：

```text
帮我找一个能做依赖升级检查的 skill。
```

## 常见内置或可用 Skills

### init

初始化 CLAUDE.md，帮助 Claude Code 理解项目。

### review

审查 Pull Request。

### code-review

审查当前 diff，寻找正确性问题。

### security-review

审查安全风险。

### run / verify

启动应用并验证功能。

### update-config

修改 Claude Code 设置，例如权限、hooks、环境变量等。

### claude-api

用于 Claude API / Anthropic SDK 应用开发、调试和迁移。

## 什么时候应该使用 Skill

当任务有明确专用流程时，优先使用 skill。

例如，用户说：

```text
帮我验证这个改动真的能用。
```

比起普通回答，更适合调用验证相关 skill。

## 团队自定义 Skills

团队可以把常见流程做成 skill，例如：

- 发布前检查
- 数据库迁移审查
- 移动端提测流程
- 依赖安全扫描
- 内部 PR 模板生成

## Skill 使用建议

- 明确输入范围
- 明确是否允许修改代码
- 明确是否允许外部操作
- 明确输出格式
- 对高风险 skill 加权限确认

## 示例提示词

```text
用安全审查 skill 检查当前分支的改动。
```

```text
用运行验证 skill 启动应用，并确认设置页保存按钮可用。
```

```text
帮我找一个能减少权限提示的 skill。
```
