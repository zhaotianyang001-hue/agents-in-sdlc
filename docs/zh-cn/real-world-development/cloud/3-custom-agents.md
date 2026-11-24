---
title: "练习 3：自定义代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## 什么是自定义代理？

[自定义代理][custom-agents-concept] 可创建针对开发流程中特定任务或领域的专用 AI 助手。通过在存储库的 `.github/agents` 文件夹中定义 Markdown 文件，可以向 Copilot 提供聚焦的指令、最佳实践、编码模式和领域知识。团队可将专业经验固化为可复用代理，例如无障碍代理、安全代理或测试代理。

每个代理文件都有至少包含 `name` 和 `description` 的 YAML frontmatter，后接定义代理行为、专业知识和指令的 Markdown 提示。

### 自定义代理与代理技能的比较

自定义代理和[代理技能][agent-skills-concept]都使用 Markdown 定义，并指导 AI 执行操作。最简洁的区分方式是：**自定义代理是执行者，技能是工具**。自定义代理拥有独立上下文窗口，并可在工作中编排技能或其他代理。

> [!NOTE]
> 自定义代理没有唯一的“正确”编写方式。应在实际环境和场景中测试并迭代。

[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[agent-skills-concept]: https://docs.github.com/copilot/concepts/agents/about-agent-skills

## 场景

Tailspin Toys 致力于让所有用户都能无障碍使用众筹平台。用户反馈显示，当前深色主题的文字与背景对比度不足。设计团队希望实现可切换的高对比度模式。

因为无障碍功能至关重要，你将使用自定义代理生成此功能。

## 审阅无障碍自定义代理

存储库已包含无障碍自定义代理。返回 codespace并审阅：

1. 打开 `.github/agents/accessibility.md`。
2. 注意包含 `name` 和 `description` 字段的 YAML frontmatter。

> [!CAUTION]
> 自定义代理的 `name` 和 `description` frontmatter 字段是必需的。

3. 查看代理定义的核心职责、无障碍最佳实践、HTML/CSS/JavaScript 示例以及常见陷阱。

## 创建并分配 Issue

任务中心是管理代理任务的中央位置。你可以分配任务、监控任务并提供额外指导。

1. 打开存储库。
2. 选择 **Issues**。
3. 选择 **New issue**，再选择 **Blank issue**。
4. 将标题设为 `Add high contrast mode to website`。
5. 将说明设为：

   ```plaintext
   We need a high contrast mode for the site. There should be a toggle for high contrast which the user can set. It should store the setting in local storage on the browser.
   ```

6. 创建 Issue。
7. 在右侧选择 **Assign to Copilot**。
8. 从自定义代理列表中选择 **Accessibility agent**。
9. 选择 **Assign**。Copilot 将在后台处理任务。

## 总结与下一步

本课展示了 GitHub Copilot 中针对特定任务定制的[自定义代理][custom-agents]。现在可以在任务中心[监控并引导代理会话][next-lesson]。

## 资源

- [关于自定义代理][custom-agents]
- [在组织中准备使用自定义代理][org-custom-agents]
- [在企业中准备使用自定义代理][enterprise-custom-agents]

---

| [← 上一课：GitHub Copilot 云代理][previous-lesson] | [下一课：监控和管理代理 →][next-lesson] |
|:--|--:|

[previous-lesson]: ../2-cloud-agent/
[next-lesson]: ../4-managing-agents/
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[org-custom-agents]: https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-organization/prepare-for-custom-agents
[enterprise-custom-agents]: https://docs.github.com/copilot/how-tos/administer-copilot/manage-for-enterprise/manage-agents/prepare-for-custom-agents
