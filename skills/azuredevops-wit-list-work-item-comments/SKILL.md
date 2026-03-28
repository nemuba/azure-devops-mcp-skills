---
name: azuredevops-wit-list-work-item-comments
description: Use when reading comments for an Azure DevOps work item, with optional pagination limits.
---

# Skill: azuredevops_wit_list_work_item_comments

## O que faz
- Lista comentarios de um work item.
- Permite limitar a quantidade retornada.

## Quando usar
- Para revisar historico de discussao de um item.
- Antes de adicionar novo comentario e evitar duplicidade.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `workItemId`: ID do work item.

## Parametros opcionais
- `top`: limite de comentarios retornados.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "workItemId": 1201,
  "top": 20
}
```

## Retorno do comando
- Retorna comentarios ordenados do work item.

Exemplo de retorno:
```json
{
  "count": 1,
  "comments": [
    {
      "id": 45,
      "text": "Aguardando validacao do QA",
      "createdBy": "Ana Silva",
      "createdDate": "2026-03-26T12:10:00Z"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de comentarios retornados.
- `comments`: lista de comentarios.
- `comments[].id`: ID do comentario.
- `comments[].text`: conteudo do comentario.
- `comments[].createdBy`: autor do comentario.
- `comments[].createdDate`: data/hora de criacao.

## Armadilhas comuns
- Ler apenas os primeiros comentarios sem ajustar `top`.
- Assumir que `text` vem em markdown quando foi salvo como HTML.
