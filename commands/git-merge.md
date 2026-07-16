---
allowed-tools: Bash(git checkout:*), Bash(git branch:*), Bash(git merge:*), Bash(git push:*), Bash(git status:*)
description: 将当前分支合并到指定分支（参数：目标分支名）
---

## 上下文

- 当前 git 状态：!`git status`
- 当前分支（源分支）：!`git branch --show-current`
- 目标分支：$ARGUMENTS

## 你的任务

将当前分支的代码合并到指定的目标分支（由参数 `$ARGUMENTS` 提供）。步骤：

1. 记录当前分支名（源分支），稍后需要切回
2. 切换到目标分支：`git checkout <目标分支>`
3. 合并源分支：`git merge <源分支>`
4. 将目标分支推送到 origin：`git push`
5. 切回源分支：`git checkout <源分支>`

**注意事项：**
- 如果 `$ARGUMENTS` 为空（未提供目标分支），停止并提示用户提供目标分支名，不要继续。
- 如果目标分支与源分支相同，停止并报告，不要继续。
- 如果合并出现冲突，不要强制提交；报告冲突并停止，等待用户手动处理。

你可以在单次回复中调用多个工具完成上述操作。不要使用任何其他工具或执行其他操作。
