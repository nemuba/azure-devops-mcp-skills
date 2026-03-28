---
name: azuredevops-repo-vote-pull-request
description: Use when casting an approval or rejection vote on an Azure DevOps pull request as the authenticated reviewer.
---

# Skill: azuredevops_repo_vote_pull_request

## O que faz
- Registra voto do usuario autenticado em um PR.
- Pode aprovar, aprovar com sugestoes, aguardar autor ou rejeitar.

## Quando usar
- Durante processo formal de code review.
- Para atualizar decisao apos novas alteracoes no PR.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `pullRequestId`: ID do PR.
- `vote`: `Approved`, `ApprovedWithSuggestions`, `NoVote`, `WaitingForAuthor` ou `Rejected`.

## Parametros opcionais
- `project`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "pullRequestId": 128,
  "vote": "ApprovedWithSuggestions"
}
```

## Retorno do comando
- Retorna estado atualizado do reviewer/voto no PR.

## Armadilhas comuns
- Votar sem checar threads pendentes.
- Esquecer que `NoVote` remove decisao anterior.
