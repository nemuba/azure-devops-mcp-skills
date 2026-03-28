---
name: azuredevops-pipelines-get-run
description: Use when retrieving details of a specific run from an Azure DevOps pipeline by pipeline and run IDs.
---

# Skill: azuredevops_pipelines_get_run

## O que faz
- Recupera detalhes de uma execucao especifica (`run`) de uma pipeline.

## Quando usar
- Para inspecionar status e metadados de uma run conhecida.
- Para correlacionar resultado de run com automacoes externas.

## Parametros obrigatorios
- `project`, `pipelineId`, `runId`.

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "pipelineId": 15,
  "runId": 3007
}
```

## Retorno do comando
- Retorna dados completos da run (estado, resultado, tempos, referencia).

## Armadilhas comuns
- Confundir `runId` com `buildId`.
- Consultar run em `pipelineId` errado.
