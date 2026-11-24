---
title: "第 4 课：自定义指令"
authors:
  - geektrainer
lastUpdated: 2026-09-18
---

指令文件可让 Copilot 持续遵循项目规则。存储库级 `.github/copilot-instructions.md` 对所有请求提供项目上下文，按路径限定的 `*.instructions.md` 文件则提供特定语言、文件类型或任务的规则。

1. 打开 `.github/copilot-instructions.md`，审阅项目结构、编码规范和脚本。
2. 打开 `.github/instructions` 中与任务相关的文件。
3. 根据项目标准添加或更新指令。
4. 提交指令并验证 Copilot 后续生成的代码是否遵循这些规则。

> [!TIP]
> 指令应简洁、可执行并提供正反示例。

[previous-lesson]: ../3-agent-modes/
[next-lesson]: ../5-agent-skills/
