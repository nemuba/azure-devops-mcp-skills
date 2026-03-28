---
name: azuredevops-wit-get-query-results-by-id
description: Use when executing a saved Azure DevOps query by ID and retrieving either full payload or only work item IDs.
---

# Skill: azuredevops_wit_get_query_results_by_id

## O que faz
- Executa query salva por ID e retorna resultados.
- Permite retorno completo (`full`) ou apenas IDs (`ids`).

## Quando usar
- Para alimentar fluxos de processamento de work items por query.
- Quando precisa reduzir payload usando resposta so com IDs.

## Parametros obrigatorios
- `id`: ID da query.

## Parametros opcionais
- `project`: nome ou ID do projeto.
- `team`: nome ou ID do time.
- `timePrecision`: inclui precisao de tempo.
- `top`: limite de resultados.
- `responseType`: `full` ou `ids`.

## Exemplo minimo (JSON)
```json
{
  "id": "4a8bc9f0-1234-4f4a-9aa1-0ea0652f13a1",
  "project": "Platform",
  "top": 50,
  "responseType": "ids"
}
```

## Retorno do comando
- Retorna resultados da query no formato escolhido.

Exemplo de retorno (`ids`):
```json
{
  "count": 2,
  "workItemIds": [1201, 1202]
}
```

## Descricao dos campos retornados
- `count`: quantidade de itens encontrados.
- `workItemIds`: lista de IDs (quando `responseType` = `ids`).
- `workItems`: lista completa de referencias/itens (quando `responseType` = `full`).

## Armadilhas comuns
- Pedir `full` para conjuntos muito grandes e gerar payload excessivo.
- Esquecer `top` e supor que o resultado e completo em queries amplas.
