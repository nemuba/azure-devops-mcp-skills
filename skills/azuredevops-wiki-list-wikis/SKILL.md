---
name: azuredevops-wiki-list-wikis
description: Use when listing Azure DevOps wikis in an organization or project and validating available wiki identifiers.
---

# Skill: azuredevops_wiki_list_wikis

## O que faz
- Lista wikis disponiveis na organizacao ou em um projeto especifico.
- Ajuda a identificar `wikiIdentifier` correto para chamadas seguintes.

## Quando usar
- No inicio de um fluxo de leitura/escrita em wiki.
- Para mapear quais wikis existem no escopo do projeto.

## Parametros obrigatorios
- Nenhum.

## Parametros opcionais
- `project`: nome ou ID do projeto para filtrar a listagem.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform"
}
```

## Retorno do comando
- Retorna lista de wikis com metadados principais e links.

## Armadilhas comuns
- Assumir que existe apenas uma wiki por projeto.
- Usar wiki errada ao nao validar o identificador retornado.
