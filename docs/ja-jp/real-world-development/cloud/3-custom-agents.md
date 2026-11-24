---
title: "演習 3 - カスタムエージェント"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[カスタムエージェント][custom-agents-concept]は、特定のタスクや分野向けに再利用可能な AI アシスタントを定義します。リポジトリの `.github/agents` フォルダーに Markdown ファイルを作成し、名前、説明、専門知識、指示を記述します。

## アクセシビリティエージェントを確認する

1. `.github/agents/accessibility.md` を開きます。
2. `name` と `description` を含む YAML フロントマターを確認します。
3. アクセシブルな Web サイトを作成するための責務、ベストプラクティス、コード例、よくある落とし穴を確認します。

> [!CAUTION]
> カスタムエージェントのフロントマターには `name` と `description` が必要です。

## Issue を作成して割り当てる

1. リポジトリで **New issue** を作成します。
2. タイトルに `Add high contrast mode to website` を設定します。
3. 説明にはハイコントラストモードの切り替えとブラウザーのローカルストレージへの設定保存を記載します。
4. **Assign to Copilot** を選択し、カスタムエージェントの一覧から **Accessibility agent** を選択します。

次は、[エージェントセッションの監視と方向付け][next-lesson]を行います。

[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[next-lesson]: ../4-managing-agents/
