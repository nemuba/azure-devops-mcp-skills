---
name: azuredevops-wit-list-backlogs
description: Use when identifying available backlog categories for a project team before querying backlog items.
---

# Skill: azuredevops_wit_list_backlogs

## O que faz
- Lista os backlogs disponiveis para um time em um projeto Azure DevOps.
- Retorna categorias como Epic, Feature e Requirement (varia por processo).

## Quando usar
- Antes de chamar `azuredevops_wit_list_backlog_work_items`.
- Quando precisa descobrir o `backlogId` correto para um time.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `team`: nome ou ID do time.

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "team": "Platform Team"
}
```

## Retorno do comando
- Retorna uma lista de categorias de backlog habilitadas para o time.

Exemplo de retorno:
```json
{
  "count": 3,
  "value": [
    {
      "id": "Microsoft.EpicCategory",
      "name": "Epics",
      "rank": 1,
      "workItemTypes": ["Epic"]
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de backlogs retornados.
- `value`: lista de categorias de backlog.
- `value[].id`: identificador tecnico do backlog (use em chamadas seguintes).
- `value[].name`: nome exibido do backlog.
- `value[].rank`: ordem na hierarquia de backlog.
- `value[].workItemTypes`: tipos de work item associados.

## Armadilhas comuns
- Tentar usar nome do backlog quando a API espera `id`.
- Assumir que todos os times tem os mesmos backlogs habilitados.
