---
name: azuredevops-wit-update-work-item
description: Use when updating one Azure DevOps work item fields by ID using JSON patch operations.
---

# Skill: azuredevops_wit_update_work_item

## O que faz
- Atualiza campos de um work item por meio de operacoes de patch.
- Suporta `Add`, `Replace` e `Remove` em caminhos de campos.

## Quando usar
- Para mudar estado, titulo, atribuicao, prioridade e outros campos.
- Para automacoes que atualizam um item especifico.

## Parametros obrigatorios
- `id`: ID do work item.
- `updates`: lista de operacoes com `path` e `value`.

## Parametros opcionais
- `updates[].op`: operacao (`add`, `replace`, `remove`).

## Exemplo minimo (JSON)
```json
{
  "id": 1201,
  "updates": [
    {
      "op": "replace",
      "path": "/fields/System.State",
      "value": "Resolved"
    },
    {
      "op": "replace",
      "path": "/fields/System.AssignedTo",
      "value": "ana@empresa.com"
    }
  ]
}
```

## Retorno do comando
- Retorna o work item atualizado apos aplicacao do patch.

Exemplo de retorno:
```json
{
  "id": 1201,
  "rev": 9,
  "fields": {
    "System.State": "Resolved",
    "System.AssignedTo": "Ana Silva"
  },
  "url": "https://dev.azure.com/org/_apis/wit/workItems/1201"
}
```

## Descricao dos campos retornados
- `id`: ID do item atualizado.
- `rev`: nova revisao apos update.
- `fields`: campos relevantes apos a mudanca.
- `fields.System.State`: estado atual.
- `fields.System.AssignedTo`: usuario atribuido atual.
- `url`: endpoint REST do item.

## Armadilhas comuns
- Usar `path` incorreto (ex.: nome de campo errado ou sem prefixo `/fields/`).
- Enviar `remove` com `value` e receber comportamento inesperado.
- Tentar atualizar campos bloqueados por regras de processo.
