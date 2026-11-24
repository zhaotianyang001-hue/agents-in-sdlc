---
title: "练习 4：监控和管理代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

在前面的练习中，你让 Copilot 云代理处理了多个任务。云代理虽然会异步自主运行，但监控任务仍然很重要。[GitHub.com 上的代理页面][agents-page] 是任务控制中心，可查看所有带开放拉取请求的代理任务、检查操作并引导进行中的会话。

在本课中，你将：

- 使用代理页面监控云代理任务；
- 引导进行中的会话以添加更多功能。

## 场景

团队让代理实现高对比度模式后，又决定添加浅色模式。由于工作正好涉及网站样式和切换功能，便希望代理同时实现浅色模式。

## 审阅云代理任务

1. 打开 [Copilot 代理页面](https://github.com/copilot/agents)。
2. 查看主区域和左侧窗格中的任务，例如：
   - 更新代码库文档；
   - 为游戏生成修改用 API；
   - 为网站添加高对比度模式。
3. 选择一个正在运行的任务，审阅 Copilot 执行过的步骤。

> [!NOTE]
> 列出的步骤会随 Copilot 的工作状态和采用的方法而变化。

4. 查看右侧的拉取请求窗格，可监控其更改的文件和 PR 状态。

## 引导云代理

1. 选择与高对比度模式相关的会话。

   ![任务控制中心中的无障碍会话](../../../_images/ex6-accessibility-session.png)

2. 等待会话完成环境设置并开始工作。
3. 在 **Steer active session while Copilot is working** 对话框中输入：

   ```plaintext
   While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
   ```

   ![代理页面中突出显示引导会话对话框的截图](../../../_images/ex6-steer-cloud-agent-task.png)

4. 按 <kbd>Enter</kbd> 发送提示。
5. Copilot 会确认并将此要求纳入工作流程。

## 总结与下一步

本课介绍了 Copilot 代理页面——监控和引导云代理任务的任务控制中心。接下来将[审阅并迭代 Copilot 创建的拉取请求][next-lesson]。

## 资源

- [Copilot 代理页面][agents-page]
- [关于自定义代理][custom-agents]

---

| [← 上一课：自定义代理][previous-lesson] | [下一课：迭代 Copilot 的工作 →][next-lesson] |
|:--|--:|

[previous-lesson]: ../3-custom-agents/
[next-lesson]: ../5-iterating/
[agents-page]: https://github.blog/changelog/2025-07-03-agents-page-for-copilot-coding-agent-in-public-preview
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
