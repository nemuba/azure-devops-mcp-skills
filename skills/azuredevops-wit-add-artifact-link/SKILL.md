---
name: azuredevops-wit-add-artifact-link
description: Use when linking Azure DevOps work items to artifacts such as branches, commits, pull requests, builds, or explicit VSTFS URIs.
---

# Skill: azuredevops_wit_add_artifact_link

## O que faz
- Adiciona link de artefato a um work item.
- Suporta branch, commit, pull request, build e URI VSTFS completa.

## Quando usar
- Para rastreabilidade entre item e artefatos de desenvolvimento.
- Para associar PR/build ao item durante fluxo de entrega.

## Parametros obrigatorios
- `workItemId`: ID do work item.
- `project`: nome ou ID do projeto.

## Parametros opcionais
- `artifactUri`: URI VSTFS completa do artefato.
- `projectId`, `repositoryId`: identificadores para compor URI Git.
- `branchName`, `commitId`, `pullRequestId`, `buildId`: dados do artefato alvo.
- `linkType`: tipo de link (`Branch`, `Pull Request`, `Fixed in Commit`, etc.).
- `comment`: comentario opcional do link.

## Exemplo minimo (JSON)
```json
{
  "workItemId": 1201,
  "project": "Platform",
  "projectId": "11111111-2222-3333-4444-555555555555",
  "repositoryId": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
  "pullRequestId": 87,
  "linkType": "Pull Request",
  "comment": "PR que implementa a correcao"
}
```

## Retorno do comando
- Retorna confirmacao do link criado e referencia do artefato.

Exemplo de retorno:
```json
{
  "workItemId": 1201,
  "linkType": "Pull Request",
  "artifactUri": "vstfs:///Git/PullRequestId/...",
  "success": true
}
```

## Descricao dos campos retornados
- `workItemId`: ID do item que recebeu o link.
- `linkType`: tipo de link aplicado.
- `artifactUri`: URI final do artefato vinculado.
- `success`: indica sucesso da operacao.

## Armadilhas comuns
- Informar `linkType` que nao combina com os parametros enviados.
- Misturar IDs de projeto/repositorio e vincular artefato errado.
