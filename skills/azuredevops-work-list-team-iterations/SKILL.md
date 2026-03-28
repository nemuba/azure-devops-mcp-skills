---
name: azuredevops-work-list-team-iterations
description: Use when discovering the current or available team iterations in Azure DevOps before planning sprint work, capacity updates, or iteration-scoped queries.
---

# Skill: azuredevops_work_list_team_iterations

## O que faz
- Lista iteracoes de um time em um projeto Azure DevOps.
- Pode retornar apenas a iteracao atual com `timeframe: current`.
- Ajuda a descobrir `iterationId` e caminho da iteracao para comandos seguintes.

## Quando usar
- Antes de consultar ou atualizar capacidade do time.
- Quando voce precisa validar qual sprint/iteracao esta ativa.
- Quando nao sabe o nome exato do time ou projeto associado.

## Parametros obrigatorios
- Nenhum.

## Parametros opcionais
- `project`: nome ou ID do projeto.
- `team`: nome ou ID do time.
- `timeframe`: filtro temporal (`current`).

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "team": "Platform Team",
  "timeframe": "current"
}
```

## Retorno do comando
- Retorna uma lista de iteracoes visiveis para o time.
- Cada item traz identificador, nome, caminho, datas e URL da iteracao.
- O retorno pode vir como array direto ou como objeto com `count` e `value`.

Exemplo de retorno real:
```json
[
  {
    "id": "3d9c94ab-2ea2-4123-af19-f6a03201df6d",
    "name": "Inovações-202604-01",
    "path": "Siedos Inovação\\Inovações-202604-01",
    "attributes": {
      "startDate": "2026-03-24T00:00:00.000Z",
      "finishDate": "2026-04-06T00:00:00.000Z",
      "timeFrame": 1
    },
    "url": "https://dev.azure.com/siedos/b7c47b08-f158-4ab7-b7f1-7cdbd65c9bc0/02c0a6b6-3866-4904-8809-75576c8adc69/_apis/work/teamsettings/iterations/3d9c94ab-2ea2-4123-af19-f6a03201df6d"
  }
]
```

## Descricao dos campos retornados

### Campos principais
- `[]`: array de iteracoes (retorno direto) ou `value`: lista de iteracoes.
- `[].id`: identificador unico da iteracao (GUID). Usado em outros comandos como `iterationId`.
- `[].name`: nome amigavel da iteracao (ex: "Sprint 24", "Inovações-202604-01").
- `[].path`: caminho completo da iteracao no projeto (ex: "Projeto\\Iteration").

### Campos de atributos
- `[].attributes.startDate`: data/hora de inicio (ISO 8601).
- `[].attributes.finishDate`: data/hora de fim (ISO 8601).
- `[].attributes.timeFrame`: codigo numerico da classificacao temporal:
  - `0` = Past
  - `1` = Current
  - `2` = Future

### Campos de link
- `[].url`: endpoint REST da iteracao (pode ser usado para consultar detalhes).

### Campos opcionais (quando retornados)
- `[].attributes.deliveryPlans`: planos de entrega associados.
- `[].attributes.goal`: meta da iteracao.
- `[].attributes.startingType`: tipo de inicio.
- `[].attributes.length`: duracao em dias.

## Exemplos de uso

#### Iteracao atual
```json
{
  "project": "Siedos Inovação",
  "team": "Siedos Inovação Team",
  "timeframe": "current"
}
```

#### Todas as iteracoes de um time
```json
{
  "project": "Siedos Inovação",
  "team": "Siedos Inovação Team"
}
```

#### Iteracoes futuras
```json
{
  "project": "SST",
  "team": "SST Team",
  "timeframe": "future"
}
```

## Observacoes
- O `timeframe` suporta: `current`, `past`, `future`.
- O `id` retornado deve ser usado como `iterationId` em outros comandos (ex: `azuredevops_work_get_team_capacity`).
- O `path` corresponde ao `System.IterationPath` nos work items.

## Armadilhas comuns
- Assumir que a iteracao atual e unica sem validar `count`.
- Usar nome da iteracao quando o proximo comando exige `iterationId`.
- Informar `team` incorreto e interpretar lista vazia como erro de permissao.
