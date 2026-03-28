---
name: azuredevops-core-list-projects
description: Use when listing Azure DevOps projects, filtering by state or name, and validating available project context before running other commands.
---

# Skill: azuredevops_core_list_projects

## O que faz
- Lista projetos da organizacao Azure DevOps.
- Permite filtrar por estado (`wellFormed`, `all`, `createPending`, `deleted`).
- Permite filtrar por nome parcial e paginar resultados.

## Quando usar
- No inicio de um fluxo para descobrir projetos disponiveis.
- Quando voce precisa confirmar o nome exato do projeto antes de chamar outros comandos `azuredevops_*`.
- Quando ha muitos projetos e voce quer filtrar por nome ou estado.

## Parametros obrigatorios
- Nenhum.

## Parametros opcionais
- `stateFilter`: filtra por estado do projeto.
- `top`: limita quantidade de itens retornados.
- `skip`: deslocamento para paginacao.
- `continuationToken`: continua paginacao anterior.
- `projectNameFilter`: filtra por trecho do nome do projeto.

## Exemplo minimo (JSON)
```json
{
  "stateFilter": "wellFormed",
  "top": 20,
  "projectNameFilter": "platform"
}
```

## Retorno do comando
- Retorna uma colecao paginada de projetos.
- Cada item representa um projeto com metadados basicos (identidade, estado, links e visibilidade).

Exemplo de retorno:
```json
{
  "count": 2,
  "value": [
    {
      "id": "11111111-2222-3333-4444-555555555555",
      "name": "Platform",
      "description": "Projeto da plataforma central",
      "url": "https://dev.azure.com/org/_apis/projects/11111111-2222-3333-4444-555555555555",
      "state": "wellFormed",
      "revision": 42,
      "visibility": "private",
      "lastUpdateTime": "2026-03-26T12:34:56Z"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de projetos retornados nesta resposta.
- `value`: lista de projetos.
- `value[].id`: identificador unico (GUID) do projeto.
- `value[].name`: nome do projeto (use este valor em comandos seguintes).
- `value[].description`: descricao textual do projeto (pode estar vazia).
- `value[].url`: endpoint REST do projeto.
- `value[].state`: estado atual do projeto (`wellFormed`, `createPending`, `deleted`, etc.).
- `value[].revision`: numero de revisao do metadado do projeto.
- `value[].visibility`: visibilidade do projeto (`private` ou `public`).
- `value[].lastUpdateTime`: data/hora da ultima atualizacao do projeto.

## Armadilhas comuns
- Assumir que o nome exibido esta correto sem validar com a listagem antes de usar em comandos seguintes.
- Esquecer paginacao (`top`, `skip`, `continuationToken`) em organizacoes com muitos projetos.
- Buscar projetos excluidos sem ajustar `stateFilter`.
