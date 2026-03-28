---
name: azuredevops-search-code
description: Use when searching Azure DevOps repositories for code snippets, symbols, or text patterns across projects, repositories, paths, or branches.
---

# Skill: azuredevops_search_code

## O que faz
- Pesquisa codigo nos repositorios do Azure DevOps por texto.
- Permite filtrar por projeto, repositorio, caminho e branch.
- Pode retornar facetas para ajudar a refinar a busca.

## Quando usar
- Quando voce precisa localizar implementacoes existentes rapidamente.
- Para investigar onde um simbolo, endpoint ou termo aparece no codigo.
- Para mapear impacto antes de mudancas maiores.

## Parametros obrigatorios
- `searchText`: texto/termo a buscar no codigo.

## Parametros opcionais
- `project`: lista de projetos para limitar a busca.
- `repository`: lista de repositorios para limitar a busca.
- `path`: lista de caminhos/pastas para restringir escopo.
- `branch`: lista de branches para consulta.
- `includeFacets`: inclui metadados agregados da busca.
- `skip`: deslocamento para paginacao.
- `top`: quantidade maxima de resultados.

## Exemplo minimo (JSON)
```json
{
  "searchText": "WorkItemTrackingHttpClient",
  "project": ["Platform"],
  "repository": ["backend-api"],
  "path": ["/src"],
  "branch": ["refs/heads/main"],
  "top": 5
}
```

## Retorno do comando
- Retorna resultados de busca com referencia de arquivo e trecho correspondente.
- Pode incluir informacoes de facetas quando solicitado.

Exemplo de retorno:
```json
{
  "count": 2,
  "results": [
    {
      "project": "Platform",
      "repository": "backend-api",
      "path": "/src/services/work-items.ts",
      "branch": "refs/heads/main",
      "matches": [
        {
          "line": 42,
          "text": "const client = new WorkItemTrackingHttpClient(...)"
        }
      ]
    }
  ],
  "facets": {
    "repository": [
      {
        "name": "backend-api",
        "count": 2
      }
    ]
  }
}
```

## Descricao dos campos retornados
- `count`: quantidade de resultados retornados.
- `results`: lista de ocorrencias encontradas.
- `results[].project`: projeto do resultado.
- `results[].repository`: repositorio do resultado.
- `results[].path`: caminho do arquivo encontrado.
- `results[].branch`: branch usada na pesquisa.
- `results[].matches`: trechos onde o texto foi encontrado.
- `results[].matches[].line`: numero da linha aproximada do match.
- `results[].matches[].text`: trecho de codigo/texto encontrado.
- `facets`: agregacoes por categoria (quando `includeFacets` for `true`).

## Armadilhas comuns
- Buscar com termo muito generico e receber ruido excessivo.
- Esquecer filtros de `project`/`repository` em organizacoes grandes.
- Interpretar ausencia de resultado sem validar branch e path usados.
