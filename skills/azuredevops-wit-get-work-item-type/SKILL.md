---
name: azuredevops-wit-get-work-item-type
description: Use when inspecting Azure DevOps work item type metadata and field rules before creating or updating items.
---

# Skill: azuredevops_wit_get_work_item_type

## O que faz
- Retorna metadados de um tipo de work item (Task, Bug, User Story, etc.).
- Mostra campos, estados e regras suportadas pelo tipo.

## Quando usar
- Antes de criar itens para validar campos obrigatorios.
- Antes de automacoes que atualizam campos sensiveis.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `workItemType`: nome do tipo de work item.

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "workItemType": "Task"
}
```

## Retorno do comando
- Retorna definicao do tipo de work item.

Exemplo de retorno:
```json
{
  "name": "Task",
  "referenceName": "Microsoft.VSTS.WorkItemTypes.Task",
  "states": [
    { "name": "New" },
    { "name": "Active" },
    { "name": "Closed" }
  ],
  "fields": [
    { "referenceName": "System.Title", "required": true }
  ]
}
```

## Descricao dos campos retornados
- `name`: nome amigavel do tipo.
- `referenceName`: nome tecnico do tipo.
- `states`: estados permitidos para o tipo.
- `states[].name`: nome do estado.
- `fields`: definicoes de campos do tipo.
- `fields[].referenceName`: nome tecnico do campo.
- `fields[].required`: indica obrigatoriedade.

## Armadilhas comuns
- Criar item sem verificar campos obrigatorios do tipo.
- Assumir fluxo de estados igual entre tipos diferentes.
