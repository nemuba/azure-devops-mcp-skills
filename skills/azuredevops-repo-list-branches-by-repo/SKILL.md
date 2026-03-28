---
name: azuredevops-repo-list-branches-by-repo
description: Use when listing branches in an Azure DevOps repository and filtering branch names.
---

# Skill: azuredevops_repo_list_branches_by_repo

## O que faz
- Lista branches de um repositorio.
- Permite filtrar por trecho no nome da branch.

## Quando usar
- Para validar se uma branch existe antes de criar PR.
- Para descobrir convencoes de nomes no repositorio.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.

## Parametros opcionais
- `top`, `filterContains`, `project`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "filterContains": "feature/",
  "top": 100
}
```

## Retorno do comando
- Retorna lista de refs/branches do repositorio.

## Armadilhas comuns
- Esquecer `project` ao usar nome de repositorio.
- Interpretar branch local como branch remota no Azure DevOps.
