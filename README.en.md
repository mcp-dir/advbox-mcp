# AdvBox

### AdvBox for Claude, ChatGPT and AI agents

Wrapper for the official AdvBox API (legal practice management): cases (with history, movements, publications), clients/contacts, tasks/notes and finance (transactions). Read + create and update for cases and transactions. Authenticated by the firm's API token.

- 📊 **20 tools**
- ✏️ **Read and write**
- 💬 **Works with any MCP client**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Magic-link login (no password)**

[Portuguese version](README.md) · [Full docs (PT-BR)](docs/)

---

## One-click install

### Claude (Web and Desktop)

[➕ Open in Claude and connect](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

Manual: [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Add custom connector** → name `AdvBox`, URL `https://api.mcp.ai/p_advbox`.

### Cursor

[➕ Install in Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=advbox&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9hZHZib3gifQ==)

### VS Code (Copilot Chat)

[➕ Install in VS Code](vscode:mcp/install?name=advbox&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_advbox%22%7D)

### Any other MCP-over-HTTP client

```
https://api.mcp.ai/p_advbox
```

---

## 20 tools

| Tool | Description |
|---|---|
| `advbox_settings` | Obtém todos os IDs e configurações da conta (usuários, origens, tipos de tarefa, fases, tipos de processo). |
| `advbox_list_customers` | Lista clientes/contatos com filtros avançados (nome, cpf, cnpj, e-mail etc. |
| `advbox_get_customer` | Busca os dados completos de um contato por ID. |
| `advbox_customers_birthdays` | Lista aniversariantes (para campanhas de relacionamento). |
| `advbox_create_customer` | Cria um novo contato/cliente. Campos conforme a API oficial (ex.: name, type, cpf/cnpj, email, phone) — envie o restante via `extra`. |
| `advbox_list_lawsuits` | Lista/busca processos (22+ filtros). |
| `advbox_get_lawsuit` | Busca um processo por ID (dados completos). |
| `advbox_create_lawsuit` | Cria um processo. Campos conforme a API oficial (use advbox_settings para descobrir IDs de tipo/responsável); envie via campos nomeados + `extra`. |
| `advbox_update_lawsuit` | Atualiza um processo existente por ID. |
| `advbox_lawsuit_history` | Histórico completo de um processo. |
| `advbox_lawsuit_movements` | Lista todas as movimentações de um processo. |
| `advbox_create_movement` | Adiciona uma movimentação manual a um processo. |
| `advbox_last_movements` | Última atualização de cada processo (resumo recente). |
| `advbox_list_posts` | Lista posts e anotações (tarefas/notas). |
| `advbox_create_post` | Cria um novo post/anotação. Campos conforme a API oficial via campos nomeados + `extra`. |
| `advbox_publications` | Lista as publicações oficiais de um processo. |
| `advbox_list_transactions` | Lista transações financeiras com filtros de data/tipo/status (via `query`). |
| `advbox_get_transaction` | Detalha uma transação por ID. Bulk support: accepts ids for batched execution. |
| `advbox_create_transaction` | Cria um lançamento financeiro (receita ou despesa). |
| `advbox_update_transaction` | Atualiza valor, vencimento ou status de pagamento de uma transação por ID. |

---

## Pricing

See [docs/precos.md](docs/precos.md) (PT-BR).

---

## License

MIT — see [LICENSE](LICENSE). The MCP server at `api.mcp.ai/p_advbox` is proprietary (hosted); this repo (manifests, docs, skills) is MIT.
