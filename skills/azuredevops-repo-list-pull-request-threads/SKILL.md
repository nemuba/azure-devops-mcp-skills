---
name: azuredevops-repo-list-pull-request-threads
description: Use when retrieving comment threads of an Azure DevOps pull request, including status and author-based filtering.
---

# Skill: azuredevops_repo_list_pull_request_threads

## O que faz
- Lista threads de comentarios de um PR.
- Permite filtrar por status, autor e iteracao.

## Quando usar
- Para revisar discussoes abertas em um PR.
- Para monitorar threads pendentes por autor/status.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `pullRequestId`: ID do PR.

## Parametros opcionais
- `project`, `iteration`, `baseIteration`, `top`, `skip`, `fullResponse`.
- `status`, `authorEmail`, `authorDisplayName`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "pullRequestId": 128,
  "status": "Active",
  "top": 100
}
```

## Retorno do comando
- Retorna threads com comentarios, status e contexto de arquivo quando aplicavel.

## Armadilhas comuns
- Ler apenas status do PR e ignorar threads ainda ativas.
- Filtrar por iteracao errada e perder comentarios recentes.
