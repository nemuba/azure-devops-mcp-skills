---
name: azuredevops-work-update-team-capacity
description: Use when updating Azure DevOps team member capacity for a specific iteration, including activity quotas and optional days off.
---

# Skill: azuredevops_work_update_team_capacity

## O que faz
- Atualiza capacidade de um membro do time em uma iteracao.
- Permite definir atividades e capacidade diaria por atividade.
- Permite registrar periodos de folga opcionais.

## Quando usar
- Quando o planejamento da sprint mudou e a capacidade precisa ser recalculada.
- Para refletir ferias, folgas ou redistribuicao de funcao.
- Depois de validar dados com `azuredevops_work_get_team_capacity`.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `team`: nome ou ID do time.
- `teamMemberId`: ID do membro do time.
- `iterationId`: ID da iteracao.
- `activities`: lista de atividades com `name` e `capacityPerDay`.

## Parametros opcionais
- `daysOff`: lista de periodos de folga (`start`, `end`).

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "team": "Platform Team",
  "teamMemberId": "d0f0b4f2-5d8a-4d0e-b2a0-9d1f436f5c86",
  "iterationId": "4f9f3f6d-12ab-4b44-8d8c-85ef0c0a2f41",
  "activities": [
    {
      "name": "Development",
      "capacityPerDay": 5
    }
  ],
  "daysOff": [
    {
      "start": "2026-03-25T00:00:00Z",
      "end": "2026-03-25T23:59:59Z"
    }
  ]
}
```

## Retorno do comando
- Retorna a configuracao atualizada de capacidade para o membro informado.
- Inclui atividades aplicadas e folgas persistidas para a iteracao.

Exemplo de retorno:
```json
{
  "teamMember": {
    "id": "d0f0b4f2-5d8a-4d0e-b2a0-9d1f436f5c86",
    "displayName": "Ana Silva"
  },
  "activities": [
    {
      "name": "Development",
      "capacityPerDay": 5
    }
  ],
  "daysOff": [
    {
      "start": "2026-03-25T00:00:00Z",
      "end": "2026-03-25T23:59:59Z"
    }
  ]
}
```

## Descricao dos campos retornados
- `teamMember.id`: ID do membro atualizado.
- `teamMember.displayName`: nome exibido do membro.
- `activities`: lista de atividades configuradas.
- `activities[].name`: nome da atividade.
- `activities[].capacityPerDay`: capacidade diaria aplicada para a atividade.
- `daysOff`: lista de folgas salvas.
- `daysOff[].start`: inicio da folga.
- `daysOff[].end`: fim da folga.

## Armadilhas comuns
- Atualizar membro errado por usar `displayName` em vez de `teamMemberId`.
- Enviar `capacityPerDay` com tipo invalido (string em vez de numero).
- Informar `daysOff` fora da iteracao e interpretar como erro do comando.
