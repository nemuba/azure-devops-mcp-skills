---
name: azuredevops-wit-list-work-item-revisions
description: Use when inspecting historical revisions of an Azure DevOps work item, including field changes and optional pagination.
---

# Skill: azuredevops_wit_list_work_item_revisions

## O que faz
- Lista revisoes historicas de um work item.
- Permite paginar (`top`, `skip`) e controlar expansao de dados.

## Quando usar
- Para auditoria de alteracoes de campos.
- Para descobrir quando e por quem um campo foi mudado.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `workItemId`: ID do work item.

## Parametros opcionais
- `top`: limite de revisoes.
- `skip`: deslocamento para paginacao.
- `expand`: `None`, `Fields`, `Relations`, `Links` ou `All`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "workItemId": 1201,
  "top": 20,
  "expand": "Fields"
}
```

## Retorno do comando
- Retorna lista de revisoes em ordem historica.

Exemplo de retorno:
```json
{
  "count": 2,
  "value": [
    {
      "id": 1201,
      "rev": 8,
      "fields": {
        "System.State": "Active"
      },
      "revisedDate": "2026-03-26T10:00:00Z"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de revisoes retornadas.
- `value`: lista de revisoes.
- `value[].id`: ID do work item.
- `value[].rev`: numero da revisao.
- `value[].fields`: snapshot parcial/completo de campos na revisao.
- `value[].revisedDate`: data/hora da revisao.

## Armadilhas comuns
- Analisar revisao sem considerar `skip/top` e perder eventos antigos.
- Assumir que todos os campos mudados aparecem sem `expand` adequado.
