---
name: azuredevops-core-list-project-teams
description: Use when listing Azure DevOps teams in a project, validating team names, or filtering to teams where the current user is a member.
---

# Skill: azuredevops_core_list_project_teams

## O que faz
- Lista os times de um projeto Azure DevOps.
- Permite filtrar para retornar apenas times dos quais o usuario autenticado participa.
- Permite paginacao para ambientes com muitos times.

## Quando usar
- Quando voce precisa descobrir o nome exato de um time antes de chamar comandos que exigem `team`.
- Quando voce quer validar rapidamente em quais times voce tem participacao (`mine: true`).
- Quando esta montando fluxos de sprint/iteracao e precisa do contexto de time.

## Parametros obrigatorios
- Nenhum.

## Parametros opcionais
- `project`: nome ou ID do projeto.
- `mine`: retorna apenas times do usuario autenticado.
- `top`: limita a quantidade de itens retornados.
- `skip`: deslocamento para paginacao.

## Exemplo minimo (JSON)
```json
{
  "project": "MeuProjeto",
  "mine": true,
  "top": 20
}
```

## Retorno do comando
- Retorna uma colecao de times do projeto.
- Cada item contem metadados basicos de identificacao do time.

Exemplo de retorno:
```json
{
  "count": 2,
  "value": [
    {
      "id": "aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
      "name": "Time Plataforma",
      "description": "Time responsavel pela plataforma",
      "url": "https://dev.azure.com/org/_apis/projects/MeuProjeto/teams/aaaaaaaa-bbbb-cccc-dddd-eeeeeeeeeeee",
      "projectName": "MeuProjeto",
      "projectId": "11111111-2222-3333-4444-555555555555"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de times retornados nesta resposta.
- `value`: lista de times.
- `value[].id`: identificador unico (GUID) do time.
- `value[].name`: nome do time (use este valor em comandos seguintes).
- `value[].description`: descricao textual do time (pode estar vazia).
- `value[].url`: endpoint REST do time.
- `value[].projectName`: nome do projeto ao qual o time pertence.
- `value[].projectId`: identificador unico (GUID) do projeto ao qual o time pertence.

## Armadilhas comuns
- Informar um `project` incorreto e concluir que o time nao existe.
- Usar `mine: true` e achar que nao ha times, quando o problema e permissao/membro.
- Nao paginar (`top`, `skip`) em projetos com muitos times.
