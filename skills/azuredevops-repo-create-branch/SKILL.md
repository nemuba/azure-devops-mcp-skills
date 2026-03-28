---
name: azuredevops-repo-create-branch
description: Use when creating a new branch in an Azure DevOps repository from a source branch or specific commit.
---

# Skill: azuredevops_repo_create_branch

## O que faz
- Cria uma nova branch em um repositorio Azure DevOps.
- Permite escolher branch base ou commit base.

## Quando usar
- Ao iniciar desenvolvimento de feature/hotfix.
- Quando precisa derivar branch de um commit especifico.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `branchName`: nome da nova branch.

## Parametros opcionais
- `sourceBranchName`, `sourceCommitId`, `project`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "branchName": "feature/auth-token",
  "sourceBranchName": "main"
}
```

## Retorno do comando
- Retorna confirmacao da branch criada e referencia do commit associado.

## Armadilhas comuns
- Tentar criar branch com nome que ja existe.
- Misturar `sourceBranchName` e `sourceCommitId` sem intencao clara.
