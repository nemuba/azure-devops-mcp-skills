---
name: azuredevops-wit-update-work-items-batch
description: Use when applying field updates to multiple Azure DevOps work items in batch.
---

# Skill: azuredevops_wit_update_work_items_batch

## O que faz
- Atualiza varios work items em uma unica chamada.
- Cada operacao inclui ID, caminho de campo e valor.

## Quando usar
- Para alteracoes em massa de estado, atribuicao ou outros campos.
- Quando precisa reduzir chamadas individuais de update.

## Parametros obrigatorios
- `updates`: lista de updates em lote.
- `updates[].id`: ID do work item.
- `updates[].path`: caminho do campo.
- `updates[].value`: novo valor.

## Parametros opcionais
- `updates[].op`: `Add`, `Replace` ou `Remove`.
- `updates[].format`: `Html` ou `Markdown` para campos de texto grande.

## Exemplo minimo (JSON)
```json
{
  "updates": [
    {
      "op": "Replace",
      "id": 1201,
      "path": "/fields/System.State",
      "value": "Resolved"
    },
    {
      "op": "Replace",
      "id": 1202,
      "path": "/fields/System.AssignedTo",
      "value": "ana@empresa.com"
    }
  ]
}
```

## Retorno do comando
- Retorna consolidado de updates aplicados por item.

Exemplo de retorno:
```json
{
  "count": 2,
  "updated": [
    { "id": 1201, "success": true },
    { "id": 1202, "success": true }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de operacoes processadas.
- `updated`: lista de resultados por item.
- `updated[].id`: ID do work item processado.
- `updated[].success`: indica sucesso da operacao no item.
- `updated[].error`: detalhe de erro quando houver falha.

## Armadilhas comuns
- Misturar paths invalidos e obter sucesso parcial no lote.
- Nao validar retorno por item e assumir sucesso total.
