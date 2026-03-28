---
name: azuredevops-repo-list-repos-by-project
description: Use when listing repositories in an Azure DevOps project and validating repository names before repository-scoped operations.
---

# Skill: azuredevops_repo_list_repos_by_project

## O que faz
- Lista repositorios de um projeto Azure DevOps.
- Permite filtro por trecho do nome e paginacao.

## Quando usar
- No inicio de fluxos que exigem `repositoryId`.
- Para validar nome exato de repositorio.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.

## Parametros opcionais
- `top`, `skip`, `repoNameFilter`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "repoNameFilter": "backend",
  "top": 20
}
```

## Retorno do comando
- Retorna lista de repositorios do projeto com metadados basicos.

## Armadilhas comuns
- Assumir nome sem listar antes em projetos grandes.
- Ignorar paginacao em organizacoes com muitos repositorios.
