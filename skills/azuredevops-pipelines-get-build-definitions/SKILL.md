---
name: azuredevops-pipelines-get-build-definitions
description: Use when listing Azure DevOps build definitions and filtering pipelines by repository, name, path, or metadata.
---

# Skill: azuredevops_pipelines_get_build_definitions

## O que faz
- Lista definicoes de build de um projeto.
- Permite filtrar por repositorio, nome, caminho e outros metadados.

## Quando usar
- Para descobrir pipelines/classicas de build existentes.
- Antes de consultar builds por definicao.

## Parametros obrigatorios
- `project`: ID ou nome do projeto.

## Parametros opcionais
- `repositoryId`, `repositoryType`, `name`, `path`, `queryOrder`, `top`, `continuationToken`, `minMetricsTime`, `definitionIds`, `builtAfter`, `notBuiltAfter`, `includeAllProperties`, `includeLatestBuilds`, `taskIdFilter`, `processType`, `yamlFilename`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "top": 20,
  "includeLatestBuilds": true
}
```

## Retorno do comando
- Retorna lista de definicoes de build com IDs, nomes, path e metadados.

## Armadilhas comuns
- Confundir `pipelineId` (pipelines YAML) com `definitionId` (build definitions).
- Ignorar paginacao em organizacoes com muitas definicoes.
