---
title: "第 12 课：使用 GitHub Pages 部署网站"
description: "使用 GitHub Copilot app 配置 Pages 工作流、审阅拉取请求并验证已上线的 Space Quiz。"
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

通过 GitHub Pages 部署，让 Space Quiz 获得公开访问地址。Copilot 可以准备工作流并指导部署，但仍由你负责审阅更改并确认网站已上线。

在本课中，你将：

- 请求 Copilot 配置 GitHub Pages 部署；
- 合并前审阅工作流和拉取请求；
- 跟踪部署并验证已发布的网站。

## 场景

Space Quiz 已位于 GitHub 存储库中，但需要一种简单方式让其他人试用。通过 GitHub Pages 发布这个单文件网站，无需添加服务器或运行时依赖，即可通过公开 URL 访问。

## 请求 Copilot 准备部署

> [!WARNING]
> 创建拉取请求可能会提交并推送代码。发送提示词前，请审阅批准设置和目标存储库。启用 **Approve all** 后，可能不会再出现单独确认提示。

在 `space-quiz` 的 Copilot app 会话中发送：

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## 审阅工作流和拉取请求

1. 确认只有在仓库尚无 README 时才添加 README。
2. 审阅拉取请求中的更改，包括工作流的构建、部署步骤、触发器和权限。
3. 确认工作流只从默认分支部署，而不是从未合并的拉取请求部署。
4. 请求必要的修正并审阅更新后的差异。等待必需的 PR 棉查通过后再授权合并。

## 授权合并和部署

> [!WARNING]
> 以下提示词授权代理合并已审阅的拉取请求、修改存储库的 Pages 设置并发布网站。只有完成审阅并确认存储库及拉取请求后才发送。审批设置可能允许这些操作而不再提示。

将 `<PR_NUMBER>` 替换为已审阅的拉取请求编号，然后发送以下提示词：

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![三阶段示意图：已合并的 space-quiz 拉取请求；成功运行的 GitHub Actions Deploy website，包含 Build website、Upload artifact 和 Deploy to Pages 步骤；以及位于 yourname.github.io/space-quiz/ 的在线 Space Quiz。](../../../_images/first-steps-app-pages-deploy.svg)

## 验证部署

1. 跟踪 GitHub Actions 部署运行直至成功。
2. 打开报告的 URL，并确认 Space Quiz 可正常加载。

如果代理无法启用 Pages 或合并拉取请求，请按其提供的具体说明操作。只有部署成功且在线网站可加载后，才算完成任务。

## 总结与下一步

你的 Space Quiz 已作为在线网站发布，并且你亲自验证了部署，而不是仅依赖代理的报告。继续阅读 [第 13 课：审阅与下一步][next-lesson]。

[next-lesson]: ../13-review/
