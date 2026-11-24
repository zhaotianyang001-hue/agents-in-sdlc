---
title: "练习 2：GitHub Copilot 云代理"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← 上一课：自定义指令][previous-lesson] |
|:--|

技术债务几乎存在于每个组织中。它可能表现为未解决的安全问题、需要更新的旧代码，或因缺少时间而长期积压的功能请求。[GitHub Copilot 云代理](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent) 可更新代码并添加功能。代理完成工作后，会生成供人类开发人员审阅的草稿 PR，因此开发人员可以把繁琐任务交给代理，把精力集中在更大的工作上。

## 场景

Tailspin Toys 需要处理技术债务。原先创建网站的承包商没有补充文档，首要任务是为应用中所有导出的函数添加 TSDoc 注释。

设计团队还希望改进游戏发现体验：在每款游戏的详情页展示同一类别的相关游戏，以便用户继续浏览。此功能只需用于体验与验收测试，无须完成最终打磨。

## 云代理简介

[GitHub Copilot 云代理](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent#overview-of-copilot-cloud-agent-formerly-copilot-coding-agent) 可在后台执行任务，方式类似人类开发人员。[将 GitHub Issue 分配给 Copilot](https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions) 后，Copilot 会创建草稿 PR、设置环境并开始处理任务。你可以在会话进行中或完成后查看进度；解决方案就绪后，Copilot 会在 PR 中提醒你。

## 设置云代理的开发环境

云代理使用 [GitHub Actions][github-actions] 运行工作环境。可通过 `.github/workflows/copilot-setup-steps.yml` 中的 [自定义设置工作流][setup-workflow] 安装工具和依赖。实验室已预先配置该工作流，使其能够访问 Node.js、项目依赖、端到端测试所需浏览器，以及迁移并填充后的 SQLite 数据库：

```yaml
name: "Copilot Setup Steps"

on: workflow_dispatch

env:
  ASTRO_TELEMETRY_DISABLED: "1"

jobs:
  copilot-setup-steps:
    runs-on: ubuntu-latest
    permissions:
      contents: read
    steps:
      - name: Checkout code
        uses: actions/checkout@v5

      - name: Set up Node.js
        uses: actions/setup-node@v6
        with:
          node-version: "lts/*"
          cache: "npm"
          cache-dependency-path: "./package-lock.json"

      - name: Install JavaScript dependencies
        run: npm ci

      - name: Install Playwright browsers
        run: npx playwright install --with-deps chromium

      - name: Migrate + seed the local SQLite database
        run: npm run db:setup
```

## 添加文档

1. 在新浏览器标签页中打开存储库。
2. 选择 **Issues** 选项卡。
3. 选择 **New issue**。
4. 选择 **Blank issue**。
5. 将标题设为 `Code lacks documentation`。
6. 将说明设为：

   ```plaintext
   Our organization has a requirement that functions and methods include TSDoc doc comments where helpful. Unfortunately, recent updates haven't followed this standard. We need to update the existing code to ensure doc comments are included where they clarify behavior.
   ```

7. 创建 Issue。
8. 在右侧选择 **Assign to Copilot**。
9. 选择 **Assign**。
10. 等待 Copilot 创建草稿拉取请求并开始工作。

## 添加相关游戏区域

可继续将第二个任务分配给云代理：

1. 创建标题为 `Show related games on the game details page` 的 Issue。
2. 在说明中要求：

   ```markdown
   We want to help people discover more games by showing related games on each game's details page. The design team wants to explore the UX and do some acceptance testing. Our requirements are:

   - Add a data-access helper in `src/lib/` that returns other games in the same category as a given game, excluding that game
   - Show a "Related games" section on the game details page that uses the helper
   - Handle the case where a game has no related games
   - There should be unit tests created for the new helper
   - Before creating the PR, ensure all tests pass
   ```

3. 创建 Issue 并分配给 Copilot。

Copilot 正在处理第二个请求时，可继续下一课，创建并使用自定义代理。

## 总结与下一步

本课展示了 [GitHub Copilot 云代理][copilot-agents]。你了解了环境设置、明确范围的重要性，以及如何将 Issue 异步分配给 Copilot。接下来将 [创建并使用自定义代理][next-lesson]。

## 资源

- [关于 Copilot 云代理][copilot-agents]
- [将 GitHub Issue 分配给 Copilot][assign-issue]
- [云代理设置工作流最佳实践][cloud-agent-best-practices]

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-custom-agents/
[cloud-agent-mcp]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/extend-cloud-agent-with-mcp
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
[setup-workflow]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[cloud-agent-best-practices]: https://docs.github.com/copilot/how-tos/copilot-on-github/customize-copilot/customize-cloud-agent/customize-the-agent-environment
[github-actions]: https://docs.github.com/actions
