---
name: azuredevops-pipelines-list-artifacts
description: Use when listing artifacts produced by an Azure DevOps build before downloading or publishing actions.
---

# Skill: azuredevops_pipelines_list_artifacts

## O que faz
- Lista artefatos de um build especifico.

## Quando usar
- Para identificar `artifactName` disponivel para download.
- Para validar se um build publicou os outputs esperados.

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
- Retorna lista de artefatos com nome, tipo e links de download.

## Armadilhas comuns
- Tentar baixar artefato sem validar nome exato.
- Assumir que todo build gera artefatos.
