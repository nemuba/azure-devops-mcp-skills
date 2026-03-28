---
name: azuredevops-work-get-team-capacity
description: Use when viewing per-member Azure DevOps team capacity for a specific iteration, including activity allocations and days off.
---

# Skill: azuredevops_work_get_team_capacity

## O que faz
- Consulta a capacidade de membros de um time em uma iteracao especifica.
- Mostra atividades, capacidade diaria e folgas por membro.
- Serve como base para ajustes de alocacao da sprint.

## Quando usar
- Antes de alterar capacidade com `azuredevops_work_update_team_capacity`.
- Durante planejamento de sprint para identificar sobrecarga.
- Para auditoria de configuracao de capacidade de time.

## Parametros obrigatorios
- `team`: nome ou ID do time.
- `iterationId`: ID da iteracao.

## Parametros opcionais
- `project`: nome ou ID do projeto.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "team": "Platform Team",
  "iterationId": "4f9f3f6d-12ab-4b44-8d8c-85ef0c0a2f41"
}
```

## Retorno do comando
- Retorna capacidade por membro do time para a iteracao.
- Cada membro pode ter varias atividades e periodos de folga.

Exemplo de retorno:
```json
{
  "count": 2,
  "value": [
    {
      "teamMember": {
        "id": "d0f0b4f2-5d8a-4d0e-b2a0-9d1f436f5c86",
        "displayName": "Ana Silva"
      },
      "activities": [
        {
          "name": "Development",
          "capacityPerDay": 6
        }
      ],
      "daysOff": [
        {
          "start": "2026-03-20T00:00:00Z",
          "end": "2026-03-20T23:59:59Z"
        }
      ]
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de membros retornados.
- `value`: lista de capacidade por membro.
- `value[].teamMember.id`: ID do membro do time (usado em atualizacoes).
- `value[].teamMember.displayName`: nome exibido do membro.
- `value[].activities`: lista de atividades configuradas.
- `value[].activities[].name`: nome da atividade (ex.: `Development`).
- `value[].activities[].capacityPerDay`: capacidade diaria para a atividade.
- `value[].daysOff`: periodos de indisponibilidade.
- `value[].daysOff[].start`: inicio da folga.
- `value[].daysOff[].end`: fim da folga.

## Armadilhas comuns
- Usar `displayName` no update em vez de `teamMember.id`.
- Ignorar `daysOff` e superestimar capacidade real.
- Confundir `iterationId` de outro projeto/time.
