---
name: azuredevops-repo-get-pull-request-by-id
description: Use when retrieving a single Azure DevOps pull request by ID, optionally including labels or linked work items.
---

# Skill: azuredevops_repo_get_pull_request_by_id

## O que faz
- Retorna detalhes de um PR por ID.
- Pode incluir referencias de work items e labels.

## Quando usar
- Para obter estado detalhado de um PR especifico.
- Para automacoes de auditoria e acompanhamento.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `pullRequestId`: ID do PR.

## Parametros opcionais
- `project`, `includeWorkItemRefs`, `includeLabels`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "pullRequestId": 128,
  "includeWorkItemRefs": true,
  "includeLabels": true
}
```

## Retorno do comando
- Retorna metadados completos do PR, status, branches e referencias opcionais.

## Armadilhas comuns
- Consultar PR em repositorio/projeto errado.
- Esquecer `includeWorkItemRefs` quando depende de rastreabilidade.
