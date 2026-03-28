---
name: azuredevops-work-create-iterations
description: Use when creating one or more Azure DevOps iterations for a project, including optional start and finish dates for planning cadences.
---

# Skill: azuredevops_work_create_iterations

## O que faz
- Cria uma ou varias iteracoes dentro de um projeto Azure DevOps.
- Permite definir nome e, opcionalmente, datas de inicio/fim para cada iteracao.
- Facilita preparar estrutura de sprints antes de atribuir aos times.

## Quando usar
- Ao iniciar um novo ciclo de planejamento com sprints ainda nao criadas.
- Quando precisa padronizar datas de iteracoes futuras.
- Antes de usar comandos de atribuicao de iteracao para time.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `iterations`: lista de iteracoes para criar (`iterationName`, e opcionalmente datas).

## Parametros opcionais
- `iterations[].startDate`: data/hora de inicio em ISO.
- `iterations[].finishDate`: data/hora de fim em ISO.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "iterations": [
    {
      "iterationName": "Sprint 25",
      "startDate": "2026-03-30T00:00:00Z",
      "finishDate": "2026-04-12T23:59:59Z"
    }
  ]
}
```

## Retorno do comando
- Retorna as iteracoes criadas com metadados e caminhos resultantes.
- Em criacoes em lote, cada item representa uma iteracao criada.

Exemplo de retorno:
```json
{
  "count": 1,
  "value": [
    {
      "id": "8b5b5ea2-7d96-4ccb-bf4e-a6eb70284d15",
      "name": "Sprint 25",
      "path": "Platform\\Sprint 25",
      "attributes": {
        "startDate": "2026-03-30T00:00:00Z",
        "finishDate": "2026-04-12T23:59:59Z"
      },
      "url": "https://dev.azure.com/org/Platform/_apis/wit/classificationnodes/Iterations/Sprint%2025"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de iteracoes criadas e retornadas.
- `value`: lista de iteracoes criadas.
- `value[].id`: identificador da iteracao.
- `value[].name`: nome configurado para a iteracao.
- `value[].path`: caminho completo na arvore de iteracoes.
- `value[].attributes.startDate`: data/hora inicial configurada.
- `value[].attributes.finishDate`: data/hora final configurada.
- `value[].url`: endpoint REST da iteracao criada.

## Armadilhas comuns
- Enviar datas fora do padrao ISO e receber erro de validacao.
- Criar iteracoes com nomes duplicados no mesmo caminho.
- Esquecer de atribuir iteracoes ao time apos cria-las.
