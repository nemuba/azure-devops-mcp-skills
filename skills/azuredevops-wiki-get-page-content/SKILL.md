---
name: azuredevops-wiki-get-page-content
description: Use when retrieving Azure DevOps wiki page content by URL or by wiki identifier/project/path parameters.
---

# Skill: azuredevops_wiki_get_page_content

## O que faz
- Retorna o conteudo de uma pagina de wiki.
- Aceita duas formas: URL completa da pagina ou conjunto (`wikiIdentifier`, `project`, `path`).

## Quando usar
- Para ler documentacao existente antes de editar.
- Para extrair markdown de uma pagina especifica.

## Parametros obrigatorios
- Informe **ou** `url` **ou** (`wikiIdentifier` + `project`).

## Parametros opcionais
- `path` (quando nao usar `url`).

## Exemplo minimo (JSON)
```json
{
  "wikiIdentifier": "Platform.wiki",
  "project": "Platform",
  "path": "/Architecture/API-Gateway"
}
```

## Retorno do comando
- Retorna conteudo da pagina (normalmente markdown) e metadados relacionados.

## Armadilhas comuns
- Passar `url` e parametros de wiki/path esperando combinacao (a URL prevalece).
- Usar path incorreto e interpretar resposta vazia como pagina inexistente.
