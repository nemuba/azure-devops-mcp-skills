---
name: azuredevops-pipelines-get-build-changes
description: Use when listing source changes associated with an Azure DevOps build for traceability and release notes.
---

# Skill: azuredevops_pipelines_get_build_changes

## O que faz
- Lista alteracoes de codigo associadas a um build.
- Pode incluir detalhes de source change e paginacao.

## Quando usar
- Para rastrear quais commits entraram em uma execucao.
- Para montar notas de release por build.

## Parametros obrigatorios
- `project`, `buildId`.

## Parametros opcionais
- `continuationToken`, `top`, `includeSourceChange`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "buildId": 1001,
  "top": 100,
  "includeSourceChange": true
}
```

## Retorno do comando
- Retorna lista de changesets/commits ligados ao build.

## Armadilhas comuns
- Assumir que a lista sempre cabe em uma pagina.
- Nao habilitar `includeSourceChange` quando precisar de contexto adicional.
