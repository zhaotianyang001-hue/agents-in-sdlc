---
title: "练习 5：迭代 GitHub Copilot 的工作"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← 上一课：管理代理][previous-lesson] |
|:--|

## 审阅工作

在本实验中，你让 GitHub Copilot 完成了多项改进用户体验和功能的任务，包括添加文档、构建相关游戏功能，以及实现高对比度和浅色模式。接下来审阅代码更改，并在必要时向 Copilot 提供反馈。

## 安全性与云代理

由于云代理异步且无人实时监督地执行任务，GitHub 已实施安全限制：

- Copilot 只能读取存储库，只能写入用于生成代码的分支。
- 云代理在 GitHub Actions 中运行，并使用独立的临时环境。
- 所有 GitHub Actions 工作流都需要人工批准。
- 默认限制对外部资源的访问，包括 MCP 服务器。

## 审阅生成的文档

1. 返回存储库，打开由云代理创建的第一个 PR。
2. 选择 **Files changed**，审阅 TSDoc 注释、TypeScript 规范和文件注释头。
3. 棡查所有更改符合预期后，返回 **Conversation**。
4. 如果工作流等待批准，选择 **Approve and run workflows**。

   ![批准并运行工作流](../../../_images/shared-approve-workflows.png)

## 向 Copilot 请求修改

可在 PR 或代码行内评论中使用 `@copilot` 请求变更，例如：

- 为每个代码文件顶部添加简短的注释头；
- 为 TypeScript 和 Astro 文件添加 TSDoc 注释；
- 创建说明 Astro 应用结构的 README。

提交评论后，Copilot 会启动新会话并创建新的提交。审阅后可将草稿 PR 转为可审阅状态并合入 `main` 分支。

## 审阅相关游戏功能

打开标题类似于 **Show related games on the game details page** 的 PR，审阅数据访问辅助函数、详情页区域、空结果处理和单元测试。

可在本地切换到 Copilot 创建的分支并运行应用：

```bash
git fetch origin
git checkout <branch-name>
```

## 审阅无障碍功能

审阅由无障碍自定义代理实现的高对比度模式和浅色模式，重点检查：

- 模式切换 UI；
- 使用本地存储保存偏好；
- 高对比度和浅色模式的 CSS；
- ARIA 属性和键盘导航；
- 管理模式切换的 JavaScript/TypeScript。

可切换到相应分支，在浏览器中测试两种模式及页面刷新后的持久化。

> [!NOTE]
> 若发现无障碍问题，可在评论中 `@copilot` 请求更新。

## 可选练习：继续委派任务

- 创建游戏详情页上的支持者兴趣表。
- 为游戏列表页实现分页。
- 为数据访问辅助函数添加输入验证和错误处理。

## 总结

你已完成云代理学习路径，实践了：

- 检查自定义指令及其对云代理输出的影响；
- 将 Issue 异步分配给云代理；
- 创建并使用无障碍自定义代理；
- 使用代理页面监控和引导会话；
- 审阅拉取请求并通过评论迭代。

## 资源

- [GitHub Copilot][github-copilot]
- [关于 Copilot 代理][copilot-agents]
- [将 GitHub Issue 分配给 Copilot][assign-issue]
- [云代理设置工作流最佳实践][cloud-agent-best-practices]
- [配置云代理防火墙][agent-firewall]

[github-copilot]: https://github.com/features/copilot
[cloud-agent-overview]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[setup-workflow]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[agent-firewall]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-firewall
[previous-lesson]: ../4-managing-agents/
