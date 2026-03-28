---
name: azuredevops-wit-create-work-item
description: Use when creating a new Azure DevOps work item with explicit field values, including rich-text fields.
---

# Skill: azuredevops_wit_create_work_item

## O que faz
- Cria um novo work item em um projeto e tipo especificos.
- Define campos iniciais por nome tecnico (ex.: `System.Title`).

## Quando usar
- Para abrir tarefas, bugs ou historias via automacao.
- Quando precisa garantir consistencia de campos de criacao.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `workItemType`: tipo do item a criar.
- `fields`: lista de campos (`name`, `value`).

## Parametros opcionais
- `fields[].format`: formato (`Html` ou `Markdown`) para campos de texto grande.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "workItemType": "Task",
  "fields": [
    {
      "name": "System.Title",
      "value": "Implementar validacao do endpoint"
    },
    {
      "name": "System.Description",
      "value": "Validar schema de entrada e mensagens de erro.",
      "format": "Markdown"
    }
  ]
}
```

## Retorno do comando
- Retorna o work item criado com ID e revisao inicial.

Exemplo de retorno:
```json
{
  "id": 1401,
  "rev": 1,
  "fields": {
    "System.Title": "Implementar validacao do endpoint",
    "System.State": "New"
  },
  "url": "https://dev.azure.com/org/_apis/wit/workItems/1401"
}
```

## Descricao dos campos retornados
- `id`: ID do item criado.
- `rev`: revisao inicial do item.
- `fields`: campos principais persistidos.
- `fields.System.Title`: titulo salvo.
- `fields.System.State`: estado inicial aplicado.
- `url`: endpoint REST do item criado.

## Armadilhas comuns
- Informar campo invalido para o tipo selecionado.
- Esquecer campo obrigatorio e receber erro de validacao.
