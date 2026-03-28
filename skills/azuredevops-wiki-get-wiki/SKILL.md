---
name: azuredevops-wiki-get-wiki
description: Use when retrieving metadata of a specific Azure DevOps wiki by identifier before page operations.
---

# Skill: azuredevops_wiki_get_wiki

## O que faz
- Busca metadados de uma wiki especifica por `wikiIdentifier`.
- Retorna informacoes basicas para validar contexto de operacoes de pagina.

## Quando usar
- Antes de listar paginas ou atualizar conteudo em uma wiki.
- Para confirmar se o identificador da wiki esta correto.

## Parametros obrigatorios
- `wikiIdentifier`: identificador unico da wiki.

## Parametros opcionais
- `project`: nome ou ID do projeto.

## Exemplo minimo (JSON)
```json
{
  "wikiIdentifier": "Platform.wiki",
  "project": "Platform"
}
```

## Retorno do comando
- Retorna metadados da wiki (nome, tipo, projeto, repositorio associado e links).

## Armadilhas comuns
- Confundir nome amigavel da wiki com o identificador real.
- Omitir `project` quando houver ambiguidades entre wikis.
