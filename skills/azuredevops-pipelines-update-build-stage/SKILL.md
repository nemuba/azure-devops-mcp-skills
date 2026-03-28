---
name: azuredevops-pipelines-update-build-stage
description: Use when updating an Azure DevOps build stage state to run, retry, or cancel during execution control.
---

# Skill: azuredevops_pipelines_update_build_stage

## O que faz
- Atualiza o status de um stage de build (`Run`, `Retry`, `Cancel`).
- Permite forcar retry de jobs no stage.

## Quando usar
- Para retentar stage com falha.
- Para cancelar ou iniciar stage em cenarios controlados.

## Parametros obrigatorios
- `project`, `buildId`, `stageName`, `status`.

## Parametros opcionais
- `forceRetryAllJobs`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "buildId": 1001,
  "stageName": "Build",
  "status": "Retry",
  "forceRetryAllJobs": true
}
```

## Retorno do comando
- Retorna estado atualizado do stage na execucao alvo.

## Armadilhas comuns
- Informar `stageName` com nome diferente do definido na pipeline.
- Usar `Retry` em contexto onde o stage nao permite retentativa.
