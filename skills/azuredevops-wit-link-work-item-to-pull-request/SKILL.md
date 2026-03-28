---
name: azuredevops-wit-link-work-item-to-pull-request
description: Use when linking an existing Azure DevOps work item to a specific pull request for traceability.
---

# Skill: azuredevops_wit_link_work_item_to_pull_request

## O que faz
- Vincula um work item existente a um pull request especifico.
- Cria relacao de rastreabilidade entre demanda e entrega de codigo.

## Quando usar
- Depois de abrir PR que implementa um work item.
- Para garantir rastreabilidade em relatorios e politicas de merge.

## Parametros obrigatorios
- `projectId`: ID do projeto do work item (GUID).
- `repositoryId`: ID do repositorio do PR.
- `pullRequestId`: ID do PR.
- `workItemId`: ID do work item.

## Parametros opcionais
- `pullRequestProjectId`: ID do projeto do PR quando diferente do projeto do item.

## Exemplo minimo (JSON)
```json
{
  "projectId": "11111111-2222-3333-4444-555555555555",
  "repositoryId": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
  "pullRequestId": 87,
  "workItemId": 1201
}
```

## Retorno do comando
- Retorna confirmacao do vinculo criado entre item e PR.

Exemplo de retorno:
```json
{
  "workItemId": 1201,
  "pullRequestId": 87,
  "repositoryId": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
  "success": true
}
```

## Descricao dos campos retornados
- `workItemId`: ID do work item vinculado.
- `pullRequestId`: ID do PR associado.
- `repositoryId`: repositorio onde o PR existe.
- `success`: resultado da operacao.

## Armadilhas comuns
- Usar nome de projeto/repositorio em vez de GUID quando o comando exige IDs.
- Informar `projectId` errado e falhar vinculacao cross-project.
