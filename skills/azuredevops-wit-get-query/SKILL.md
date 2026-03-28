---
name: azuredevops-wit-get-query
description: Use when reading Azure DevOps saved query metadata or WIQL before executing it.
---

# Skill: azuredevops_wit_get_query

## O que faz
- Busca uma query salva por ID ou caminho.
- Pode expandir clausulas, WIQL e detalhes adicionais.

## Quando usar
- Antes de executar query para validar definicao.
- Para inspecionar filtros e estrutura de uma consulta compartilhada.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `query`: ID ou caminho da query.

## Parametros opcionais
- `expand`: `None`, `Wiql`, `Clauses`, `All` ou `Minimal`.
- `depth`: profundidade de expansao.
- `includeDeleted`: inclui itens excluidos.
- `useIsoDateFormat`: usa formato ISO em datas.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "query": "Shared Queries/Backlog Ativo",
  "expand": "Wiql"
}
```

## Retorno do comando
- Retorna metadados da query e opcionalmente o WIQL.

Exemplo de retorno:
```json
{
  "id": "4a8bc9f0-1234-4f4a-9aa1-0ea0652f13a1",
  "name": "Backlog Ativo",
  "path": "Shared Queries/Backlog Ativo",
  "wiql": "SELECT [System.Id] FROM WorkItems WHERE [System.State] <> 'Closed'"
}
```

## Descricao dos campos retornados
- `id`: ID da query.
- `name`: nome da query.
- `path`: caminho completo da query.
- `wiql`: consulta WIQL (quando expandido).

## Armadilhas comuns
- Executar query sem validar se o caminho esta correto.
- Assumir que `wiql` vira no retorno sem definir `expand` apropriado.
