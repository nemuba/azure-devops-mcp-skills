---
name: azuredevops-repo-list-directory
description: Use when browsing files and folders in an Azure DevOps repository path at a specific branch, tag, or commit.
---

# Skill: azuredevops_repo_list_directory

## O que faz
- Lista arquivos e pastas de um caminho no repositorio.
- Suporta versao por branch, tag ou commit.
- Pode listar recursivamente com profundidade controlada.

## Quando usar
- Para explorar estrutura do repositorio via API.
- Para localizar caminhos antes de obter conteudo de arquivo.

## Parametros obrigatorios
- `repositoryId`: ID ou nome do repositorio.

## Parametros opcionais
- `path`, `project`, `version`, `versionType`, `recursive`, `recursionDepth`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "backend-api",
  "project": "Platform",
  "path": "/src",
  "version": "main",
  "versionType": "Branch",
  "recursive": true,
  "recursionDepth": 2
}
```

## Retorno do comando
- Retorna itens de diretorio (arquivos/pastas) conforme escopo informado.

## Armadilhas comuns
- Ativar recursao profunda em repositorios muito grandes.
- Confundir caminho raiz `/` com caminho relativo.
