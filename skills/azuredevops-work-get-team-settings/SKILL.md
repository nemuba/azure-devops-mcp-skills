---
name: azuredevops-work-get-team-settings
description: Use when reading Azure DevOps team configuration such as default iteration, backlog iteration, and area path before changing planning behavior.
---

# Skill: azuredevops_work_get_team_settings

## O que faz
- Retorna configuracoes de time no Azure DevOps.
- Exibe iteracao padrao, backlog padrao e area path padrao.
- Ajuda a entender como o time esta configurado para planejamento.

## Quando usar
- Antes de alterar configuracoes de backlog/iteracao do time.
- Para diagnosticar por que itens aparecem em backlog inesperado.
- Para validar contexto de time em automacoes de planejamento.

## Parametros obrigatorios
- Nenhum.

## Parametros opcionais
- `project`: nome ou ID do projeto.
- `team`: nome ou ID do time.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "team": "Platform Team"
}
```

## Retorno do comando
- Retorna objeto unico com configuracoes principais do time.
- Inclui caminhos padrao de area e iteracao usados pelo time.

Exemplo de retorno:
```json
{
  "workingDays": [
    "monday",
    "tuesday",
    "wednesday",
    "thursday",
    "friday"
  ],
  "backlogIteration": {
    "id": "2d7da44e-4e31-4bb6-9c41-d2e6fb5cb3cd",
    "name": "Backlog",
    "path": "Platform\\Backlog"
  },
  "defaultIteration": {
    "id": "4f9f3f6d-12ab-4b44-8d8c-85ef0c0a2f41",
    "name": "Sprint 24",
    "path": "Platform\\Sprints\\Sprint 24"
  },
  "defaultAreaPath": {
    "id": "0c1d2e3f-4a5b-6789-0abc-def123456789",
    "name": "Platform",
    "path": "Platform"
  }
}
```

## Descricao dos campos retornados
- `workingDays`: dias uteis configurados para o time.
- `backlogIteration`: iteracao usada como backlog padrao.
- `backlogIteration.id`: ID da iteracao de backlog.
- `backlogIteration.name`: nome da iteracao de backlog.
- `backlogIteration.path`: caminho completo da iteracao de backlog.
- `defaultIteration`: iteracao padrao para novos itens.
- `defaultIteration.id`: ID da iteracao padrao.
- `defaultIteration.name`: nome da iteracao padrao.
- `defaultIteration.path`: caminho da iteracao padrao.
- `defaultAreaPath`: area path padrao do time.
- `defaultAreaPath.id`: ID da area padrao.
- `defaultAreaPath.name`: nome da area padrao.
- `defaultAreaPath.path`: caminho completo da area padrao.

## Armadilhas comuns
- Alterar automacoes sem validar `defaultIteration` e `backlogIteration`.
- Assumir que `workingDays` e igual para todos os times do projeto.
- Ignorar `defaultAreaPath` e criar itens em area incorreta.
