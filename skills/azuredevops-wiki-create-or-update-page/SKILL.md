---
name: azuredevops-wiki-create-or-update-page
description: Use when creating or updating Azure DevOps wiki pages with markdown content at a specific path.
---

# Skill: azuredevops_wiki_create_or_update_page

## O que faz
- Cria ou atualiza uma pagina de wiki em um caminho definido.
- Publica conteudo em markdown.
- Pode usar `etag` para controle de concorrencia em edicoes.

## Quando usar
- Para documentar mudancas tecnicas em wiki de projeto.
- Para automatizar atualizacoes de paginas recorrentes.

## Parametros obrigatorios
- `wikiIdentifier`: identificador ou nome da wiki.
- `path`: caminho da pagina.
- `content`: conteudo markdown da pagina.

## Parametros opcionais
- `project`, `etag`, `branch`.

## Exemplo minimo (JSON)
```json
{
  "wikiIdentifier": "Platform.wiki",
  "project": "Platform",
  "path": "/Runbooks/Deploy",
  "content": "# Deploy\n\nPassos atualizados...",
  "branch": "wikiMaster"
}
```

## Retorno do comando
- Retorna metadados da pagina criada/atualizada, incluindo versao e URL.

## Armadilhas comuns
- Sobrescrever conteudo sem validar versao/`etag` em cenarios concorrentes.
- Escrever em `path` incorreto e fragmentar documentacao da wiki.
