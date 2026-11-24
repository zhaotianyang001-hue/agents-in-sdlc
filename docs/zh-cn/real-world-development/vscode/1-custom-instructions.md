---
title: "练习 1：自定义指令"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

自定义指令可让 GitHub Copilot 遵循存储库的编码规范和项目上下文。

1. 打开 `.github/copilot-instructions.md`，审阅项目结构、编码规范和脚本。
2. 打开 `.github/instructions`，查看 Astro、Drizzle、测试等按文件类型限定的指令。
3. 在 VS Code 中修改一个指令文件或添加适用于项目需求的新指令。
4. 在 Copilot Chat 中提交提示词，确认代理读取并遵循新指令。

> [!TIP]
> 将全局规则放在 `.github/copilot-instructions.md`，将文件类型或任务规则放在带 `applyTo` 的 `*.instructions.md` 文件中。

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-agent-mode/
