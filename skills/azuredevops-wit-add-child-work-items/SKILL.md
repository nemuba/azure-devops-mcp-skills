---
name: azuredevops-wit-add-child-work-items
description: Use when creating one or more child Azure DevOps work items under an existing parent item.
---

# Skill: azuredevops_wit_add_child_work_items

## O que faz
- Cria um ou varios work items filhos para um item pai.
- Define tipo, titulo, descricao e opcionalmente area/iteracao dos filhos.

## Quando usar
- Para decompor um item maior em tarefas menores.
- Para organizar hierarquia pai-filho no backlog.

## Parametros obrigatorios
- `parentId`: ID do item pai.
- `project`: nome ou ID do projeto.
- `workItemType`: tipo dos filhos (Task, Bug, etc.).
- `items`: lista de filhos com `title` e `description`.

## Parametros opcionais
- `items[].format`: formato da descricao (`Html` ou `Markdown`).
- `items[].areaPath`: area path do filho.
- `items[].iterationPath`: iteration path do filho.

## Exemplo minimo (JSON)
```json
{
  "parentId": 900,
  "project": "Platform",
  "workItemType": "Task",
  "items": [
    {
      "title": "Criar contrato da API",
      "description": "Definir request/response do endpoint.",
      "format": "Markdown",
      "areaPath": "Platform",
      "iterationPath": "Platform\\Sprints\\Sprint 25"
    }
  ]
}
```

## Retorno do comando
- Retorna os work items filhos criados e vinculados ao pai.

Exemplo de retorno:
```json
{
  "count": 1,
  "value": [
    {
      "id": 1308,
      "title": "Criar contrato da API",
      "workItemType": "Task",
      "url": "https://dev.azure.com/org/_apis/wit/workItems/1308"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de filhos criados.
- `value`: lista de filhos criados.
- `value[].id`: ID do work item filho.
- `value[].title`: titulo do filho.
- `value[].workItemType`: tipo do item criado.
- `value[].url`: endpoint REST do item filho.

## Armadilhas comuns
- Usar `workItemType` nao permitido no projeto/processo.
- Informar `iterationPath` inexistente e falhar criacao.
