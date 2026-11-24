---
title: "Exercício 0: Pré-requisitos"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

Antes de iniciar os exercícios do VS Code, prepare o ambiente. Você criará sua própria cópia do repositório Tailspin Toys, iniciará um [codespace][codespaces] e confirmará que o GitHub Copilot Chat está funcionando no editor.

## Configurar o repositório do laboratório

1. Em uma nova janela do navegador, acesse o [modelo Tailspin Toys][tailspin-template].
2. Selecione **Use this template** e depois **Create a new repository**.

    ![Botão Use this template](../../../_images/ex0-use-template.png)

3. Se estiver participando de um evento conduzido pelo GitHub ou pela Microsoft, siga as instruções dos moderadores. Caso contrário, crie o repositório em uma organização onde tenha acesso ao GitHub Copilot.

    ![Configurações do repositório criado a partir do modelo](../../../_images/ex0-repository-settings.png)

4. Anote o caminho do repositório criado (**organization-or-user-name/repository-name**).

> [!NOTE]
> **Seu backlog está pronto**
>
> Ao criar o repositório a partir do modelo, um backlog de issues do GitHub é criado automaticamente. Você usará essas issues ao longo do workshop.

## Criar um codespace

O [GitHub Codespaces][codespaces] permite escrever, executar e depurar código diretamente no navegador.

1. Acesse o repositório recém-criado.
2. Selecione o botão verde **Code**.
3. Selecione a guia **Codespaces** e o botão **+** para criar um novo codespace.

    ![Criar um novo codespace](../../../_images/ex0-create-codespace.png)

> [!CAUTION]
> Você retornará ao codespace em exercícios futuros. Por enquanto, deixe-o aberto em uma aba do navegador.

## Usar o GitHub Copilot Chat e o modo agent

Para usar o modo agent do GitHub Copilot Chat, você precisa da extensão GitHub Copilot Chat instalada no IDE.

1. Retorne ao codespace.
2. Se o chat não estiver visível à direita, selecione o ícone do **Copilot Chat**.
3. Digite uma mensagem como "Hello world" na janela do Copilot Chat.
4. Se necessário, autentique-se em sua conta do GitHub.

    ![Exemplo de autenticação do Copilot Chat](../../../_images/ex1-copilot-authentication.png)

## Resumo

Você criou uma cópia do repositório e iniciou um codespace para começar a escrever código.

## Próximo passo

Comece a usar o Copilot no [Exercício 1 - Instruções personalizadas][next-lesson].

[codespaces]: https://github.com/features/codespaces
[tailspin-template]: https://github.com/github-samples/tailspin-toys
[template-repository]: https://docs.github.com/repositories/creating-and-managing-repositories/creating-a-template-repository
[next-lesson]: ../1-custom-instructions/
