---
name: azuredevops-work-get-iteration-capacities
description: Use when retrieving capacity snapshots across all teams for a single Azure DevOps iteration in a project.
---

# Skill: azuredevops_work_get_iteration_capacities

## O que faz
- Retorna capacidade da iteracao para todos os times do projeto.
- Consolida visao de capacidade por time em uma chamada.
- Ajuda em planejamento multi-time ou comparacao entre squads.

## Quando usar
- Em planejamento de release envolvendo varios times.
- Para diagnosticar desequilibrio de capacidade entre equipes.
- Antes de realocar trabalho entre times na mesma iteracao.

## Parametros obrigatorios
- `iterationId`: ID da iteracao.

## Parametros opcionais
- `project`: nome ou ID do projeto.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "iterationId": "4f9f3f6d-12ab-4b44-8d8c-85ef0c0a2f41"
}
```

## Retorno do comando
- Retorna capacidade agregada por time para a iteracao informada.
- Cada entrada normalmente inclui o time e a lista de membros/capacidades.

Exemplo de retorno:
```json
{
  "count": 2,
  "value": [
    {
      "team": {
        "id": "1fd01953-1b53-45d9-a894-8f1d402d89a1",
        "name": "Platform Team"
      },
      "members": [
        {
          "teamMemberId": "d0f0b4f2-5d8a-4d0e-b2a0-9d1f436f5c86",
          "displayName": "Ana Silva",
          "totalCapacityPerDay": 5
        }
      ]
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de times retornados.
- `value`: lista de capacidades por time.
- `value[].team.id`: ID do time.
- `value[].team.name`: nome do time.
- `value[].members`: lista de membros do time nessa iteracao.
- `value[].members[].teamMemberId`: ID do membro no contexto de capacidade.
- `value[].members[].displayName`: nome exibido do membro.
- `value[].members[].totalCapacityPerDay`: capacidade diaria total consolidada.

## Armadilhas comuns
- Esperar granularidade de atividade quando o retorno pode trazer apenas consolidado por membro.
- Misturar `iterationId` de sprint diferente e comparar dados incorretamente.
- Ignorar diferencas de calendario/folgas ao comparar times.
