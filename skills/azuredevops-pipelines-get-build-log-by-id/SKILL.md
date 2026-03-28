---
name: azuredevops-pipelines-get-build-log-by-id
description: Use when fetching a specific Azure DevOps build log by log ID, optionally slicing lines by range.
---

# Skill: azuredevops_pipelines_get_build_log_by_id

## O que faz
- Busca um log especifico de build por `logId`.
- Suporta recorte por linhas com `startLine` e `endLine`.

## Quando usar
- Para isolar trecho de erro sem baixar o log inteiro.
- Para automacoes de diagnostico incremental.

## Parametros obrigatorios
- `project`, `buildId`, `logId`.

## Parametros opcionais
- `startLine`, `endLine`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "buildId": 1001,
  "logId": 3,
  "startLine": 0,
  "endLine": 200
}
```

## Retorno do comando
- Retorna conteudo textual do log solicitado (total ou parcial).

## Armadilhas comuns
- Usar `logId` inexistente para o `buildId` selecionado.
- Definir intervalo de linhas invalido.
