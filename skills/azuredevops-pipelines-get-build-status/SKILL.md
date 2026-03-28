---
name: azuredevops-pipelines-get-build-status
description: Use when checking the current status of an Azure DevOps build for polling or deployment gating.
---

# Skill: azuredevops_pipelines_get_build_status

## O que faz
- Consulta status atual de um build especifico.

## Quando usar
- Em loops de polling para aguardar conclusao.
- Como gate para processos de deploy dependentes do build.

## Parametros obrigatorios
- `project`, `buildId`.

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "buildId": 1001
}
```

## Retorno do comando
- Retorna estado e resultado atuais do build.

## Armadilhas comuns
- Interpretar status parcial como resultado final.
- Nao tratar estados intermediarios em automacao.
