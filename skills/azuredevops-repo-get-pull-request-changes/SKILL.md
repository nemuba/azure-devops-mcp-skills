---
name: azuredevops-repo-get-pull-request-changes
description: Use when retrieving file-level and line-level diffs for an Azure DevOps pull request iteration.
---

# Skill: azuredevops_repo_get_pull_request_changes

## O que faz
- Retorna mudancas de arquivos de um PR por iteracao.
- Pode incluir diff linha a linha e conteudo das linhas alteradas.

## Quando usar
- Para revisar impacto real de codigo em um PR.
- Para analise automatica de alteracoes entre iteracoes.

## Parametros obrigatorios
- `repositoryId`: ID do repositorio.
- `pullRequestId`: ID do PR.

## Parametros opcionais
- `iterationId`, `project`, `top`, `skip`, `compareTo`.
- `includeDiffs`, `includeLineContent`.

## Exemplo minimo (JSON)
```json
{
  "repositoryId": "11111111-2222-3333-4444-555555555555",
  "project": "Platform",
  "pullRequestId": 128,
  "top": 50,
  "includeDiffs": true,
  "includeLineContent": true
}
```

## Retorno do comando
- Retorna lista de arquivos alterados e, quando solicitado, diffs detalhados.

## Armadilhas comuns
- Solicitar muitos arquivos com diff completo e gerar payload muito grande.
- Comparar iteracoes erradas ao usar `compareTo`.
