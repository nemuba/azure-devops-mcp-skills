---
name: azuredevops-wit-list-backlog-work-items
description: Use when listing work items from a specific team backlog category in Azure DevOps.
---

# Skill: azuredevops_wit_list_backlog_work_items

## O que faz
- Lista work items de um backlog especifico de time.
- Usa `backlogId` retornado por `azuredevops_wit_list_backlogs`.

## Quando usar
- Para obter a fila atual de itens por categoria (Epics, Features, etc.).
- Antes de priorizacao ou analise de backlog.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `team`: nome ou ID do time.
- `backlogId`: ID da categoria de backlog.

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "team": "Platform Team",
  "backlogId": "Microsoft.RequirementCategory"
}
```

## Retorno do comando
- Retorna lista de work items no backlog informado.

Exemplo de retorno:
```json
{
  "count": 2,
  "workItems": [
    { "id": 1201, "url": "https://dev.azure.com/org/_apis/wit/workItems/1201" }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de itens retornados.
- `workItems`: lista de referencias de work items.
- `workItems[].id`: ID do work item.
- `workItems[].url`: endpoint REST do work item.

## Armadilhas comuns
- Usar `backlogId` de outro time/processo.
- Esperar campos completos sem buscar detalhes com `get_work_item`.
