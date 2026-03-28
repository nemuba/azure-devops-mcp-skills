---
name: azuredevops-repo-list-pull-requests-by-repo-or-project
description: Use when listing Azure DevOps pull requests by repository or project with filters for author, reviewer, branch, or status.
---

# Skill: azuredevops_repo_list_pull_requests_by_repo_or_project

## O que faz
- Lista pull requests por repositorio ou por projeto.
- Filtra por autor, reviewer, status, branch origem/destino.

## Quando usar
- Para triagem de PRs ativos e acompanhamento de fila de revisao.
- Para encontrar PRs de uma branch especifica.

## Parametros obrigatorios
- Pelo menos um dos dois: `repositoryId` ou `project`.

## Parametros opcionais
- `top`, `skip`, `created_by_me`, `created_by_user`, `i_am_reviewer`, `user_is_reviewer`.
- `status`, `sourceRefName`, `targetRefName`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "repositoryId": "backend-api",
  "status": "Active",
  "i_am_reviewer": true,
  "top": 50
}
```

## Retorno do comando
- Retorna lista de PRs com estado, autoria, branches e metadados principais.

## Armadilhas comuns
- Informar `repositoryId` como nome sem `project`.
- Confundir filtros `created_by_me` e `i_am_reviewer`.
