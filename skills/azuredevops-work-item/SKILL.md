---
title: Skill Work Item
tags:
  - opencode
  - azure-devops
  - mcp
  - work-item
status: draft
aliases:
  - Work Item Skill
---

# Skill: Work Item

## Catalogo de funcoes

Cada funcao deve ser documentada neste formato fixo:
- O que faz
- Quando usar
- Parametros obrigatorios
- Parametros opcionais
- Exemplo minimo
- Armadilhas comuns

Regra de uso:
- Priorizar a funcao minima necessaria para resolver a tarefa.
- Evitar sequencias longas de chamadas quando uma chamada direta resolve.
- Para qualquer comando de criacao, atualizacao ou exclusao, pedir confirmacao explicita do usuario antes de executar.

### `azuredevops_wit_get_work_item`
- O que faz: consulta um Work Item por ID.
- Quando usar: leitura pontual para triagem ou verificacao de estado.
- Parametros obrigatorios: `project`, `id`.
- Parametros opcionais: `fields`, `expand`.
- Exemplo minimo:
```json
{ "project": "MeuProjeto", "id": 123 }
```
- Armadilhas comuns: pedir muitos campos sem necessidade.

### `azuredevops_wit_list_work_item_revisions`
- O que faz: lista o historico de revisoes de um Work Item (auditoria de mudancas).
- Quando usar: validar se houve mudanca de iteracao, estado, responsavel ou campos-chave ao longo do tempo.
- Parametros obrigatorios: `project`, `workItemId`.
- Parametros opcionais: `top`, `skip`, `expand`.
- Exemplo minimo:
```json
{ "project": "MeuProjeto", "workItemId": 123, "top": 100, "expand": "Fields" }
```
- Armadilhas comuns: nao usar `expand: "Fields"` e perder visibilidade dos campos alterados por revisao.

### `azuredevops_wit_get_work_items_batch_by_ids`
- O que faz: consulta/listagem de varios itens por IDs.
- Quando usar: lote pequeno de IDs conhecidos.
- Parametros obrigatorios: `project`, `ids`.
- Parametros opcionais: `fields`.
- Exemplo minimo:
```json
{ "project": "MeuProjeto", "ids": [123, 124] }
```
- Armadilhas comuns: enviar lista grande sem filtrar campos.

### `azuredevops_wit_create_work_item`
- O que faz: criacao de Work Item com campos iniciais.
- Quando usar: abertura de bug, task ou user story.
- Parametros obrigatorios: `project`, `workItemType`, `fields`.
- Parametros opcionais: nenhum.
- Exemplo minimo:
```json
{
  "project": "MeuProjeto",
  "workItemType": "Task",
  "fields": [{ "name": "System.Title", "value": "Ajustar fluxo" }]
}
```
- Armadilhas comuns: usar tipo invalido para o processo.

### `azuredevops_wit_update_work_item`
- O que faz: atualizacao de campos e estado.
- Quando usar: mudar `System.State`, atribuir responsavel, ajustar iteracao.
- Parametros obrigatorios: `id`, `updates`.
- Parametros opcionais: nenhum.
- Exemplo minimo:
```json
{
  "id": 123,
  "updates": [{ "path": "/fields/System.State", "value": "Active" }]
}
```
- Armadilhas comuns: transicao de estado nao permitida.

### `azuredevops_wit_add_work_item_comment`
- O que faz: adiciona comentarios ao item.
- Quando usar: registrar progresso, bloqueio ou decisao.
- Parametros obrigatorios: `project`, `workItemId`, `comment`.
- Parametros opcionais: `format`.
- Exemplo minimo:
```json
{
  "project": "MeuProjeto",
  "workItemId": 123,
  "comment": "Atualizacao diaria enviada"
}
```
- Armadilhas comuns: comentario sem contexto objetivo.

