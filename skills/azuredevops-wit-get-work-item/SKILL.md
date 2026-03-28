---
name: azuredevops-wit-get-work-item
description: Use when retrieving a single Azure DevOps work item with optional field filtering, historical snapshot, or relation expansion.
---

# Skill: azuredevops_wit_get_work_item

## O que faz
- Busca um work item especifico por ID.
- Permite filtrar campos, expandir relacoes e consultar estado em uma data (`asOf`).

## Quando usar
- Para detalhar um item retornado por listas.
- Para inspecionar links/relacoes entre work items.

## Parametros obrigatorios
- `id`: ID do work item.
- `project`: nome ou ID do projeto.

## Parametros opcionais
- `fields`: lista de campos a retornar.
- `asOf`: snapshot temporal em ISO.
- `expand`: `none`, `fields`, `relations`, `links` ou `all`.

## Exemplo minimo (JSON)
```json
{
  "id": 1201,
  "project": "Platform",
  "fields": ["System.Id", "System.Title", "System.State"],
  "expand": "relations"
}
```

## Retorno do comando
- Retorna os detalhes do work item solicitado.

Exemplo de retorno:
```json
{
  "id": 1201,
  "rev": 8,
  "fields": {
    "System.Title": "Ajustar endpoint",
    "System.State": "Active",
    "System.WorkItemType": "Task"
  },
  "relations": [
    {
      "rel": "System.LinkTypes.Hierarchy-Reverse",
      "url": "https://dev.azure.com/org/_apis/wit/workItems/900"
    }
  ],
  "url": "https://dev.azure.com/org/_apis/wit/workItems/1201"
}
```

## Descricao dos campos retornados

### Campos principais
- `id`: ID do work item.
- `rev`: revisao atual retornada.
- `fields`: dicionario de campos do item.
- `relations`: lista de links com outros artefatos/work items (disponivel com `expand: relations`).
- `relations[].rel`: tipo da relacao.
- `relations[].url`: referencia do item relacionado.
- `url`: endpoint REST do work item.

### Campos do System (sempre disponiveis)
- `System.Id`: ID do work item.
- `System.Title`: titulo.
- `System.State`: estado (ex: Active, Closed, New).
- `System.WorkItemType`: tipo (ex: Task, Bug, User Story).
- `System.AssignedTo`: usuario atribuido (objeto com displayName, email).
- `System.CreatedBy`: usuario que criou.
- `System.CreatedDate`: data de criacao (ISO).
- `System.ChangedBy`: usuario que alterou.
- `System.ChangedDate`: data de alteracao (ISO).
- `System.IterationPath`: caminho da iteration.
- `System.AreaPath`: caminho da area.
- `System.Description`: descricao HTML.
- `System.Reason`: razao da mudanca de estado.
- `System.Priority`: prioridade (0-4).
- `System.Tags`: tags separadas por vírgula.

### Campos de Scheduling (Planejamento)
- `Microsoft.VSTS.Scheduling.OriginalEstimate`: estimativa original em horas.
- `Microsoft.VSTS.Scheduling.RemainingWork`: trabalho restante em horas.
- `Microsoft.VSTS.Scheduling.CompletedWork`: trabalho completado em horas.

### Campos de Data de Fechamento
- `Microsoft.VSTS.Common.ClosedDate`: data de fechamento (ISO).
- `Microsoft.VSTS.Common.StateChangeDate`: data da ultima mudanca de estado (ISO).
- `Microsoft.VSTS.Common.ActivatedDate`: data de ativacao (ISO).
- `Microsoft.VSTS.Common.ResolvedDate`: data de resolucao (ISO).

### Campos de Bug
- `Microsoft.VSTS.Common.Severity`: severidade (ex: 1 - Critical, 2 - High, 3 - Medium, 4 - Low).
- `Microsoft.VSTS.Common.Priority`: prioridade.
- `Microsoft.VSTS.TCM.ReproSteps`: passos para reproduzir.
- `System.BugBashId`: ID do Bugbash.

### Campos de User Story / Product Backlog Item
- `System.StoryPoints`: pontos de historia.
- `System.StackRank`: ordem no backlog.
- `System.Effort`: esforço estimado.

### Campos de Task
- `Microsoft.VSTS.TaskStatus`: status da task (ex: To Do, In Progress, Done).
- `Microsoft.VSTS.SharingType`: tipo de compartilhamento.
- `Microsoft.VSTS.SharingOwner`: proprietario do compartilhamento.

### Exemplos de uso

#### Campos basicos (identificacao e estado)
```json
{
  "id": 34134,
  "project": "Siedos Inovação",
  "fields": ["System.Id", "System.Title", "System.State", "System.WorkItemType"]
}
```

#### Campos de planejamento (horas)
```json
{
  "id": 34134,
  "project": "Siedos Inovação",
  "fields": [
    "Microsoft.VSTS.Scheduling.OriginalEstimate",
    "Microsoft.VSTS.Scheduling.RemainingWork",
    "Microsoft.VSTS.Scheduling.CompletedWork"
  ]
}
```

#### Campos de datas
```json
{
  "id": 34134,
  "project": "Siedos Inovação",
  "fields": [
    "System.CreatedDate",
    "Microsoft.VSTS.Common.ClosedDate",
    "System.ChangedDate"
  ]
}
```

#### Campos completos com relacoes
```json
{
  "id": 34134,
  "project": "Siedos Inovação",
  "expand": "all"
}
```

## Armadilhas comuns
- Usar `expand: all` sem necessidade e aumentar muito o payload.
- Esperar campos nao solicitados quando `fields` foi informado.
