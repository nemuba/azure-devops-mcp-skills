---
name: azuredevops-core-get-identity-ids
description: Use when resolving Azure DevOps identity IDs from user or group names, email addresses, or unique names before assigning reviewers or owners.
---

# Skill: azuredevops_core_get_identity_ids

## O que faz
- Busca identidades no Azure DevOps a partir de um filtro de pesquisa.
- Retorna IDs de identidade para usuarios/grupos encontrados.
- Ajuda a converter nome/email em ID reutilizavel em outras chamadas.

## Quando usar
- Antes de comandos que exigem IDs de reviewer, usuario ou membro de time.
- Quando voce tem apenas nome/email e precisa do identificador tecnico correto.
- Para validar ambiguidade entre usuarios com nomes parecidos.

## Parametros obrigatorios
- `searchFilter`: texto de busca (nome, unique name ou email).

## Parametros opcionais
- Nenhum.

## Exemplo minimo (JSON)
```json
{
  "searchFilter": "maria.silva@empresa.com"
}
```

## Retorno do comando
- Retorna uma lista de identidades que combinaram com o filtro.
- Cada item inclui ID de identidade e metadados de exibicao/autenticacao.

Exemplo de retorno:
```json
{
  "count": 1,
  "value": [
    {
      "id": "99999999-8888-7777-6666-555555555555",
      "displayName": "Maria Silva",
      "uniqueName": "maria.silva@empresa.com",
      "descriptor": "aad.YTk5OTk5OTktODg4OC03Nzc3LTY2NjYtNTU1NTU1NTU1NTU1",
      "subjectKind": "user"
    }
  ]
}
```

## Descricao dos campos retornados
- `count`: quantidade de identidades retornadas nesta resposta.
- `value`: lista de identidades encontradas.
- `value[].id`: identificador unico (GUID) da identidade.
- `value[].displayName`: nome exibido da identidade.
- `value[].uniqueName`: identificador unico textual (normalmente email/login).
- `value[].descriptor`: descritor interno de identidade no Azure DevOps.
- `value[].subjectKind`: tipo da identidade (`user`, `group`, etc.).

## Armadilhas comuns
- Usar um filtro muito generico e receber multiplas identidades ambiguas.
- Assumir que `displayName` e unico; prefira validar `uniqueName`.
- Reutilizar ID de outro tenant/organizacao por engano.
