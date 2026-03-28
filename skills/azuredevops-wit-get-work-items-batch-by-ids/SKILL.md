---
name: azuredevops-wit-get-work-items-batch-by-ids
description: Use when fetching multiple Azure DevOps work items by ID in a single request, optionally selecting specific fields.
---

# Skill: azuredevops_wit_get_work_items_batch_by_ids

## O que faz
- Busca varios work items por IDs em lote.
- Opcionalmente limita o retorno a campos especificos.

## Quando usar
- Quando ja possui IDs e precisa reduzir chamadas individuais.
- Para montar relatorios com campos padronizados.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `ids`: lista de IDs de work items.

## Parametros opcionais
- `fields`: lista de campos a retornar.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "ids": [1201, 1202, 1203],
  "fields": [
    "System.Id",
    "System.Title",
    "System.State",
    "System.AssignedTo"
  ]
}
```

## Retorno do comando
- Retorna lista de work items no mesmo payload.

Exemplo de retorno:
```json
{
  "count": 2,
  "value": [
    {
      "id": 1201,
      "fields": {
        "System.Title": "Ajustar endpoint",
        "System.State": "Active"
      },
      "url": "https://dev.azure.com/org/_apis/wit/workItems/1201"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de itens encontrados.
- `value`: lista de work items retornados.
- `value[].id`: ID do work item.
- `value[].fields`: dicionario de campos solicitados/disponiveis.
- `value[].url`: endpoint REST do work item.

## Armadilhas comuns
- Solicitar campos invalidos e interpretar `null` como erro do item.
- Enviar IDs de outro projeto e receber resultado parcial.
