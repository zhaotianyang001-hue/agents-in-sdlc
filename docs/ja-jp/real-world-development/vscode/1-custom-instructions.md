---
title: "演習 1 - カスタム指示"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

プロジェクト固有の規約を Copilot に伝えるには、リポジトリのカスタム指示を使用します。

1. `.github/copilot-instructions.md` を開きます。
2. プロジェクト構造、技術スタック、コーディング規約を確認します。
3. `.github/instructions` フォルダーで、タスクやファイル形式ごとの指示を確認します。
4. `unit-tests.instructions.md` を開き、`applyTo` が対象ファイルをどのように決めるか確認します。

> [!TIP]
> カスタム指示には、プロジェクト全体で共通する要件を記載し、特定のファイル形式やタスクにはパススコープ付きの instruction ファイルを使用します。

次は、[エージェントモードでフィルター機能を実装][next-lesson]します。

[next-lesson]: ../2-agent-mode/
