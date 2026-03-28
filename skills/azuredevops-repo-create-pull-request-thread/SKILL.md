---
name: azuredevops-repo-create-pull-request-thread
description: Use when creating a new comment thread on an Azure DevOps pull request, optionally anchored to a file and line range.
---

# Skill: azuredevops_repo_create_pull_request_thread

## O que faz
- Cria nova thread de comentario em PR.
- Pode ancorar comentario em arquivo e posicao de linha.

## Quando usar
- Para abrir novo ponto de revisao em PR.
- Para registrar problema localizado em trecho de diff.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `pullRequestId`: ID do PR.
- `content`: conteudo do comentario.

## Parametros opcionais
- `project`, `filePath`, `status`.
- `rightFileStartLine`, `rightFileStartOffset`, `rightFileEndLine`, `rightFileEndOffset`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "pullRequestId": 128,
  "content": "Validar tratamento de erro neste bloco.",
  "filePath": "/src/auth/token.ts",
  "rightFileStartLine": 42,
  "rightFileStartOffset": 1,
  "rightFileEndLine": 42,
  "rightFileEndOffset": 30
}
```

## Retorno do comando
- Retorna a thread criada com ID, status e comentarios.

## Armadilhas comuns
- Informar offsets sem linha correspondente.
- Comentar arquivo/linha fora da iteracao atual.
