---
title: "Lição 12 - Publique o site com o GitHub Pages"
description: "Use o aplicativo GitHub Copilot para configurar um workflow do Pages, revisar sua pull request e verificar o Space Quiz publicado."
authors:
  - jamesmontemagno
lastUpdated: 2026-10-12
---

Dê ao Space Quiz uma presença pública implantando-o com o GitHub Pages. O Copilot pode preparar o workflow e orientar a implantação, mas você continua responsável por revisar as alterações e confirmar que o site está disponível.

Nesta lição, você vai:

- pedir ao Copilot que configure uma implantação do GitHub Pages;
- revisar o workflow e a pull request antes de fazer o merge;
- acompanhar a implantação e verificar o site publicado.

## Cenário

O Space Quiz já está em um repositório do GitHub, mas as pessoas ainda precisam de uma maneira simples de experimentá-lo. Publicar o site de arquivo único com o GitHub Pages o torna disponível por meio de uma URL pública, sem adicionar um servidor ou dependência de runtime.

## Peça ao Copilot que prepare a implantação

> [!WARNING]
> Criar uma pull request pode confirmar e enviar código. Revise suas configurações de aprovação e o repositório de destino antes de enviar este prompt. Quando a opção **Approve all** estiver ativada, não espere uma confirmação separada.

Na sessão do aplicativo Copilot para `space-quiz`, envie este prompt:

```plaintext
Prepare a GitHub Pages deployment for this repository. Create a GitHub Actions workflow that builds the website if needed and deploys it to GitHub Pages after changes reach the default branch. Add a README describing the app and how to run it locally if one does not already exist. Create a pull request with these changes and report its link and any required Pages settings or permissions. Do not merge, enable auto-merge, change Pages settings, or deploy. Stop and wait for my review.
```

## Revise o workflow e a pull request

1. Confirme que o README será adicionado somente se o repositório ainda não tiver um.
2. Revise as alterações da pull request, incluindo as etapas de build e implantação, os gatilhos e as permissões do workflow.
3. Confirme que o workflow faz a implantação a partir da branch padrão, não de uma pull request não mesclada.
4. Solicite as correções necessárias e revise o diff atualizado. Aguarde a aprovação dos checks obrigatórios da pull request antes de autorizar o merge.

## Autorize o merge e a implantação

> [!WARNING]
> O prompt a seguir autoriza o agente a fazer o merge da pull request revisada, alterar as configurações do Pages e publicar o site. Envie-o somente depois de concluir a revisão e confirmar o repositório e a pull request. As configurações de aprovação podem permitir essas ações sem outro aviso de confirmação.

Substitua `<PR_NUMBER>` pelo número da pull request que você revisou e envie este prompt separado:

```plaintext
I have reviewed pull request <PR_NUMBER> in this repository and authorize its merge and deployment. Enable GitHub Pages using GitHub Actions, merge that pull request only after required checks pass, and monitor the deployment until it succeeds. Report the final URL of the live website. If you lack permission to enable Pages or merge, tell me exactly what I need to approve or do; do not report success until the site is live.
```

![Diagrama em três etapas: uma pull request mesclada do space-quiz; uma execução bem-sucedida de Deploy website no GitHub Actions, com as etapas Build website, Upload artifact e Deploy to Pages; e o Space Quiz publicado em yourname.github.io/space-quiz/.](../../../_images/first-steps-app-pages-deploy.svg)

## Verifique a implantação

1. Acompanhe a execução de implantação do GitHub Actions até que ela seja concluída com sucesso.
2. Abra a URL informada e confirme que o Space Quiz seja carregado.

Se o agente não puder habilitar o Pages ou fazer o merge, siga as instruções específicas fornecidas por ele. Não considere a tarefa concluída até que a implantação seja concluída e o site publicado seja carregado.

## Resumo e próximos passos

Agora o seu Space Quiz está disponível como um site publicado, e você verificou a implantação em vez de depender do relatório do agente. Continue para a [Lição 13: Revisão e próximos passos][next-lesson].

[next-lesson]: ../13-review/
