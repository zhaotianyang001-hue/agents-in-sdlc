---
title: "Exercício 2 - GitHub Copilot cloud agent"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Lição anterior: Instruções personalizadas][previous-lesson] |
|:--|

O GitHub Copilot cloud agent pode atualizar código e adicionar funcionalidades de maneira autônoma. Depois que conclui o trabalho, ele cria uma pull request em rascunho para que uma pessoa desenvolvedora revise.

Neste exercício, você explorará:

- como personalizar o ambiente usado para gerar código;
- como garantir que as operações sejam realizadas com segurança;
- a importância de definir issues com escopo claro;
- como atribuir issues ao Copilot.

## Cenário

A Tailspin Toys quer reduzir sua dívida técnica. Primeiro, deseja adicionar comentários TSDoc a todas as funções exportadas. A equipe de design também quer mostrar jogos relacionados na página de detalhes de um jogo para facilitar a descoberta.

## Introduzir o GitHub Copilot cloud agent

O [GitHub Copilot cloud agent][copilot-agents] executa tarefas em segundo plano, da mesma forma que uma pessoa desenvolvedora. Ao [atribuir uma issue do GitHub ao Copilot][assign-issue], o agente cria uma pull request em rascunho, prepara o ambiente e começa a trabalhar.

> [!NOTE]
> Não existe um atalho para obter bons resultados: defina tarefas bem delimitadas e revise o trabalho produzido.

## Personalizar o ambiente

O cloud agent usa o GitHub Actions. O arquivo `.github/workflows/copilot-setup-steps.yml` pode preparar ferramentas e dependências antes de o agente começar.

## Adicionar documentação

1. No GitHub, abra o repositório.
2. Selecione **Issues** e depois **New issue**.
3. Selecione **Blank issue**.
4. Defina o título como `Code lacks documentation`.
5. Defina a descrição:

   ```plaintext
   Our organization requires TSDoc doc comments for functions and methods where helpful. Recent updates did not follow this standard. Update the existing code so it includes doc comments that clarify behavior.
   ```

6. Crie a issue e atribua-a ao Copilot.
7. Acompanhe a pull request gerada e revise as alterações.

## Adicionar uma seção de jogos relacionados

Crie uma segunda issue com o título `Show related games on the game details page` e a seguinte descrição:

```markdown
We want to help people discover more games by showing related games on each game details page. The design team wants to explore the UX and perform acceptance testing. Requirements:

- Add a data-access helper in `src/lib/` that returns other games in the same category as a given game, excluding that game.
- Show a "Related games" section on the game details page that uses the helper.
- Handle the case where a game has no related games.
- Create unit tests for the new helper.
- Ensure all tests pass before creating the PR.
```

Atribua essa issue ao Copilot. Depois, revise a pull request concluída.

## Resumo e próximos passos

Você atribuiu tarefas ao Copilot cloud agent e viu o agente preparar o ambiente, planejar e executar o trabalho de forma assíncrona. Agora continue para [Criar agentes personalizados][next-lesson].

[previous-lesson]: ../1-custom-instructions/
[next-lesson]: ../3-custom-agents/
[copilot-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent
[assign-issue]: https://docs.github.com/copilot/how-tos/use-copilot-agents/cloud-agent/start-copilot-sessions