### `azuredevops_wit_get_query_results_by_id`
- O que faz: consultas por query salva (WIQL) para obter IDs/resultado.
- Quando usar: triagem diaria e filtros recorrentes.
- Parametros obrigatorios: `id`.
- Parametros opcionais: `project`, `team`, `responseType`, `top`.
- Exemplo minimo:
```json
{ "id": "11111111-2222-3333-4444-555555555555", "responseType": "ids" }
```
- Armadilhas comuns: usar query errada de outro projeto/time.

### `azuredevops_wit_update_work_items_batch`
- O que faz: atualizacao em lote de varios Work Items.
- Quando usar: mudanca padrao de campo em varios itens.
- Parametros obrigatorios: `updates`.
- Parametros opcionais: nenhum.
- Exemplo minimo:
```json
{
  "updates": [
    {
      "id": 123,
      "path": "/fields/System.AssignedTo",
      "value": "usuario@empresa.com"
    }
  ]
}
```
- Armadilhas comuns: lote grande sem validar antes item a item.

### `azuredevops_wit_work_items_link`
- O que faz: links entre Work Items (parent, child, related etc.).
- Quando usar: organizar dependencia e hierarquia.
- Parametros obrigatorios: `project`, `updates`.
- Parametros opcionais: `type`, `comment` dentro de `updates`.
- Exemplo minimo:
```json
{
  "project": "MeuProjeto",
  "updates": [{ "id": 123, "linkToId": 124, "type": "related" }]
}
```
- Armadilhas comuns: inverter direcao parent/child.

### `azuredevops_wit_add_artifact_link`
- O que faz: link com PR e artifacts relacionados (branch, build, commit).
- Quando usar: rastreabilidade entre item e entrega tecnica.
- Parametros obrigatorios: `workItemId`, `project` e dados do artifact.
- Parametros opcionais: `comment`, `linkType`.
- Exemplo minimo:
```json
{
  "workItemId": 123,
  "project": "MeuProjeto",
  "projectId": "00000000-0000-0000-0000-000000000000",
  "repositoryId": "11111111-1111-1111-1111-111111111111",
  "pullRequestId": 45,
  "linkType": "Pull Request"
}
```
- Armadilhas comuns: usar IDs de repositorio/projeto incorretos.

### `azuredevops_wit_get_work_items_for_iteration`
- O que faz: lista itens por iteracao relacionada ao item.
- Quando usar: acompanhamento de sprint e capacidade.
- Parametros obrigatorios: `project`, `iterationId`.
- Parametros opcionais: `team`.
- Exemplo minimo:
```json
{ "project": "MeuProjeto", "team": "Time A", "iterationId": "123" }
```
- Armadilhas comuns: iteracao nao atribuida ao time.

## Campos essenciais

- `System.Id`: identificador unico. Ler sempre; nunca atualizar. Risco comum: confundir com ID externo.
- `System.WorkItemType`: tipo do item. Ler para validar fluxo; nao atualizar diretamente. Risco comum: assumir tipo igual entre projetos.
- `System.Title`: resumo do trabalho. Ler em listas; atualizar quando o escopo muda. Risco comum: titulo vago.
- `System.State`: estado atual. Ler antes de transicionar; atualizar em mudancas de fluxo. Risco comum: transicao nao permitida.
- `System.Reason`: motivo do estado. Ler ao auditar mudanca; atualizar junto com estado quando exigido. Risco comum: motivo invalido para o processo.
- `System.AssignedTo`: responsavel atual. Ler em triagem; atualizar em redistribuicao. Risco comum: identidade invalida.
- `System.AreaPath`: area funcional. Ler para roteamento; atualizar ao mover ownership. Risco comum: area inexistente.
- `System.IterationPath`: ciclo/sprint. Ler para planejamento; atualizar ao mover backlog/sprint. Risco comum: iteracao fora do time.
- `System.Description`: detalhes do item. Ler para contexto; atualizar em refinamento. Risco comum: texto sem estrutura.
- `System.Tags`: classificacao rapida. Ler para filtro; atualizar com tags padrao. Risco comum: taxonomia inconsistente.
- `System.CreatedDate`: data de criacao. Ler para analise; nao atualizar. Risco comum: usar como campo de ordenacao unico.
- `System.ChangedDate`: ultima alteracao. Ler para detectar atividade recente; nao atualizar. Risco comum: interpretar mudanca automatica como progresso real.

