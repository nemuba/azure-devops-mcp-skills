---
name: azuredevops-wit-my-work-items
description: Use when retrieving Azure DevOps work items relevant to the authenticated user, such as assigned items or recent activity.
---

# Skill: azuredevops_wit_my_work_items

## O que faz
- Lista work items relevantes ao usuario autenticado.
- Permite alternar entre `assignedtome` e `myactivity`.

## Quando usar
- Para ver rapidamente itens atribuidos ao usuario.
- Para gerar visao pessoal de trabalho pendente.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.

## Parametros opcionais
- `type`: `assignedtome` ou `myactivity`.
- `top`: limite de itens retornados.
- `includeCompleted`: inclui itens concluidos.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "type": "assignedtome",
  "top": 25,
  "includeCompleted": false
}
```

## Retorno do comando
- Retorna lista resumida de work items relacionados ao usuario.

Exemplo de retorno:
```json
{
  "count": 1,
  "value": [
    {
      "id": 1304,
      "title": "Implementar validacao de payload",
      "state": "Active",
      "workItemType": "Task",
      "assignedTo": "Ana Silva"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de itens retornados.
- `value`: lista de work items.
- `value[].id`: ID do work item.
- `value[].title`: titulo do item.
- `value[].state`: estado atual.
- `value[].workItemType`: tipo do work item.
- `value[].assignedTo`: usuario atribuido (quando existir).

## Armadilhas comuns
- Esquecer `includeCompleted` e achar que itens sumiram.
- Confundir `myactivity` com itens necessariamente atribuidos ao usuario.
