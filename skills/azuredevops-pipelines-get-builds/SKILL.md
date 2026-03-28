---
name: azuredevops-pipelines-get-builds
description: Use when listing Azure DevOps builds with filters for definitions, branches, status, result, and date ranges.
---

# Skill: azuredevops_pipelines_get_builds

## O que faz
- Lista builds de um projeto com filtros avancados.
- Permite filtrar por definicao, branch, status, resultado, autor e periodo.

## Quando usar
- Para consultar historico de execucoes.
- Para localizar builds falhos ou recentes de uma branch.

## Parametros obrigatorios
- `project`.

## Parametros opcionais
- `definitions`, `queues`, `buildNumber`, `minTime`, `maxTime`, `requestedFor`, `reasonFilter`, `statusFilter`, `resultFilter`, `tagFilters`, `properties`, `top`, `continuationToken`, `maxBuildsPerDefinition`, `deletedFilter`, `queryOrder`, `branchName`, `buildIds`, `repositoryId`, `repositoryType`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "definitions": [42],
  "statusFilter": 2,
  "top": 20
}
```

## Retorno do comando
- Retorna lista de builds com IDs, status, resultado, branch e tempos.

## Armadilhas comuns
- Misturar filtros demais e obter lista vazia sem diagnostico.
- Nao usar `continuationToken` em projetos com alto volume.
