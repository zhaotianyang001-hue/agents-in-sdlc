---
slug: zh-cn/real-world-development/cloud
title: "GitHub Copilot 云代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

**[GitHub Copilot 云代理](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)** 可让 GitHub Copilot 在云端异步处理任务。你在 GitHub 上分配工作，云代理会在后台探索存储库、修改文件并创建拉取请求，而你可以继续处理其他事务。

在这些练习中，你将添加云代理遵循的自定义指令、分配 GitHub Issue，并让代理实现相应工作。你将审阅并使用自定义代理来调整其处理方式，在代理仪表板中监控和引导会话，最后审阅拉取请求并迭代处理结果。

## 练习

| 练习 | 主题 | 说明 |
|----------|-------|-------------|
| [0. 先决条件][ex0] | 设置 | 创建存储库和 codespace |
| [1. 自定义指令][ex1] | 上下文 | 添加云代理遵循的自定义指令 |
| [2. 云代理][ex2] | 异步代理 | 将 Issue 分配给 Copilot 云代理 |
| [3. 自定义代理][ex3] | 专用代理 | 审阅并使用自定义代理 |
| [4. 管理代理][ex4] | 监控 | 监控并引导代理会话 |
| [5. 迭代][ex5] | 审阅 | 审阅 PR、迭代 Copilot 的工作并选择后续步骤 |

## 先决条件

参加本工作坊前，请确保：

- [ ] 拥有有效的 **Copilot Student、Pro、Pro+、Business 或 Enterprise** 计划的 GitHub 账户
- [ ] 已为你的账户或组织启用 Copilot 云代理

> [!TIP]
> 没有付费计划？通过验证身份的学生可通过 [GitHub Education][callout-student-plan-education] 免费获得 GitHub Copilot。**Copilot Student** 计划包含本工作坊使用的代理、MCP、代码审查和 Copilot CLI 功能，因此可用它完成全部练习。

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> 云代理适用于 **Copilot Student、Pro、Pro+、Business 和 Enterprise**；只有 Copilot Free 不包含。使用 Copilot Business 或 Enterprise 时，管理员需要为组织启用。

> [!NOTE]
> 此学习路径不涵盖 MCP。若要探索 MCP 服务器，请参阅 [CLI 学习路径](../cli/) 或 [VS Code 学习路径](../vscode/)。

## 开始学习

**[从练习 0：先决条件开始 →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
