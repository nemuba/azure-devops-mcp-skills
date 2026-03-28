---
name: azuredevops-wit-update-work-item-comment
description: Use when editing an existing Azure DevOps work item comment by its comment ID.
---

# Skill: azuredevops_wit_update_work_item_comment

## O que faz
- Atualiza o texto de um comentario existente de work item.
- Permite manter o mesmo comentario com conteudo corrigido.

## Quando usar
- Para corrigir informacao incorreta em comentario anterior.
- Para padronizar formato (markdown/html) em comentarios existentes.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `workItemId`: ID do work item.
- `commentId`: ID do comentario.
- `text`: novo texto.

## Parametros opcionais
- `format`: `markdown` ou `html`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "workItemId": 1201,
  "commentId": 46,
  "text": "Validacao concluida com sucesso. Segue para deploy.",
  "format": "markdown"
}
```

## Retorno do comando
- Retorna o comentario atualizado.

Exemplo de retorno:
```json
{
  "id": 46,
  "text": "Validacao concluida com sucesso. Segue para deploy.",
  "format": "markdown",
  "modifiedBy": "Ana Silva",
  "modifiedDate": "2026-03-26T13:10:00Z"
}
```

## Descricao dos campos retornados
- `id`: ID do comentario atualizado.
- `text`: texto final persistido.
- `format`: formato armazenado.
- `modifiedBy`: usuario que editou.
- `modifiedDate`: data/hora da ultima edicao.

## Armadilhas comuns
- Tentar atualizar comentario inexistente (`commentId` invalido).
- Editar comentario errado por nao validar historico antes.
