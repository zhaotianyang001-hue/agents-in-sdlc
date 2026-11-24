---
title: "Exercício 3 - Agentes personalizados"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

## O que são agentes personalizados?

Os [agentes personalizados][custom-agents-concept] no GitHub Copilot permitem criar assistentes especializados para tarefas ou áreas específicas do fluxo de desenvolvimento. Você define cada agente em um arquivo Markdown na pasta `.github/agents` do repositório. O agente pode incluir instruções, práticas recomendadas, padrões de código e conhecimento específico de uma área.

Os agentes personalizados são diferentes das skills: o agente é o trabalhador que coordena o trabalho, enquanto as skills são ferramentas que ele pode usar.

## Cenário

A Tailspin Toys quer tornar sua plataforma acessível a todas as pessoas. A equipe solicitou um modo de alto contraste que possa ser ativado ou desativado e que salve a preferência no navegador.

## Revisar o agente personalizado de acessibilidade

1. Abra o arquivo `.github/agents/accessibility.md`.
2. Examine o frontmatter YAML com os campos `name` e `description`.
3. Revise suas responsabilidades, práticas recomendadas e exemplos de código.

> [!CAUTION]
> Os campos `name` e `description` no frontmatter são obrigatórios para agentes personalizados.

## Criar e atribuir uma issue

1. Acesse o repositório e abra **Issues**.
2. Selecione **New issue** e depois **Blank issue**.
3. Use o título `Add high contrast mode to website`.
4. Use esta descrição:

   ```plaintext
   We need a high contrast mode for the site. There should be a toggle for high contrast that the user can set. It should store the setting in local storage on the browser.
   ```

5. Crie a issue e selecione **Assign to Copilot**.
6. Escolha **Accessibility agent** na lista de agentes personalizados.
7. Selecione **Assign**.

## Resumo e próximos passos

Você criou uma issue para um agente personalizado de acessibilidade. Continue para [monitorar e gerenciar a sessão do agente][next-lesson].

[previous-lesson]: ../2-cloud-agent/
[next-lesson]: ../4-managing-agents/
[custom-agents-concept]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
[custom-agents]: https://docs.github.com/copilot/concepts/agents/cloud-agent/about-custom-agents
