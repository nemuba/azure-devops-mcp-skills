---
name: azuredevops-wit-work-item-unlink
description: Use when removing one or more links from an Azure DevOps work item by relation type and optional URL match.
---

# Skill: azuredevops_wit_work_item_unlink

## O que faz
- Remove links de um work item.
- Permite filtrar por tipo de link e opcionalmente por URL.

## Quando usar
- Para limpar relacoes incorretas em itens.
- Para remover artefatos/relacoes obsoletas.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `id`: ID do work item origem.

## Parametros opcionais
- `type`: tipo de link para remover.
- `url`: remove apenas o link que corresponde a URL.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "id": 900,
  "type": "child"
}
```

## Retorno do comando
- Retorna resultado da remocao de links no item.

Exemplo de retorno:
```json
{
  "id": 900,
  "removedCount": 2,
  "success": true
}
```

## Descricao dos campos retornados
- `id`: ID do work item atualizado.
- `removedCount`: quantidade de links removidos.
- `success`: indica se a operacao concluiu sem erro.

## Armadilhas comuns
- Remover por `type` sem `url` e apagar mais links do que o esperado.
- Usar tipo de relacao errado e achar que nao havia links.
