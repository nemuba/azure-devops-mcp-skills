---
name: azuredevops-repo-list-pull-request-thread-comments
description: Use when reading comments from a specific thread in an Azure DevOps pull request.
---

# Skill: azuredevops_repo_list_pull_request_thread_comments

## O que faz
- Lista comentarios de uma thread especifica em um PR.
- Suporta paginacao e retorno completo opcional.

## Quando usar
- Para auditar historico de comentarios de uma thread.
- Antes de responder ou fechar discussao.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `pullRequestId`: ID do PR.
- `threadId`: ID da thread.

## Parametros opcionais
- `project`, `top`, `skip`, `fullResponse`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "pullRequestId": 128,
  "threadId": 55,
  "top": 50
}
```

## Retorno do comando
- Retorna comentarios da thread com autor, conteudo e timestamp.

## Armadilhas comuns
- Usar `threadId` de outro PR.
- Assumir ordem cronologica sem validar timestamps.
