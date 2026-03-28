---
name: azuredevops-search-workitem
description: Use when searching Azure DevOps work items by text and filters such as project, area path, type, state, or assignee.
---

# Skill: azuredevops_search_workitem

## O que faz
- Pesquisa work items no Azure DevOps por texto.
- Permite filtrar por projeto, area path, tipo, estado e responsavel.
- Pode retornar facetas para apoiar refinamento da consulta.

## Quando usar
- Quando precisa encontrar bugs, tarefas ou historias por palavra-chave.
- Para montar listas de trabalho com filtros de estado/tipo.
- Para localizar rapidamente work items de um responsavel.

## Parametros obrigatorios
- `searchText`: texto usado na pesquisa.

## Parametros opcionais
- `project`: lista de projetos para consulta.
- `areaPath`: lista de areas para restringir resultados.
- `workItemType`: tipos de work item (ex.: `Bug`, `Task`, `User Story`).
- `state`: estados desejados (ex.: `Active`, `New`, `Closed`).
- `assignedTo`: lista de usuarios responsaveis.
- `includeFacets`: inclui dados agregados para refinamento.
- `skip`: deslocamento para paginacao.
- `top`: quantidade maxima de resultados.

## Exemplo minimo (JSON)
```json
{
  "searchText": "timeout",
  "project": ["Platform"],
  "workItemType": ["Bug"],
  "state": ["Active"],
  "assignedTo": ["ana.silva@empresa.com"],
  "top": 10
}
```

## Retorno do comando
- Retorna work items que correspondem ao texto e filtros aplicados.
- Cada resultado inclui identificador, titulo, tipo, estado e metadados basicos.

Exemplo de retorno:
```json
{
  "count": 2,
  "results": [
    {
      "id": 1201,
      "title": "Corrigir timeout em integracao",
      "workItemType": "Bug",
      "state": "Active",
      "assignedTo": "Ana Silva",
      "project": "Platform",
      "url": "https://dev.azure.com/org/Platform/_workitems/edit/1201"
    }
  ],
  "facets": {
    "state": [
      {
        "name": "Active",
        "count": 2
      }
    ]
  }
}
```

## Descricao dos campos retornados
- `count`: quantidade de itens retornados.
- `results`: lista de work items encontrados.
- `results[].id`: ID do work item.
- `results[].title`: titulo do work item.
- `results[].workItemType`: tipo do item (Bug, Task, etc.).
- `results[].state`: estado atual do item.
- `results[].assignedTo`: responsavel atual.
- `results[].project`: projeto ao qual o item pertence.
- `results[].url`: link para abrir o item no Azure DevOps.
- `facets`: agregacoes por categoria (quando `includeFacets` for `true`).

## Armadilhas comuns
- Misturar filtros muito restritivos e obter lista vazia por excesso de condicoes.
- Usar nomes de estado/tipo inconsistentes com o processo do projeto.
- Assumir que `assignedTo` sempre vem preenchido em todos os itens.
