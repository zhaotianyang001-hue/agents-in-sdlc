---
slug: pt-br/real-world-development/cloud
title: "GitHub Copilot cloud agent"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O [**GitHub Copilot cloud agent**](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent) permite que o GitHub Copilot trabalhe de forma assíncrona na nuvem. Você atribui tarefas no GitHub e o cloud agent a assume em segundo plano — explorando o repositório, fazendo alterações e abrindo uma pull request — enquanto você fica livre para realizar outras tarefas.

Ao longo destes exercícios, você adicionará instruções personalizadas que o cloud agent seguirá, atribuirá uma issue do GitHub e permitirá que ele implemente o trabalho. Você revisará os resultados e usará agentes personalizados para orientar sua abordagem, acompanhará e direcionará sessões no painel de agentes e encerrará revisando as pull requests e iterando sobre os resultados.

## Exercícios

| Exercício | Tema | Descrição |
|----------|-------|-------------|
| [0. Pré-requisitos][ex0] | Configuração | Crie seu repositório e codespace |
| [1. Instruções personalizadas][ex1] | Contexto | Adicione instruções personalizadas que o cloud agent seguirá |
| [2. Cloud Agent][ex2] | Agente assíncrono | Atribua issues ao GitHub Copilot cloud agent |
| [3. Agentes personalizados][ex3] | Agentes especializados | Revise e use agentes personalizados |
| [4. Gerenciando agentes][ex4] | Monitoramento | Monitore e direcione sessões de agentes |
| [5. Iteração][ex5] | Revisão | Revise PRs, itere sobre o trabalho do Copilot e escolha os próximos passos |

## Pré-requisitos

Antes de participar deste workshop, confirme que você tem:

- [ ] Uma conta do GitHub com um plano ativo **Copilot Student, Pro, Pro+, Business ou Enterprise**
- [ ] O cloud agent habilitado para sua conta ou organização

> [!TIP]
> Não tem um plano pago? Estudantes verificados podem usar o GitHub Copilot gratuitamente pelo [GitHub Education][callout-student-plan-education]. O plano **Copilot Student** inclui os recursos de agente, MCP, revisão de código e Copilot CLI usados neste workshop, para que você possa concluir todos os exercícios.

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> O cloud agent está disponível nos planos **Copilot Student, Pro, Pro+, Business e Enterprise** — todos, exceto o Copilot Free. No Copilot Business ou Enterprise, um administrador precisa habilitá-lo para sua organização.

> [!NOTE]
> MCP não é abordado neste workshop. Para explorar servidores MCP com o Copilot, consulte o [workshop do CLI](../cli/) ou o [workshop do VS Code](../vscode/).

## Começar

**[Começar pelo Exercício 0: Pré-requisitos →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
