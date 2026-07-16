---
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git commit:*)
description: 创建一个 git 提交
---

## 上下文

- 当前 git 状态：!`git status`
- 当前 git diff（已暂存与未暂存的改动）：!`git diff HEAD`
- 当前分支：!`git branch --show-current`
- 最近的提交记录：!`git log --oneline -10`

## 你的任务

基于上述改动，创建一个 git 提交。

**提交信息规则：**
- 如果当前分支为 `dev`，提交信息必须以 `#relese#` 结尾，用于触发自动升级。
- 其他分支不要附加 `#relese#`。

你可以在单次回复中调用多个工具。请在一条消息内完成暂存并创建提交。不要使用任何其他工具或执行其他操作，除了这些工具调用外不要发送任何其他文本或消息。
