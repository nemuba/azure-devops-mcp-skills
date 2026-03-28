---
name: azuredevops-repo-get-branch-by-name
description: Use when retrieving details of a specific branch by name in an Azure DevOps repository.
---

# Skill: azuredevops_repo_get_branch_by_name

## O que faz
- Busca detalhes de uma branch especifica em um repositorio.
- Retorna metadados da ref e commit associado.

## Quando usar
- Para validar existencia de branch antes de abrir PR.
- Para consultar branch base em automacoes.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `branchName`: nome da branch.

## Parametros opcionais
- `project`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "branchName": "main"
}
```

## Retorno do comando
- Retorna dados da branch e commit de referencia.

## Armadilhas comuns
- Informar branch com prefixo incorreto ou nome incompleto.
- Omitir `project` quando `repositoryId` e nome.
