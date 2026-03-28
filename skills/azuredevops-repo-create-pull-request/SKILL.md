---
name: azuredevops-repo-create-pull-request
description: Use when creating a new Azure DevOps pull request between branches, optionally linking work items and applying labels.
---

# Skill: azuredevops_repo_create_pull_request

## O que faz
- Cria um pull request em um repositorio do Azure DevOps.
- Define branch de origem/destino, titulo e descricao.
- Permite criar como draft, vincular work items e adicionar labels.

## Quando usar
- Ao finalizar uma branch de feature e abrir PR para revisao.
- Quando precisa padronizar criacao de PR com metadados iniciais.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `sourceRefName`: branch de origem (`refs/heads/...`).
- `targetRefName`: branch de destino (`refs/heads/...`).
- `title`: titulo do PR.

## Parametros opcionais
- `description`, `isDraft`, `project`, `workItems`, `forkSourceRepositoryId`, `labels`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "sourceRefName": "refs/heads/feature/auth-token",
  "targetRefName": "refs/heads/main",
  "title": "feat: adiciona validacao de token",
  "description": "Implementa validacao e testes",
  "isDraft": true,
  "labels": ["backend", "security"]
}
```

## Retorno do comando
- Retorna os dados do PR criado (ID, status, branches, links e metadados).

## Armadilhas comuns
- Informar branch sem prefixo `refs/heads/`.
- Usar nome de repositorio sem informar `project`.
- Exceder limite de tamanho em `description`.
