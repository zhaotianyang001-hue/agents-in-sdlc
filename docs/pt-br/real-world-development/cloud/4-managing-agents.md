---
title: "Exercício 4 - Monitoramento e gerenciamento de agentes"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O cloud agent pode funcionar de maneira assíncrona e autônoma, mas ainda é importante monitorar suas tarefas. Na [página de agentes][agents-page] do GitHub você pode ver as tarefas abertas, revisar as operações realizadas e redirecionar uma sessão em andamento.

Neste exercício, você vai:

- explorar a página de agentes para monitorar tarefas do cloud agent;
- direcionar uma sessão ativa para solicitar funcionalidades adicionais.

## Revisar tarefas do cloud agent

1. Acesse a [página de agentes do Copilot](https://github.com/copilot/agents).
2. Observe as tarefas principais e a lista lateral.
3. Selecione uma tarefa em execução e revise as etapas realizadas pelo Copilot.
4. Use o painel de pull request à direita para revisar os arquivos alterados.

## Direcionar o cloud agent

Enquanto o agente estiver implementando o modo de alto contraste, solicite também um modo claro:

```plaintext
While we are working on a high contrast mode, let's also add a light mode. There should be a switch for this mode as well where users can select their desired display mode.
```

No diálogo **Steer active session while Copilot is working**, envie o prompt e acompanhe a resposta do Copilot.

## Resumo e próximos passos

Você explorou a central de controle dos agentes e direcionou uma sessão em andamento. Continue para [iterar sobre o trabalho do Copilot][next-lesson].

[previous-lesson]: ../3-custom-agents/
[next-lesson]: ../5-iterating/
[agents-page]: https://github.blog/changelog/2025-07-03-agents-page-for-copilot-coding-agent-in-public-preview
