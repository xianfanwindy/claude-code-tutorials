# 05. 项目上下文与 CLAUDE.md

Claude Code 的效果很大程度取决于它能否获得稳定、准确的项目上下文。CLAUDE.md 是记录项目级说明的推荐方式。

## CLAUDE.md 是什么

CLAUDE.md 是给 Claude Code 阅读的项目说明文件，通常放在仓库根目录。它可以记录：

- 项目技术栈
- 常用命令
- 测试方式
- 目录结构说明
- 代码风格约定
- 安全要求
- 不要做的事
- 发布或 PR 规范

## 为什么需要 CLAUDE.md

如果没有项目说明，每次会话都要重复告诉 Claude Code：

- 用什么包管理器
- 怎么跑测试
- 哪些目录不能动
- 什么是团队风格
- PR 描述怎么写

CLAUDE.md 能减少重复沟通，并让团队成员获得一致体验。

## 初始化

可以使用初始化命令：

```text
/init
```

或者直接要求：

```text
帮我为这个项目创建 CLAUDE.md，先阅读 README、package.json 和测试配置，再写简洁说明。
```

## 推荐结构

```markdown
# 项目说明

## 技术栈

## 常用命令

## 目录结构

## 开发约定

## 测试要求

## 安全注意事项

## Git 与 PR 规范

## 禁止事项
```

## 示例

```markdown
# CLAUDE.md

## 常用命令

- 安装依赖：npm install
- 启动开发环境：npm run dev
- 类型检查：npm run typecheck
- 单元测试：npm test

## 开发约定

- 优先修改已有文件，不为简单逻辑引入新抽象。
- 不要提交 .env 或任何密钥文件。
- 前端交互改动必须启动应用并在浏览器验证。

## Git 规范

- 未经明确要求不要 commit。
- 未经明确要求不要 push。
- PR 描述必须包含 Summary 和 Test plan。
```

## 写 CLAUDE.md 的原则

### 只写长期有效的信息

适合写入：

- 项目命令
- 架构约定
- 测试要求
- 安全边界

不适合写入：

- 临时 bug 状态
- 某个未完成任务的细节
- 已经过期的分支信息
- 可以从代码直接看出的琐碎路径列表

### 简洁胜过冗长

Claude Code 会优先使用明确、可执行的规则。过长的背景故事反而降低效果。

### 用命令而不是描述

不好：

```markdown
测试可以正常运行。
```

好：

```markdown
运行单元测试：npm test
运行类型检查：npm run typecheck
```

## 多层 CLAUDE.md

在大型仓库中，可以在根目录和子目录分别放 CLAUDE.md。根目录记录全局规则，子目录记录局部规则。

例如：

```text
CLAUDE.md
apps/web/CLAUDE.md
services/api/CLAUDE.md
```

## 团队维护建议

- 把 CLAUDE.md 纳入 code review
- 当测试命令变化时同步更新
- 删除过期规则
- 明确危险操作边界
- 让新成员先阅读 CLAUDE.md
