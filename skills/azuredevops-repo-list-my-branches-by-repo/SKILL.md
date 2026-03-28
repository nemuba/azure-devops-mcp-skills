---
name: azuredevops-repo-list-my-branches-by-repo
description: Use when listing branches in an Azure DevOps repository that are owned or relevant to the current authenticated user.
---

# Skill: azuredevops_repo_list_my_branches_by_repo

## O que faz
- Lista branches do usuario autenticado em um repositorio.
- Pode filtrar por trecho no nome da branch.

## Quando usar
- Para localizar rapidamente branches pessoais de trabalho.
- Para limpeza ou acompanhamento de branches antigas.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.

## Parametros opcionais
- `top`, `filterContains`, `project`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "top": 50
}
```

## Retorno do comando
- Retorna lista de branches associadas ao usuario atual.

## Armadilhas comuns
- Esperar ver todas as branches do repositorio (comando e orientado ao usuario).
- Ignorar filtros e receber lista extensa.
