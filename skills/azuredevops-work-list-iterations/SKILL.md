---
name: azuredevops-work-list-iterations
description: Use when browsing project iteration hierarchy in Azure DevOps, including nested children, before assigning teams or selecting iteration IDs.
---

# Skill: azuredevops_work_list_iterations

## O que faz
- Lista iteracoes de um projeto Azure DevOps.
- Pode retornar estrutura hierarquica com filhos conforme profundidade.
- Permite excluir IDs especificos da resposta.

## Quando usar
- Para mapear a arvore de iteracoes do projeto.
- Antes de atribuir iteracoes para times.
- Quando precisa identificar caminhos exatos de iteracao.

## Parametros obrigatorios
- Nenhum.

## Parametros opcionais
- `project`: nome ou ID do projeto.
- `depth`: profundidade de filhos retornados.
- `excludedIds`: lista de IDs de iteracoes a excluir.

## Exemplo minimo (JSON)
```json
{
  "project": "Platform",
  "depth": 2,
  "excludedIds": [
    10
  ]
}
```

## Retorno do comando
- Retorna a estrutura de iteracoes do projeto, podendo incluir filhos.
- Cada no de iteracao contem metadados e subiteracoes em `children`.

Exemplo de retorno:
```json
{
  "count": 1,
  "value": [
    {
      "id": 101,
      "identifier": "4f9f3f6d-12ab-4b44-8d8c-85ef0c0a2f41",
      "name": "Sprints",
      "path": "Platform\\Sprints",
      "children": [
        {
          "id": 102,
          "identifier": "8b5b5ea2-7d96-4ccb-bf4e-a6eb70284d15",
          "name": "Sprint 25",
          "path": "Platform\\Sprints\\Sprint 25",
          "children": []
        }
      ]
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de nos raiz retornados.
- `value`: lista de iteracoes raiz.
- `value[].id`: ID numerico interno do no de iteracao.
- `value[].identifier`: GUID da iteracao (util para outras APIs).
- `value[].name`: nome da iteracao.
- `value[].path`: caminho completo da iteracao.
- `value[].children`: lista de subiteracoes (estrutura recursiva).

## Armadilhas comuns
- Confundir `id` numerico com `identifier` GUID em comandos que exigem um tipo especifico.
- Usar `depth` baixo e concluir que nao existem subiteracoes.
- Ignorar `path` e usar nomes iguais em ramos diferentes da arvore.
