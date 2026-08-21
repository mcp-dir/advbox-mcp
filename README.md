# AdvBox

### AdvBox para Claude, ChatGPT e agentes de IA

Wrapper da API oficial do AdvBox (software jurídico): processos (e histórico, movimentações, publicações), clientes/contatos, tarefas/anotações e financeiro (transações). Leitura + criação e atualização de processos e transações. Autenticação por token de API do escritório.

- 📊 **20 ferramentas**
- ✏️ **Leitura e escrita**
- 💬 **Funciona com qualquer cliente MCP**: Claude Desktop, Cursor, VS Code, Cline, Continue
- 🔑 **Login via magic-link (sem senha)**

[English version](README.en.md) · [Documentação completa](docs/) · [Skill pra agentes](skills/)

---

## Instalar em 1 clique

### Claude (Web e Desktop)

A Anthropic unificou a instalação de MCPs em `claude.ai/customize/connectors`. **O mesmo link serve pra Claude Web e Claude Desktop** (basta estar logado):

[➕ Abrir no Claude e conectar](https://claude.ai/new?modal=add-custom-connector#settings/customize-connectors)

**Manual** (se o deeplink não abrir): [claude.ai/customize/connectors](https://claude.ai/customize/connectors?surface=cowork) → **+** → **Adicionar conector personalizado** → cole **Nome** `AdvBox` e **URL** `https://api.mcp.ai/p_advbox`.

### Cursor

[➕ Instalar AdvBox no Cursor](cursor://anysphere.cursor-deeplink/mcp/install?name=advbox&config=eyJ1cmwiOiJodHRwczovL2FwaS5tY3AuYWkvcF9hZHZib3gifQ==)

### VS Code (Copilot Chat)

[➕ Instalar AdvBox no VS Code](vscode:mcp/install?name=advbox&config=%7B%22type%22%3A%22http%22%2C%22url%22%3A%22https%3A%2F%2Fapi.mcp.ai%2Fp_advbox%22%7D)

### ChatGPT, Manus, OpenClaw e mais 40+ clientes

Funciona em qualquer cliente MCP que suporte **MCP over HTTP**. A URL do servidor é sempre:

```
https://api.mcp.ai/p_advbox
```

Detalhes por cliente: [INSTALL.md](INSTALL.md).

---

## Exemplos de uso

```
Busque o processo número X no AdvBox e mostre as últimas movimentações
Liste as transações financeiras vencidas este mês
Crie uma movimentação manual no processo Y registrando o andamento
```

---

## 20 ferramentas disponíveis

| Tool | Descrição |
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

Detalhe de cada tool: [docs/ferramentas.md](docs/ferramentas.md)

---

## Preços

Planos a partir do tier grátis. Veja [docs/precos.md](docs/precos.md).

---

## Privacidade & LGPD

- **Sub-processadores**: o LLM host que você escolher (Claude, ChatGPT, Cursor, agente próprio). Lista completa em [docs/privacidade-lgpd.md](docs/privacidade-lgpd.md).
- Os dados retornados pelas tools são enviados ao **LLM host que você escolher**, sub-processador fora do nosso controle. Recomendamos planos com opt-out de treinamento.

---

## Perguntas frequentes

**O servidor é open source?**
O servidor é proprietário (hosted). Este repositório é o wrapper público com manifestos, docs e skills — tudo MIT.

**Posso usar com agente próprio (não Claude/Cursor)?**
Sim — qualquer cliente que suporte MCP over HTTP. URL: `https://api.mcp.ai/p_advbox`.


---

## Suporte

- 📧 [advbox@mcp.ai](mailto:advbox@mcp.ai)
- 🐛 [GitHub Issues](https://github.com/mcp-dir/advbox-mcp/issues)
- 📄 [docs/](docs/)

---

## Licença

MIT — veja [LICENSE](LICENSE). O servidor MCP em `api.mcp.ai/p_advbox` é proprietário (hosted); este repositório (manifestos, docs, skills) é MIT.
