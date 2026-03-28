---
name: azuredevops-repo-update-pull-request-reviewers
description: Use when adding or removing reviewers on an Azure DevOps pull request by identity ID.
---

# Skill: azuredevops_repo_update_pull_request_reviewers

## O que faz
- Adiciona ou remove reviewers de um PR.
- Opera por IDs de identidade Azure DevOps.

## Quando usar
- Para incluir aprovadores obrigatorios em PRs.
- Para remover reviewers quando o ownership mudou.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `pullRequestId`: ID do PR.
- `reviewerIds`: lista de IDs dos reviewers.
- `action`: `add` ou `remove`.

## Parametros opcionais
- `project`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "pullRequestId": 128,
  "action": "add",
  "reviewerIds": [
    "vssgp.Uy0xLTktMTU1..."
  ]
}
```

## Retorno do comando
- Retorna o estado atualizado de reviewers do PR.

## Armadilhas comuns
- Tentar usar email/nome em vez de identity ID.
- Remover reviewers exigidos por politica de branch.
