# 07. Git、提交与 Pull Request 工作流

Claude Code 可以协助完成 Git 状态检查、diff 总结、提交、推送和 PR 创建。由于这些操作会影响版本历史和远程仓库，需要明确授权。

## 基本原则

- 未经明确要求，不要 commit
- 未经明确要求，不要 push
- 不要默认 force push
- 不要跳过 hooks
- 提交前查看 status 和 diff
- 优先添加具体文件，不要盲目 `git add .`

## 查看状态

```text
查看当前 git status 和 diff，总结有哪些改动。
```

Claude Code 应关注：

- 修改文件
- 新增文件
- 删除文件
- 已暂存改动
- 未跟踪文件
- 是否存在敏感文件

## 创建提交

```text
为当前改动创建一个提交，不要 push。
```

好的提交信息应该说明意图，而不仅是文件变化。

例如：

```text
Fix session persistence after page reload
```

而不是：

```text
Update auth files
```

## 推送

推送会影响远程仓库，应明确说：

```text
提交并推送到当前分支。
```

如果是新分支，需要设置 upstream。

## 创建 PR

```text
创建一个 PR，目标分支是 main，标题简短，描述包含 Summary 和 Test plan。
```

推荐 PR 描述：

```markdown
## Summary

- Fix session restoration after reload
- Add regression test for persisted auth state

## Test plan

- [x] npm test -- auth
- [x] npm run typecheck
```

## 审查当前 diff

```text
审查当前 diff，重点关注正确性 bug，不要修改代码。
```

或：

```text
做安全审查，重点关注注入、鉴权、敏感信息泄漏。
```

## 处理 hooks 失败

如果 pre-commit hook 失败，不要跳过。应修复问题后重新提交。

不推荐：

```bash
git commit --no-verify
```

推荐：

```text
分析 hook 失败原因，修复后重新创建提交。
```

## 避免误提交

提交前检查：

- `.env`
- 私钥
- token
- 大型二进制文件
- 本地缓存
- debug 日志
- 临时截图

可以要求：

```text
提交前检查是否有敏感文件或不该提交的临时文件。
```

## 分支策略

常见策略：

| 场景 | 建议 |
| --- | --- |
| 小 bug fix | 当前 feature 分支提交 |
| 新功能 | 新建 feature 分支 |
| 实验性修改 | worktree 或临时分支 |
| 紧急修复 | 从 release/main 切 hotfix 分支 |

## Force push

force push 可能覆盖他人工作。只有在明确知道影响范围时才使用，并避免对 main/master 强推。

如果确实需要：

```text
解释为什么需要 force push，会影响哪个分支，先不要执行，等我确认。
```

## GitHub Token

如果使用 GitHub API 或 CLI：

- 使用环境变量保存 token
- 不要打印 token
- token 权限最小化
- 对组织仓库遵守团队安全策略

## 常用提示词

```text
查看当前分支相比 main 的所有提交和 diff，判断 PR 还缺什么。
```

```text
根据当前 diff 写 PR 描述，但不要创建 PR。
```

```text
创建 PR 后返回 PR URL。
```
