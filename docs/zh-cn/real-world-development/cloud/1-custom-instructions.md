---
title: "练习 1：自定义指令（云代理）"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← 上一课：先决条件][previous-lesson] · [下一课：Copilot 云代理 →][next-lesson]

使用生成式 AI 时，上下文至关重要。如果任务必须按特定方式完成，或 Copilot 应了解某些背景信息，应确保这些上下文可供使用。[指令文件][instruction-files] 用于提供此类指导，使 Copilot 不但知道你想做什么，还知道你希望如何完成。

在本练习中，你将：

- 探索项目级上下文、编码规范和文档标准如何通过存储库自定义指令和按路径限定的指令文件传递给 Copilot；
- 在 `.github/copilot-instructions.md` 中添加一项全新存储库标准。

> [!NOTE]
> 与 VS Code 和 CLI 学习路径不同，此处不会运行前后对比提示词：Copilot 云代理会在 GitHub Issue 上异步工作，难以实时并排展示影响。稍后审阅云代理创建的拉取请求时，会看到指令文件产生的效果。

## 指令文件

### 场景

Tailspin Toys 有一套开发规范，包括：

- 数据层始终需要单元测试。
- UI 应采用深色模式并具有现代感。
- 文档应以 TSDoc 注释形式添加到代码中。
- 每个文件的开头应包含说明该文件用途的注释块。

通过指令文件，可确保 Copilot 获取所需信息并遵循这些实践。

## 探索项目中的自定义指令

花一点时间阅读此存储库附带的指令文件：一个核心的 `copilot-instructions.md` 和多个面向不同任务的 `*.instructions.md` 文件。

1. 打开 `.github/copilot-instructions.md`。
2. 记录项目简介以及 **Agent notes**、**Code standards**、**Scripts** 和 **Repository Structure** 等章节。
3. 打开 `.github/instructions` 文件夹，查看 Astro、Drizzle 数据层、测试等指令。
4. 打开 `.github/instructions/unit-tests.instructions.md`，注意顶端的 `applyTo` 字段；它使用 glob 限定指令适用范围。
5. 最后查看 `.github/instructions/drizzle.instructions.md` 底部的链接。较大的指令集可拆分成可复用的小文件，并指向项目中的示例。

> [!NOTE]
> Copilot 会使用存储库级和带 `applyTo` frontmatter 的 `*.instructions.md` 文件生成代码。

## 添加新的存储库标准

本练习唯一需要编辑的地方，是添加一项项目级规则：使用 TSDoc 注释和文件级注释头记录代码文档。云代理处理后续 Issue 时会读取该规则。

1. 从 codespace 终端创建并切换到新分支：

   ```bash
   git checkout -b custom-instructions-cloud
   ```

2. 重新打开 `.github/copilot-instructions.md`。
3. 找到 **Code formatting requirements** 部分，在现有规范后添加：

   ```markdown
   - Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
   - Before imports or any code, add a comment block to the file that explains its purpose.
   ```

4. 保存文件。

## 提交、推送并合并指令更新

云代理读取 Issue 所指向分支中的指令文件。分配新 Issue 时，Copilot 会从 `main` 创建分支，因此更改必须合并到 `main`。

1. 暂存并提交：

   ```bash
   git add .github/copilot-instructions.md
   git commit -m "Add doc comment and file-header standards to copilot instructions"
   ```

2. 推送分支：

   ```bash
   git push -u origin custom-instructions-cloud
   ```

3. 在 github.com 创建从 `custom-instructions-cloud` 到 `main` 的拉取请求并合并。

## 总结与下一步

你已经了解 Copilot 如何通过指令文件获取项目上下文，并向 `.github/copilot-instructions.md` 添加了新的存储库级标准。接下来将 [把第一个 Issue 分配给 Copilot 云代理][next-lesson]。

## 资源

- [GitHub Copilot 自定义指令文件][instruction-files]
- [创建自定义指令的最佳实践][instructions-best-practices]
- [编写更佳 Copilot 自定义指令的 5 个技巧][copilot-instructions-five-tips]
- [Awesome Copilot 指令文件与资源集][awesome-copilot]

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-cloud-agent/
[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses
[instructions-best-practices]: https://docs.github.com/enterprise-cloud@latest/copilot/using-github-copilot/coding-agent/best-practices-for-using-copilot-to-work-on-tasks#adding-custom-instructions-to-your-repository
[copilot-instructions-five-tips]: https://github.blog/ai-and-ml/github-copilot/5-tips-for-writing-better-custom-instructions-for-copilot/
[awesome-copilot]: https://github.com/github/awesome-copilot
