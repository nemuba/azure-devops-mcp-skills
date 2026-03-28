---
name: azuredevops-wiki-list-pages
description: Use when listing pages of an Azure DevOps wiki with optional pagination and page view metadata.
---

# Skill: azuredevops_wiki_list_pages

## O que faz
- Lista paginas de uma wiki especifica.
- Suporta paginacao por `continuationToken`.
- Pode incluir metricas de visualizacao por periodo.

## Quando usar
- Para explorar a estrutura de conteudo da wiki.
- Para obter pagina raiz e subpaginas antes de ler conteudo.

## Parametros obrigatorios
- `wikiIdentifier`: identificador da wiki.
- `project`: nome ou ID do projeto.

## Parametros opcionais
- `top`, `continuationToken`, `pageViewsForDays`.

## Exemplo minimo (JSON)
```json
{
  "wikiIdentifier": "Platform.wiki",
  "project": "Platform",
  "top": 20
}
```

## Retorno do comando
- Retorna lista paginada de paginas com caminho, ordem hierarquica e metadados.

## Armadilhas comuns
- Ignorar `continuationToken` e concluir que a wiki tem poucas paginas.
- Confundir path da pagina com titulo exibido.
