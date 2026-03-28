---
name: azuredevops-wit-add-work-item-comment
description: Use when adding a new comment to an Azure DevOps work item in markdown or HTML format.
---

# Skill: azuredevops_wit_add_work_item_comment

## O que faz
- Adiciona comentario a um work item.
- Suporta formato `html` (padrao) ou `markdown`.

## Quando usar
- Para registrar progresso, bloqueios ou decisoes no item.
- Quando precisa notificar participantes via historico do work item.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `workItemId`: ID do work item.
- `comment`: texto do comentario.

## Parametros opcionais
- `format`: `markdown` ou `html`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "workItemId": 1201,
  "comment": "Validacao concluida. Segue para deploy.",
  "format": "markdown"
}
```

## Retorno do comando
- Retorna o comentario criado com metadados.

Exemplo de retorno:
```json
{
  "id": 46,
  "text": "Validacao concluida. Segue para deploy.",
  "format": "markdown",
  "createdBy": "Ana Silva",
  "createdDate": "2026-03-26T13:00:00Z"
}
```

## Descricao dos campos retornados
- `id`: ID do comentario criado.
- `text`: conteudo persistido do comentario.
- `format`: formato armazenado.
- `createdBy`: autor do comentario.
- `createdDate`: data/hora de criacao.

## Armadilhas comuns
- Enviar markdown com `format: html` e perder renderizacao esperada.
- Postar comentario duplicado sem verificar os ultimos comentarios.
