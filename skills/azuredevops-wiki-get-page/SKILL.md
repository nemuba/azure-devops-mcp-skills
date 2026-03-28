---
name: azuredevops-wiki-get-page
description: Use when retrieving Azure DevOps wiki page metadata by path, including optional child page recursion.
---

# Skill: azuredevops_wiki_get_page

## O que faz
- Busca metadados de uma pagina de wiki por `path`.
- Permite expandir subpaginas com niveis de recursao.
- Nao retorna conteudo textual da pagina.

## Quando usar
- Para validar existencia e estrutura de uma pagina.
- Antes de buscar conteudo com o comando especifico de conteudo.

## Parametros obrigatorios
- `wikiIdentifier`: identificador da wiki.
- `project`: nome ou ID do projeto.
- `path`: caminho da pagina (ex.: `/Home`).

## Parametros opcionais
- `recursionLevel`: `None`, `OneLevel`, `OneLevelPlusNestedEmptyFolders` ou `Full`.

## Exemplo minimo (JSON)
```json
{
  "wikiIdentifier": "Platform.wiki",
  "project": "Platform",
  "path": "/Architecture",
  "recursionLevel": "OneLevel"
}
```

## Retorno do comando
- Retorna metadados da pagina e, opcionalmente, de paginas filhas.

## Armadilhas comuns
- Esperar conteudo markdown (este comando retorna metadados).
- Usar `path` com codificacao/escape incorretos.
