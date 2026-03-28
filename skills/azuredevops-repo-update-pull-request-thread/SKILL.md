---
name: azuredevops-repo-update-pull-request-thread
description: Use when updating the status of an existing thread in an Azure DevOps pull request.
---

# Skill: azuredevops_repo_update_pull_request_thread

## O que faz
- Atualiza status de uma thread de comentario em PR.
- Permite marcar discussao como resolvida ou reabrir.

## Quando usar
- Ao concluir ajustes e fechar thread.
- Ao reabrir discussao apos regressao ou duvida.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `pullRequestId`: ID do PR.
- `threadId`: ID da thread.

## Parametros opcionais
- `project`, `status`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "pullRequestId": 128,
  "threadId": 55,
  "status": "Fixed"
}
```

## Retorno do comando
- Retorna thread atualizada com novo status.

## Armadilhas comuns
- Fechar thread sem evidenciar commit/correcao.
- Usar status inadequado para o contexto da discussao.
