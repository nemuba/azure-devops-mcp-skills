---
name: azuredevops-pipelines-list-runs
description: Use when listing recent Azure DevOps runs for a pipeline to monitor execution history.
---

# Skill: azuredevops_pipelines_list_runs

## O que faz
- Lista runs de uma pipeline (ate o limite do endpoint).

## Quando usar
- Para monitorar historico recente de execucoes.
- Para descobrir `runId` antes de consultar detalhes.

## Parametros obrigatorios
- `project`, `pipelineId`.

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "pipelineId": 15
}
```

## Retorno do comando
- Retorna lista de runs com IDs, status e metadados principais.

## Armadilhas comuns
- Tratar lista como completa sem considerar limites do endpoint.
- Misturar IDs de pipeline classica com pipeline YAML.
