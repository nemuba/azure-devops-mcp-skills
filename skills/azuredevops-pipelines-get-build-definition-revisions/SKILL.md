---
name: azuredevops-pipelines-get-build-definition-revisions
description: Use when retrieving revision history of an Azure DevOps build definition to audit configuration changes.
---

# Skill: azuredevops_pipelines_get_build_definition_revisions

## O que faz
- Lista revisoes de uma definicao de build especifica.
- Mostra historico de mudancas de configuracao.

## Quando usar
- Para auditoria de alteracoes em pipeline classica.
- Para investigar quando uma mudanca de definicao ocorreu.

## Parametros obrigatorios
- `project`, `definitionId`.

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "definitionId": 42
}
```

## Retorno do comando
- Retorna revisoes da definicao com dados de autoria e data.

## Armadilhas comuns
- Usar `pipelineId` em vez de `definitionId`.
- Esperar detalhes de execucao (o foco aqui e historico da definicao).
