---
title: "Exercício 1 - Instruções personalizadas"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O contexto é essencial ao trabalhar com IA generativa. Os [arquivos de instruções][instruction-files] ajudam o Copilot a entender não apenas o que você deseja, mas também como deseja que seja feito.

Neste exercício, você vai:

- explorar instruções personalizadas do repositório e instruções com escopo por caminho;
- adicionar padrões de documentação ao projeto;
- verificar o efeito das instruções no Copilot.

## Cenário

A Tailspin Toys define padrões para testes, interface, documentação e cabeçalhos de arquivos. Você usará os arquivos de instruções para fazer o Copilot seguir essas práticas.

## Explorar os arquivos existentes

1. Abra `.github/copilot-instructions.md`.
2. Revise a seção **Code standards**.
3. Abra `.github/instructions/unit-tests.instructions.md` e observe o campo `applyTo`.
4. Abra `.github/instructions/astro.instructions.md` e `.github/instructions/drizzle.instructions.md`.

## Antes e depois

Antes de alterar as instruções, peça ao Copilot que gere ou revise uma função sem comentários TSDoc. Depois, adicione o padrão abaixo ao arquivo `.github/copilot-instructions.md`:

```markdown
- Every exported function should have a TSDoc comment describing its purpose, parameters, and return value.
- Before imports or any code, add a comment block to the file that explains its purpose.
```

> [!TIP]
> Use instruções globais para padrões do projeto e arquivos `.instructions.md` para regras específicas de linguagens, tipos de arquivo ou tarefas.

[instruction-files]: https://docs.github.com/copilot/customizing-copilot/about-customizing-github-copilot-chat-responses
