---
name: azuredevops-pipelines-run-pipeline
description: Use when starting a new Azure DevOps pipeline run, previewing final YAML, or overriding run resources and stages.
---

# Skill: azuredevops_pipelines_run_pipeline

## O que faz
- Dispara uma nova execucao de pipeline.
- Suporta modo `previewRun` para validar YAML final sem criar run.
- Permite override de recursos, YAML e estagios pulados.

## Quando usar
- Para acionar CI/CD sob demanda.
- Para validar templates e expansao YAML antes da execucao real.

## Parametros obrigatorios
- `project`, `pipelineId`.

## Parametros opcionais
- `pipelineVersion`, `previewRun`, `resources`, `stagesToSkip`, `yamlOverride`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "pipelineId": 15,
  "previewRun": false
}
```

## Retorno do comando
- Retorna dados da run criada ou preview do YAML, conforme a opcao usada.

## Armadilhas comuns
- Rodar sem `previewRun` quando a intencao era apenas validar YAML.
- Enviar `yamlOverride` inconsistente com recursos/estagios.
