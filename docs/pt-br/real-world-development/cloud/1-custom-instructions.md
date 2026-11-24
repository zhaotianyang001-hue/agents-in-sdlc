---
title: "Exercício 1 - Instruções personalizadas (Cloud agent)"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

[← Lição anterior: Pré-requisitos][previous-lesson] · [Próxima lição: Copilot cloud agent →][next-lesson]

O contexto é essencial ao trabalhar com IA generativa. Quando uma tarefa precisa ser executada de uma forma específica — ou o Copilot precisa conhecer informações do projeto — você deve disponibilizar esse contexto. Os [arquivos de instruções][instruction-files] fornecem essa orientação.

Neste exercício, você vai:

- explorar como contexto específico do projeto, diretrizes de código e padrões de documentação chegam ao Copilot por meio de instruções personalizadas e arquivos de instruções com escopo por caminho;
- adicionar um novo padrão global a `.github/copilot-instructions.md`.

## Arquivos de instruções

### Cenário

A Tailspin Toys segue padrões de desenvolvimento que incluem:

- a camada de dados deve sempre ter testes unitários;
- a interface deve usar tema escuro e aparência moderna;
- a documentação deve ser adicionada ao código por meio de comentários TSDoc;
- cada arquivo deve começar com um bloco de comentários que descreva sua finalidade.

Os arquivos de instruções ajudam o Copilot a executar as tarefas de acordo com essas práticas.

### Instruções personalizadas

O arquivo `.github/copilot-instructions.md` envia informações globais do repositório ao Copilot em todas as solicitações. Os arquivos `.github/instructions/*.instructions.md` podem fornecer orientações específicas para tipos de arquivos ou tarefas.

> [!NOTE]
> No Copilot cloud agent, as instruções do repositório são usadas ao gerar código para issues e pull requests atribuídas ao agente.

## Explorar os arquivos de instruções

1. Abra `.github/copilot-instructions.md`.
2. Localize a seção **Code standards** e examine as convenções de TypeScript e TSDoc.
3. Abra `.github/instructions/unit-tests.instructions.md` e observe o campo `applyTo`, que limita as instruções a arquivos que correspondam ao padrão **/*.test.ts.
4. Abra `.github/instructions/drizzle.instructions.md` e observe como os arquivos de instruções podem ser divididos em conjuntos menores e reutilizáveis.

## Adicionar um novo padrão ao repositório

1. Crie e mude para uma nova branch:

   ```bash
   git checkout -b custom-instructions-cloud
   ```

2. Reabra `.github/copilot-instructions.md`.
3. Na seção **Code formatting requirements**, adicione:

   ```markdown
   - Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
   - Before imports or any code, add a comment block to the file that explains its purpose.
   ```

4. Salve o arquivo.

## Confirmar, enviar e mesclar a atualização

```bash
git add .github/copilot-instructions.md
git commit -m "Add doc comment and file-header standards to copilot instructions"
git push -u origin custom-instructions-cloud
```

Abra uma pull request de `custom-instructions-cloud` para `main` no GitHub e faça o merge. O cloud agent lerá essas instruções ao trabalhar nas próximas issues.

## Resumo e próximos passos

Você explorou como o Copilot recebe contexto por meio dos arquivos de instruções e adicionou um novo padrão global ao repositório. Em seguida, [atribua sua primeira issue ao Copilot cloud agent][next-lesson].

[previous-lesson]: ../0-prerequisites/
[next-lesson]: ../2-cloud-agent/
[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses
