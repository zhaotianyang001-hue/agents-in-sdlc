---
title: "演習 2 - GitHub Copilot cloud agent"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[GitHub Copilot cloud agent][cloud-agent] はバックグラウンドでタスクを実行し、完了時にレビュー可能なドラフトプルリクエストを作成します。タスクの目的と範囲を明確にすると、エージェントはより正確に作業できます。

## Issue を割り当てる

1. リポジトリの **Issues** タブを開きます。
2. **New issue** を選択します。
3. タイトルに `Code lacks documentation` を設定し、TSDoc コメントを追加する要件を説明します。
4. Issue の右側で **Assign to Copilot** を選択します。
5. Copilot がプルリクエストを作成するまで待ちます。

![Copilot への Issue の割り当て](../../../_images/ex4-assign-copilot-details.png)

> [!NOTE]
> エージェントのセッションを確認しながら、プロジェクトを探索し、計画し、コードを生成する様子を観察できます。

## 次の作業

別の Issue を作成し、ゲーム詳細ページに関連ゲームを表示する機能を追加します。

```markdown
We want to help people discover more games by showing related games on each game's details page.
- Add a data-access helper in `src/lib/` that returns other games in the same category as a given game, excluding that game
- Show a "Related games" section on the game details page
- Handle the case where a game has no related games
- Create unit tests for the helper
- Ensure all tests pass before creating the PR
```

次は[カスタムエージェント][next-lesson]の使い方を確認します。

[cloud-agent]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[next-lesson]: ../3-custom-agents/
