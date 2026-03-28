---
name: azuredevops-repo-search-commits
description: Use when searching Azure DevOps commits by branch, author, date range, commit IDs, or message text.
---

# Skill: azuredevops_repo_search_commits

## O que faz
- Busca commits em repositorio com filtros abrangentes.
- Suporta filtros por texto, autor, committer, periodo e IDs.

## Quando usar
- Para investigar historico de alteracoes e autoria.
- Para localizar commits por descricao/comentario.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `repository`: nome ou ID do repositorio.

## Parametros opcionais
- `fromCommit`, `toCommit`, `version`, `versionType`, `skip`, `top`.
- `includeLinks`, `includeWorkItems`, `searchText`.
- `author`, `authorEmail`, `committer`, `committerEmail`.
- `fromDate`, `toDate`, `commitIds`, `historySimplificationMode`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "repository": "backend-api",
  "version": "main",
  "searchText": "token validation",
  "top": 20
}
```

## Retorno do comando
- Retorna lista de commits com metadados, e opcionalmente links/work items.

## Armadilhas comuns
- Misturar `commitIds` com outros filtros esperando combinacao (IDs prevalecem).
- Buscar em branch errada por `version`/`versionType` incorretos.
