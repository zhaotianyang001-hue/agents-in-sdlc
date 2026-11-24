---
title: "Exercício 5: Iteração sobre o trabalho do GitHub Copilot"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

| [← Lição anterior: Gerenciamento de agentes][previous-lesson] |
|:--|

Neste laboratório, você trabalhou com o GitHub Copilot para melhorar a experiência do usuário e adicionar funcionalidades. Agora revise as alterações e solicite melhorias quando necessário.

## Segurança

Como o cloud agent trabalha de forma assíncrona, o GitHub aplica restrições de segurança:

- o Copilot tem acesso de leitura ao repositório e acesso de escrita somente à branch usada pelo agente;
- o cloud agent é executado dentro do GitHub Actions em um ambiente temporário;
- os workflows exigem aprovação humana antes da execução;
- o acesso a recursos externos é limitado por padrão.

## Revisar a documentação gerada

1. Abra a pull request do Copilot que adicionou documentação.
2. Selecione **Files changed** e revise os comentários TSDoc e os cabeçalhos de arquivo.
3. Na guia **Conversation**, aprove os workflows que estiverem aguardando.
4. Confirme que os checks do projeto passam.

## Solicitar alterações

Você pode mencionar o Copilot em um comentário da pull request ou em um comentário inline. Exemplos de solicitações:

- adicionar cabeçalhos de arquivo aos arquivos de código;
- adicionar comentários TSDoc aos arquivos TypeScript e Astro;
- criar um README que descreva a estrutura da aplicação.

## Revisar os recursos implementados

Revise a seção de jogos relacionados e os recursos de acessibilidade. Confira componentes de interface, armazenamento local, CSS, atributos ARIA e navegação pelo teclado.

## Exercício opcional

- crie um formulário de interesse na página de detalhes do jogo;
- implemente paginação na lista de jogos;
- adicione validação de entrada e tratamento de erros.

## Resumo

Você revisou e iterou sobre o trabalho do cloud agent, aprovou workflows e usou agentes personalizados para implementar recursos de acessibilidade.

## Próximos passos

O [workshop do VS Code](../../vscode/) complementa o que você praticou aqui, assim como o [workshop do CLI](../../cli/).

[previous-lesson]: ../4-managing-agents/
