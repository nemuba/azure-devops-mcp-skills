---
name: azuredevops-wit-get-work-items-for-iteration
description: Use when listing Azure DevOps work items scoped to a specific iteration for project or team planning.
---

# Skill: azuredevops_wit_get_work_items_for_iteration

## O que faz
- Retorna work items de uma iteracao especifica.
- Pode ser filtrado por time (ou usar time padrao).

## Quando usar
- Para montar visao de sprint atual.
- Para validar escopo de itens por iteracao.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `iterationId`: ID da iteracao.

## Parametros opcionais
- `team`: nome ou ID do time.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "team": "Platform Team",
  "iterationId": "4f9f3f6d-12ab-4b44-8d8c-85ef0c0a2f41"
}
```

## Retorno do comando
- Retorna lista de work items associados a iteracao.

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
- `workItems`: lista de referencias de work item.
- `workItems[].id`: ID do work item.
- `workItems[].url`: endpoint REST do item.

## Armadilhas comuns
- Usar `iterationId` errado e interpretar lista vazia como falha da API.
- Esperar detalhes completos sem consultar `get_work_item` depois.
