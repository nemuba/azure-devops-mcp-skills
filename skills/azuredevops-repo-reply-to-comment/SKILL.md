---
name: azuredevops-repo-reply-to-comment
description: Use when replying to an existing comment thread in an Azure DevOps pull request.
---

# Skill: azuredevops_repo_reply_to_comment

## O que faz
- Adiciona resposta em uma thread existente de comentario de PR.
- Mantem contexto da discussao no mesmo thread.

## Quando usar
- Para responder feedback de review sem abrir nova thread.
- Para registrar esclarecimentos ou status de ajuste.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `pullRequestId`: ID do PR.
- `threadId`: ID da thread.
- `content`: texto da resposta.

## Parametros opcionais
- `project`, `fullResponse`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "pullRequestId": 128,
  "threadId": 55,
  "content": "Ajuste aplicado no ultimo commit."
}
```

## Retorno do comando
- Retorna confirmacao da resposta criada (ou payload completo quando `fullResponse=true`).

## Armadilhas comuns
- Responder no `threadId` errado.
- Publicar resposta sem contexto tecnico suficiente para o reviewer.