## Como descobrir campos

Fluxo seguro para campos customizados:
1. Identificar `project` e `workItemType` alvo.
2. Consultar um item real do mesmo tipo com `azuredevops_wit_get_work_item`.
3. Validar metadados do tipo com `azuredevops_wit_get_work_item_type`.
4. Iniciar atualizacoes pelos campos essenciais antes dos customizados.
5. Validar existencia e formato do campo antes de atualizar.

Regras de token-efficiency:
- Pedir apenas os campos necessarios em `fields`.
- Evitar expand desnecessario quando so precisa de valores basicos.

## Como identificar historico de revisoes

Fluxo recomendado para auditoria de mudancas:
1. Buscar revisoes com `azuredevops_wit_list_work_item_revisions` usando `top` suficiente e `expand: "Fields"`.
2. Comparar revisao a revisao os campos-chave: `System.IterationPath`, `System.State`, `System.AssignedTo`, `System.ChangedDate`.
3. Identificar o ponto de mudanca: quando um campo muda de valor entre `rev N` e `rev N+1`.
4. Se `System.IterationPath` permanecer igual em todas as revisoes, o item nao mudou de iteracao.
5. Para confirmar se a iteracao atual do item bate com a sprint atual do time, cruzar com `azuredevops_work_list_team_iterations` (`timeframe: current`) e comparar o `path`.

Exemplo pratico (mudou ou nao de iteracao):
```text
- Ler `System.IterationPath` em todas as revisoes.
- Se houver dois valores diferentes ao longo do historico, houve mudanca de iteracao.
- Se houver apenas um valor em todas as revisoes, nao houve mudanca de iteracao.
```

## Erros comuns

- Campo invalido/inexistente -> Causa provavel: nome de campo errado ou customizado nao mapeado -> Correcao: revisar metadados do tipo e ajustar path -> Prevencao: validar campo antes de update.
- Transicao de estado nao permitida -> Causa provavel: workflow do processo bloqueia mudanca -> Correcao: usar transicao valida com `System.Reason` compativel -> Prevencao: ler estado e razoes permitidas antes.
- Permissao insuficiente -> Causa provavel: usuario sem permissao no projeto/area -> Correcao: solicitar permissao ou executar com identidade correta -> Prevencao: validar acesso no inicio da operacao.
- Projeto/ID incorreto -> Causa provavel: `project` errado ou ID de outro ambiente -> Correcao: confirmar contexto e consultar item por ID -> Prevencao: fixar projeto/time no fluxo.
- Link duplicado ou tipo de link incorreto -> Causa provavel: relacao ja existe ou tipo inadequado -> Correcao: listar relacoes atuais e aplicar tipo correto -> Prevencao: verificar relacoes antes de criar link.
- Iteracao inexistente/fora do time -> Causa provavel: caminho de iteracao invalido para o time -> Correcao: listar iteracoes do time e reaplicar -> Prevencao: validar iteracao antes de atualizar `System.IterationPath`.

## Quando usar

- Esta e a primeira skill `work-item` para operacao orientada a Work Items no Azure DevOps MCP.
- Use para consulta, criacao e atualizacao de item com foco em estado/status.
- Use para registrar comentarios em fluxos de triagem e entrega.
- Use para ajustes de iteracao e acompanhamento por sprint.
- Use para vincular Work Item a PR e artifacts relacionados.

## Quando nao usar

- Nao usar para pipelines, wiki, test plans ou automacoes fora do dominio de Work Item.
- Nao usar para operacoes de repositorio sem relacao direta com Work Item.
- Nao usar quando a tarefa exige apenas leitura agregada de metricas (preferir consultas/reporting dedicados).
