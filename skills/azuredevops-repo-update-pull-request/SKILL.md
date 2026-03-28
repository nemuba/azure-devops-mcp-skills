---
name: azuredevops-repo-update-pull-request
description: Use when updating an existing Azure DevOps pull request, including metadata, status, target branch, labels, or autocomplete settings.
---

# Skill: azuredevops_repo_update_pull_request

## O que faz
- Atualiza campos de um pull request existente.
- Suporta mudanca de titulo, descricao, status, labels e branch alvo.
- Configura autocomplete e estrategia de merge.

## Quando usar
- Para ajustar PR apos feedback de revisao.
- Para ativar autocomplete com regras de conclusao.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `pullRequestId`: ID do PR.

## Parametros opcionais
- `project`, `title`, `description`, `isDraft`, `targetRefName`, `status`.
- `autoComplete`, `mergeStrategy`, `deleteSourceBranch`, `transitionWorkItems`, `bypassReason`, `labels`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "pullRequestId": 128,
  "title": "feat: validacao de token (ajustes)",
  "autoComplete": true,
  "mergeStrategy": "Squash",
  "deleteSourceBranch": true
}
```

## Retorno do comando
- Retorna o PR atualizado com os campos aplicados.

## Armadilhas comuns
- Usar `targetRefName` sem prefixo `refs/heads/`.
- Definir `bypassReason` sem necessidade, burlando politicas de branch.
