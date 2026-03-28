---
name: azuredevops-repo-get-repo-by-name-or-id
description: Use when retrieving Azure DevOps repository metadata by project and repository name or repository ID.
---

# Skill: azuredevops_repo_get_repo_by_name_or_id

## O que faz
- Busca detalhes de um repositorio por nome ou ID.
- Resolve metadados essenciais para chamadas posteriores.

## Quando usar
- Para validar identidade de repositorio antes de operacoes de PR/branch.
- Para obter IDs canonicamente em automacoes.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `repositoryNameOrId`: nome ou ID do repositorio.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "repositoryNameOrId": "backend-api"
}
```

## Retorno do comando
- Retorna metadados do repositorio (id, nome, projeto, defaultBranch e links).

## Armadilhas comuns
- Assumir que nomes iguais em projetos diferentes apontam para o mesmo repositorio.
