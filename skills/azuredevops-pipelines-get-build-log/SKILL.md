---
name: azuredevops-pipelines-get-build-log
description: Use when retrieving all logs metadata for a specific Azure DevOps build to inspect execution output.
---

# Skill: azuredevops_pipelines_get_build_log

## O que faz
- Recupera logs de um build especifico.
- Retorna estrutura de logs disponiveis para aquele build.

## Quando usar
- Para investigar erros de execucao em CI.
- Antes de buscar uma secao especifica por `logId`.

## Parametros obrigatorios
- `project`, `buildId`.

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "buildId": 1001
}
```

## Retorno do comando
- Retorna logs associados ao build (IDs, tipo, referencias).

## Armadilhas comuns
- Esperar recorte de linhas neste endpoint (use o `get-build-log-by-id`).
- Consultar `buildId` de outro projeto por engano.
