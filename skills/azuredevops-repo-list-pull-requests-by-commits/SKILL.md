---
name: azuredevops-repo-list-pull-requests-by-commits
description: Use when finding which Azure DevOps pull requests contain specific commits.
---

# Skill: azuredevops_repo_list_pull_requests_by_commits

## O que faz
- Lista PRs relacionados a um ou mais commits.
- Permite rastrear de commit para PR de origem/merge.

## Quando usar
- Para auditoria de rastreabilidade commit -> PR.
- Para descobrir em qual PR um commit foi integrado.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `repository`: nome ou ID do repositorio.
- `commits`: lista de SHAs de commit.

## Parametros opcionais
- `queryType`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "repository": "backend-api",
  "commits": [
    "7f1a2b3c4d5e6f7a8b9c"
  ],
  "queryType": "Commit"
}
```

## Retorno do comando
- Retorna PRs associados aos commits informados.

## Armadilhas comuns
- Usar SHA truncado de forma ambigua.
- Esperar resultado em repositorio diferente do commit.
