---
title: "演習 1 - カスタム指示（クラウドエージェント）"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

生成 AI に作業を任せる場合、プロジェクト固有のコンテキストを提供することが重要です。[カスタム指示ファイル][instruction-files]を使うと、Copilot に「何をするか」だけでなく「どのようにするか」を伝えられます。

この演習では、リポジトリ全体のカスタム指示を確認し、TSDoc コメントとファイルヘッダーに関する規約を追加します。

1. `.github/copilot-instructions.md` を開きます。
2. **Code formatting requirements** セクションを確認します。
3. 次の規約を既存の規約の下に追加します。

   ```markdown
   - Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
   - Before imports or any code, add a comment block to the file that explains its purpose.
   ```

4. ファイルを保存し、新しいブランチでコミットして `main` に反映します。

> [!NOTE]
> クラウドエージェントは非同期で Issue を処理するため、この演習では実行結果をすぐに比較できません。次の演習で作成されるプルリクエストをレビューするときに、指示が反映されていることを確認します。

次は、最初の Issue を[クラウドエージェントに割り当てます][next-lesson]。

[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses
[next-lesson]: ../2-cloud-agent/
