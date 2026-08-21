---
name: advbox-mcp
description: Skill da REST API do AdvBox na MCP.AI: 20 endpoints em /api/advbox. Wrapper da API oficial do AdvBox (software jurídico): processos (e histórico, movimentações, publicações), clientes/contatos, tarefas/anotações e financeiro (transações). Leitura + criação e atualização de processos e transações. Autenticação por token de API do escritório. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# AdvBox — REST API skill

Você tem acesso à **AdvBox** REST API na MCP.AI.

> Wrapper da API oficial do AdvBox (software jurídico): processos (e histórico, movimentações, publicações), clientes/contatos, tarefas/anotações e financeiro (transações). Leitura + criação e atualização de processos e transações. Autenticação por token de API do escritório.

## Base URL

```
https://api.mcp.ai/api/advbox
```

Todo endpoint é um **POST** na Base URL + o path abaixo. Os parâmetros vão no corpo JSON.

## Autenticação

Inclua em toda request:

```
Authorization: Bearer sk_live_...
Content-Type: application/json
```

> Gere sua chave em **https://app.mcp.ai/settings/api-keys** (workspace API key `sk_live_…`, não expira, revogável). Uma única chave serve pra todos os seus MCPs.

## Formato de resposta

```json
{ "ok": true, "tool": "<tool_id>", "result": <payload> }
```

## Exemplo cURL

```bash
curl -X POST https://api.mcp.ai/api/advbox/create/customer \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/advbox/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (20)

#### `advbox_create_customer`

Cria um novo contato/cliente. Campos conforme a API oficial (ex.: name, type, cpf/cnpj, email, phone) — envie o restante via `extra`. _(POST /api/advbox/create/customer)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `name` | string | Não | Nome do contato. |
| `email` | string | Não |  |
| `cpf` | string | Não |  |
| `cnpj` | string | Não |  |
| `extra` | object | Não | Campos adicionais do body conforme a API oficial do AdvBox. |

#### `advbox_create_lawsuit`

Cria um processo. Campos conforme a API oficial (use advbox_settings para descobrir IDs de tipo/responsável); envie via campos nomeados + `extra`. _(POST /api/advbox/create/lawsuit)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `number` | string | Não | Número do processo. |
| `extra` | object | Não | Campos adicionais do body conforme a API oficial do AdvBox. |

#### `advbox_create_movement`

Adiciona uma movimentação manual a um processo. _(POST /api/advbox/create/movement)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `description` | string | Não | Descrição da movimentação. |
| `extra` | object | Não | Campos adicionais do body conforme a API oficial do AdvBox. |

#### `advbox_create_post`

Cria um novo post/anotação. Campos conforme a API oficial via campos nomeados + `extra`. _(POST /api/advbox/create/post)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `text` | string | Não | Texto do post/anotação. |
| `extra` | object | Não | Campos adicionais do body conforme a API oficial do AdvBox. |

#### `advbox_create_transaction`

Cria um lançamento financeiro (receita ou despesa). _(POST /api/advbox/create/transaction)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `type` | string | Não | Tipo do lançamento (receita/despesa). |
| `value` | string | Não |  |
| `due_date` | string | Não |  |
| `extra` | object | Não | Campos adicionais do body conforme a API oficial do AdvBox. |

#### `advbox_customers_birthdays`

Lista aniversariantes (para campanhas de relacionamento). _(POST /api/advbox/customers/birthdays)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não |  |
| `page_size` | integer | Não |  |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |

#### `advbox_get_customer`

Busca os dados completos de um contato por ID. _(POST /api/advbox/get/customer)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Path: id |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `advbox_get_lawsuit`

Busca um processo por ID (dados completos). _(POST /api/advbox/get/lawsuit)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Path: id |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `advbox_get_transaction`

Detalha uma transação por ID. _(POST /api/advbox/get/transaction)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Path: id |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `advbox_last_movements`

Última atualização de cada processo (resumo recente). _(POST /api/advbox/last/movements)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não |  |
| `page_size` | integer | Não |  |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |

#### `advbox_lawsuit_history`

Histórico completo de um processo. _(POST /api/advbox/lawsuit/history)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `lawsuit_id` | string | Sim | Path: lawsuit_id |
| `page` | integer | Não |  |
| `page_size` | integer | Não |  |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |
| `lawsuit_ids` | string[] | Não | Bulk mode: multiple values for lawsuit_id |

#### `advbox_lawsuit_movements`

Lista todas as movimentações de um processo. _(POST /api/advbox/lawsuit/movements)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `lawsuit_id` | string | Sim | Path: lawsuit_id |
| `page` | integer | Não |  |
| `page_size` | integer | Não |  |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |
| `lawsuit_ids` | string[] | Não | Bulk mode: multiple values for lawsuit_id |

#### `advbox_list_customers`

Lista clientes/contatos com filtros avançados (nome, cpf, cnpj, e-mail etc. _(POST /api/advbox/list/customers)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não |  |
| `page_size` | integer | Não |  |
| `name` | string | Não |  |
| `cpf` | string | Não |  |
| `cnpj` | string | Não |  |
| `email` | string | Não |  |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |

#### `advbox_list_lawsuits`

Lista/busca processos (22+ filtros). _(POST /api/advbox/list/lawsuits)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não |  |
| `page_size` | integer | Não |  |
| `number` | string | Não |  |
| `cpf` | string | Não |  |
| `cnpj` | string | Não |  |
| `status` | string | Não |  |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |

#### `advbox_list_posts`

Lista posts e anotações (tarefas/notas). _(POST /api/advbox/list/posts)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não |  |
| `page_size` | integer | Não |  |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |

#### `advbox_list_transactions`

Lista transações financeiras com filtros de data/tipo/status (via `query`). _(POST /api/advbox/list/transactions)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `page` | integer | Não |  |
| `page_size` | integer | Não |  |
| `type` | string | Não | Tipo (receita/despesa). |
| `status` | string | Não |  |
| `start_date` | string | Não |  |
| `end_date` | string | Não |  |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |

#### `advbox_publications`

Lista as publicações oficiais de um processo. _(POST /api/advbox/publications)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `lawsuit_id` | string | Sim | Path: lawsuit_id |
| `page` | integer | Não |  |
| `page_size` | integer | Não |  |
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |
| `lawsuit_ids` | string[] | Não | Bulk mode: multiple values for lawsuit_id |

#### `advbox_settings`

Obtém todos os IDs e configurações da conta (usuários, origens, tipos de tarefa, fases, tipos de processo). _(POST /api/advbox/settings)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `query` | object | Não | Parâmetros de query adicionais conforme a API oficial do AdvBox. |

#### `advbox_update_lawsuit`

Atualiza um processo existente por ID. _(POST /api/advbox/update/lawsuit)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Path: id |
| `extra` | object | Não | Campos adicionais do body conforme a API oficial do AdvBox. |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

#### `advbox_update_transaction`

Atualiza valor, vencimento ou status de pagamento de uma transação por ID. _(POST /api/advbox/update/transaction)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `id` | string | Sim | Path: id |
| `value` | string | Não |  |
| `due_date` | string | Não |  |
| `status` | string | Não |  |
| `extra` | object | Não | Campos adicionais do body conforme a API oficial do AdvBox. |
| `ids` | string[] | Não | Bulk mode: multiple values for id |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_advbox` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
