---
name: azuredevops-repo-get-file-content
description: Use when retrieving the content of a specific file from an Azure DevOps repository at a branch, tag, or commit.
---

# Skill: azuredevops_repo_get_file_content

## O que faz
- Retorna conteudo de um arquivo do repositorio Git.
- Permite ler arquivo por branch, tag ou commit.

## Quando usar
- Para inspecionar codigo sem checkout local.
- Para comparar conteudo entre refs especificas.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.
- `path`: caminho completo do arquivo.

## Parametros opcionais
- `project`, `version`, `versionType`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "path": "/src/auth/token.ts",
  "version": "main",
  "versionType": "Branch"
}
```

## Retorno do comando
- Retorna conteudo textual do arquivo na versao solicitada.

## Armadilhas comuns
- Informar caminho relativo incompleto.
- Usar `versionType` incorreto para o valor de `version`.
