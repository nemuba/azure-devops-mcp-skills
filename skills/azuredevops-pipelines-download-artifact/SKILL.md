---
name: azuredevops-pipelines-download-artifact
description: Use when downloading a specific Azure DevOps pipeline artifact from a build to local path or base64 output.
---

# Skill: azuredevops_pipelines_download_artifact

## O que faz
- Faz download de um artefato de pipeline por nome.
- Pode salvar localmente ou retornar binario em base64.

## Quando usar
- Para consumir pacote gerado no CI.
- Para integrar artefato em processos de release automatizados.

## Parametros obrigatorios
- `project`, `buildId`, `artifactName`.

## Parametros opcionais
- `destinationPath`.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "buildId": 1001,
  "artifactName": "drop",
  "destinationPath": "/tmp/platform-drop"
}
```

## Retorno do comando
- Retorna confirmacao de download ou conteudo base64 quando sem destino.

## Armadilhas comuns
- Usar `artifactName` diferente do publicado no build.
- Esquecer `destinationPath` quando precisa persistir localmente.
