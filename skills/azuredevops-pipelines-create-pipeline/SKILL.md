---
name: azuredevops-pipelines-create-pipeline
description: Use when creating a new Azure DevOps pipeline from a YAML file and repository configuration.
---

# Skill: azuredevops_pipelines_create_pipeline

## O que faz
- Cria uma pipeline com base em arquivo YAML do repositorio.
- Define nome, pasta e configuracao de origem (repo e conexao).

## Quando usar
- Para provisionar novas pipelines de CI/CD.
- Ao padronizar setup de projetos via automacao.

## Parametros obrigatorios
- `project`, `name`, `yamlPath`, `repositoryType`, `repositoryName`.

## Parametros opcionais
- `folder`, `repositoryId`, `repositoryConnectionId`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "name": "platform-ci",
  "yamlPath": "/azure-pipelines.yml",
  "repositoryType": "AzureReposGit",
  "repositoryName": "platform-api"
}
```

## Retorno do comando
- Retorna a pipeline criada com `id`, nome e configuracao de repositorio.

## Armadilhas comuns
- Informar `repositoryName` incorreto (especialmente em GitHub: `owner/repo`).
- Usar `yamlPath` inexistente na branch padrao.
