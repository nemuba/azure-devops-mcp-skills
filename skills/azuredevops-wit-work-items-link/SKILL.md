---
name: azuredevops-wit-work-items-link
description: Use when creating links between Azure DevOps work items in batch (parent/child, related, successor, and others).
---

# Skill: azuredevops_wit_work_items_link

## O que faz
- Cria links entre work items em lote.
- Suporta tipos de relacao como `parent`, `child`, `related`, `predecessor`, etc.

## Quando usar
- Para montar ou corrigir estrutura de dependencia/hierarquia.
- Em migracoes e reorganizacoes de backlog.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `updates`: lista de links para criar.
- `updates[].id`: work item origem.
- `updates[].linkToId`: work item destino.

## Parametros opcionais
- `updates[].type`: tipo de relacao (padrao `related`).
- `updates[].comment`: comentario no link.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "updates": [
    {
      "id": 900,
      "linkToId": 1201,
      "type": "child",
      "comment": "Quebra da historia principal"
    }
  ]
}
```

## Retorno do comando
- Retorna status da criacao de links por operacao.

Exemplo de retorno:
```json
{
  "count": 1,
  "linked": [
    {
      "id": 900,
      "linkToId": 1201,
      "type": "child",
      "success": true
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de links processados.
- `linked`: lista de resultados de vinculo.
- `linked[].id`: item de origem.
- `linked[].linkToId`: item de destino.
- `linked[].type`: tipo de relacao aplicada.
- `linked[].success`: indica sucesso da operacao.

## Armadilhas comuns
- Inverter `parent`/`child` e criar hierarquia invertida.
- Tentar criar links duplicados sem checar relacoes existentes.
