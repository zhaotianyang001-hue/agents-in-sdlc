---
title: "第 2 课：添加星级评分：快速取胜"
description: "使用 Copilot CLI 对游戏卡片进行小幅修改，在转发的浏览器中审阅，并将其作为第一个拉取请求合并。"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

现在已安装 Copilot CLI，可以开始对项目进行第一次修改。先做一个小而集中的改动：游戏数据已有星级评分，但首页的游戏卡片尚未展示。你将让代理显示评分、审阅改动并合并第一个拉取请求。

在本课中，你将：

- 在功能分支上开始一次集中式 Copilot 对话；
- 请求代理对项目做小幅修改；
- 使用 `/diff` 审阅改动；
- 在转发的浏览器中运行应用并确认改动；
- 创建并合并第一个拉取请求。

## 场景

Tailspin Toys 中的每款游戏都有星级评分，而且详情页已展示该评分。首页卡片目前只显示标题、类别、出版商和说明。本练习将让代理在每张卡片上显示现有评分。

## 开始对话并请求改动

1. 返回 codespace。
2. 使用终端快捷键打开终端：<kbd>Control</kbd>+<kbd>\`</kbd>（Mac）或 <kbd>Ctrl</kbd>+<kbd>\`</kbd>（Windows/Linux）。
3. 启动 Copilot：

   ```bash
   copilot --yolo
   ```

4. 使用 `/new` 启动新会话。
5. 输入以下提示词：

   ```plaintext
   Show each game's starRating out of 5 in the game cards on the list page. If the rating is null, show "No rating yet". Keep the card layout as it is, add tests, and run the relevant checks.
   ```

Copilot 会探索项目、找到游戏卡片组件并创建必要的代码。

## 审阅差异

1. 输入 `/diff` 并审阅每个更改的文件。
2. 确认有评分时显示数值；`starRating` 为 `null` 时显示 `No rating yet`。
3. 确认测试覆盖上述两种状态。
4. 检查 Copilot 运行的检查结果，如有失败请让它修复。

> [!NOTE]
> 所有生成式 AI 工具都具有概率性，因此实际实现可能有所不同，应审阅行为而不是追求唯一实现。

## 检查改动

1. 请求 Copilot 启动应用：

   ```plaintext
   Start the app so I can inspect the star-rating change in my browser. Tell me the URL and leave the server running.
   ```

2. 当 Codespaces 映射端口 `4321` 后，选择 **Open in Browser**。
3. 确认游戏卡片会显示五分制评分。

## 创建并合并拉取请求

1. 请求默认代理提交改动。
2. 输入 `/pr create` 创建拉取请求。
3. 审阅更改和检查。
4. 准备就绪后选择 **Merge pull request**。
5. 使用 `/exit` 离开 CLI。
6. 更新本地 `main`：

   ```bash
   git checkout main
   git pull
   ```

## 总结与下一步

恭喜，你已使用 Copilot CLI 完成并合并第一个改动。接下来将[开始使用筛选 Issue 并采用规划与自动驾驶模式][next-lesson]构建更大的功能。

## 资源

- [关于 GitHub Copilot CLI][about-copilot-cli]
- [Copilot CLI 命令参考][cli-reference]

[previous-lesson]: ../1-install-copilot-cli/
[next-lesson]: ../3-agent-modes/
[about-copilot-cli]: https://docs.github.com/copilot/concepts/agents/about-copilot-cli
[cli-reference]: https://docs.github.com/copilot/reference/copilot-cli-reference/cli-command-reference
