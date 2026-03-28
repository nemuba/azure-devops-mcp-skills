---
name: azuredevops-wit-get-work-item-attachment
description: Use when downloading an Azure DevOps work item attachment by attachment ID, including screenshots and binary evidence files.
---

# Skill: azuredevops_wit_get_work_item_attachment

## O que faz
- Baixa um anexo de work item por `attachmentId`.
- Retorna o conteudo como recurso base64 para inspecao/consumo.

## Quando usar
- Para recuperar screenshots anexadas em bugs.
- Para analisar evidencias (logs, imagens, arquivos) ligadas ao item.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `attachmentId`: GUID do anexo.

## Parametros opcionais
- `fileName`: nome do arquivo para ajudar na deteccao de tipo MIME.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "attachmentId": "5c5f2d8a-2f22-4ab5-89c3-4c6a5778b84f",
  "fileName": "erro-login.png"
}
```

## Retorno do comando
- Retorna conteudo binario codificado e metadados do recurso.

Exemplo de retorno:
```json
{
  "attachmentId": "5c5f2d8a-2f22-4ab5-89c3-4c6a5778b84f",
  "fileName": "erro-login.png",
  "mimeType": "image/png",
  "contentBase64": "iVBORw0KGgoAAAANSUhEUgAA..."
}
```

## Descricao dos campos retornados
- `attachmentId`: GUID do anexo baixado.
- `fileName`: nome de arquivo associado.
- `mimeType`: tipo MIME detectado.
- `contentBase64`: conteudo do arquivo em base64.

## Armadilhas comuns
- Passar `attachmentId` incompleto extraido de URL.
- Tratar `contentBase64` como texto plano sem decodificar.
