# Ferramentas

AdvBox expõe 20 ferramentas.

### 1. `advbox_settings`
**Input**: `query` (opcional)

Obtém todos os IDs e configurações da conta (usuários, origens, tipos de tarefa, fases, tipos de processo).

### 2. `advbox_list_customers`
**Input**: `page` (opcional), `page_size` (opcional), `name` (opcional), `cpf` (opcional), `cnpj` (opcional), `email` (opcional), `query` (opcional)

Lista clientes/contatos com filtros avançados (nome, cpf, cnpj, e-mail etc.

### 3. `advbox_get_customer`
**Input**: `id`, `query` (opcional), `ids` (opcional)

Busca os dados completos de um contato por ID.

### 4. `advbox_customers_birthdays`
**Input**: `page` (opcional), `page_size` (opcional), `query` (opcional)

Lista aniversariantes (para campanhas de relacionamento).

### 5. `advbox_create_customer`
**Input**: `name` (opcional), `email` (opcional), `cpf` (opcional), `cnpj` (opcional), `extra` (opcional)

Cria um novo contato/cliente. Campos conforme a API oficial (ex.: name, type, cpf/cnpj, email, phone) — envie o restante via `extra`.

### 6. `advbox_list_lawsuits`
**Input**: `page` (opcional), `page_size` (opcional), `number` (opcional), `cpf` (opcional), `cnpj` (opcional), `status` (opcional), `query` (opcional)

Lista/busca processos (22+ filtros).

### 7. `advbox_get_lawsuit`
**Input**: `id`, `query` (opcional), `ids` (opcional)

Busca um processo por ID (dados completos).

### 8. `advbox_create_lawsuit`
**Input**: `number` (opcional), `extra` (opcional)

Cria um processo. Campos conforme a API oficial (use advbox_settings para descobrir IDs de tipo/responsável); envie via campos nomeados + `extra`.

### 9. `advbox_update_lawsuit`
**Input**: `id`, `extra` (opcional), `ids` (opcional)

Atualiza um processo existente por ID.

### 10. `advbox_lawsuit_history`
**Input**: `lawsuit_id`, `page` (opcional), `page_size` (opcional), `query` (opcional), `lawsuit_ids` (opcional)

Histórico completo de um processo.

### 11. `advbox_lawsuit_movements`
**Input**: `lawsuit_id`, `page` (opcional), `page_size` (opcional), `query` (opcional), `lawsuit_ids` (opcional)

Lista todas as movimentações de um processo.

### 12. `advbox_create_movement`
**Input**: `description` (opcional), `extra` (opcional)

Adiciona uma movimentação manual a um processo.

### 13. `advbox_last_movements`
**Input**: `page` (opcional), `page_size` (opcional), `query` (opcional)

Última atualização de cada processo (resumo recente).

### 14. `advbox_list_posts`
**Input**: `page` (opcional), `page_size` (opcional), `query` (opcional)

Lista posts e anotações (tarefas/notas).

### 15. `advbox_create_post`
**Input**: `text` (opcional), `extra` (opcional)

Cria um novo post/anotação. Campos conforme a API oficial via campos nomeados + `extra`.

### 16. `advbox_publications`
**Input**: `lawsuit_id`, `page` (opcional), `page_size` (opcional), `query` (opcional), `lawsuit_ids` (opcional)

Lista as publicações oficiais de um processo.

### 17. `advbox_list_transactions`
**Input**: `page` (opcional), `page_size` (opcional), `type` (opcional), `status` (opcional), `start_date` (opcional), `end_date` (opcional), `query` (opcional)

Lista transações financeiras com filtros de data/tipo/status (via `query`).

### 18. `advbox_get_transaction`
**Input**: `id`, `query` (opcional), `ids` (opcional)

Detalha uma transação por ID. Bulk support: accepts ids for batched execution.

### 19. `advbox_create_transaction`
**Input**: `type` (opcional), `value` (opcional), `due_date` (opcional), `extra` (opcional)

Cria um lançamento financeiro (receita ou despesa).

### 20. `advbox_update_transaction`
**Input**: `id`, `value` (opcional), `due_date` (opcional), `status` (opcional), `extra` (opcional), `ids` (opcional)

Atualiza valor, vencimento ou status de pagamento de uma transação por ID.

## Prompts de exemplo

```
Busque o processo número X no AdvBox e mostre as últimas movimentações
Liste as transações financeiras vencidas este mês
Crie uma movimentação manual no processo Y registrando o andamento
```
