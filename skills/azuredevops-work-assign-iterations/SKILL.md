---
name: azuredevops-work-assign-iterations
description: Use when assigning existing Azure DevOps iterations to a specific team so they appear in team settings and planning views.
---

# Skill: azuredevops_work_assign_iterations

## O que faz
- Atribui iteracoes existentes a um time de um projeto.
- Publica as iteracoes na configuracao do time para planejamento.
- Suporta atribuicao de varias iteracoes em uma chamada.

## Quando usar
- Depois de criar iteracoes no projeto.
- Quando um time nao enxerga uma sprint criada na arvore global.
- Para ajustar rapidamente backlog/sprints disponiveis ao time.

## Parametros obrigatorios
- `project`: nome ou ID do projeto.
- `team`: nome ou ID do time.
- `iterations`: lista com `identifier` e `path` das iteracoes.

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "team": "Platform Team",
  "iterations": [
    {
      "identifier": "8b5b5ea2-7d96-4ccb-bf4e-a6eb70284d15",
      "path": "Platform\\Sprints\\Sprint 25"
    }
  ]
}
```

## Retorno do comando
- Retorna as iteracoes atualmente atribuidas ao time apos a operacao.
- Cada item inclui identificador e caminho usado nas configuracoes do time.

Exemplo de retorno:
```json
{
  "count": 1,
  "value": [
    {
      "id": "8b5b5ea2-7d96-4ccb-bf4e-a6eb70284d15",
      "name": "Sprint 25",
      "path": "Platform\\Sprints\\Sprint 25",
      "url": "https://dev.azure.com/org/Platform/_apis/work/teamsettings/iterations/8b5b5ea2-7d96-4ccb-bf4e-a6eb70284d15"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de iteracoes atribuidas retornadas.
- `value`: lista de iteracoes disponiveis para o time.
- `value[].id`: identificador da iteracao atribuida.
- `value[].name`: nome da iteracao.
- `value[].path`: caminho completo da iteracao no projeto.
- `value[].url`: endpoint REST da atribuicao/iteracao no contexto do time.

## Armadilhas comuns
- Enviar `path` incorreto para o `identifier` informado.
- Tentar atribuir iteracao inexistente no projeto.
- Assumir sucesso sem validar retorno quando apenas parte das iteracoes foi aplicada.
