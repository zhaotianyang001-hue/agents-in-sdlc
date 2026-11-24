---
slug: ja-jp/real-world-development/cloud
title: "GitHub Copilot cloud agent"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

**[GitHub Copilot cloud agent](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)** を使うと、GitHub 上の作業を非同期エージェントに任せ、リポジトリの調査、変更、プルリクエスト作成をバックグラウンドで進められます。

この演習では、クラウドエージェントが従うカスタム指示を追加し、GitHub Issue を割り当てます。エージェントダッシュボードでセッションを監視し、カスタムエージェントでアプローチを調整しながら、作成されたプルリクエストをレビューして反復します。

## 演習

| 演習 | トピック | 説明 |
|----------|-------|-------------|
| [0. 前提条件][ex0] | セットアップ | リポジトリと codespace を作成 |
| [1. カスタム指示][ex1] | コンテキスト | クラウドエージェント向けの指示を追加 |
| [2. Cloud Agent][ex2] | 非同期エージェント | Issue を Copilot に割り当て |
| [3. カスタムエージェント][ex3] | 専門エージェント | カスタムエージェントを確認して使用 |
| [4. エージェントの管理][ex4] | 監視 | セッションを監視して方向付け |
| [5. 反復][ex5] | レビュー | Copilot の結果をレビューして改善 |

## 前提条件

- [ ] 有効な **Copilot Student、Pro、Pro+、Business、Enterprise** プランがある GitHub アカウント
- [ ] アカウントまたは組織で Copilot cloud agent が有効になっていること

> [!NOTE]
> Cloud agent は **Copilot Free** を除く各プランで利用できます。Copilot Business または Enterprise の場合は、管理者が組織で有効化する必要があります。

## はじめる

**[演習 0: 前提条件から始める →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
