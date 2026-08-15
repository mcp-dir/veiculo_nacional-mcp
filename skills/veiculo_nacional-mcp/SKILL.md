---
name: veiculo_nacional-mcp
description: Skill da REST API do Consulta Veicular Nacional na MCP.AI: 1 endpoint em /api/veiculo_nacional. Dados cadastrais de um veículo a partir da placa em base nacional: marca, modelo, ano de fabricação, cor e demais características. Hospedado pela plataforma, sem credenciais, pague por consulta com crédito pré-pago. Autentique com workspace API key (sk_live) gerada em app.mcp.ai/settings/api-keys. Use quando o usuário pedir algo coberto pelos endpoints.
---

# Consulta Veicular Nacional — REST API skill

Você tem acesso à **Consulta Veicular Nacional** REST API na MCP.AI.

> Dados cadastrais de um veículo a partir da placa em base nacional: marca, modelo, ano de fabricação, cor e demais características. Hospedado pela plataforma, sem credenciais, pague por consulta com crédito pré-pago.

## Base URL

```
https://api.mcp.ai/api/veiculo_nacional
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
curl -X POST https://api.mcp.ai/api/veiculo_nacional/consultar \
  -H "Authorization: Bearer sk_live_..." \
  -H "Content-Type: application/json" \
  -d '{"Placa":"..."}'
```

## Reportar problemas

Se um endpoint retornar erro, vazio ou dado inesperado, reporte (não desista calado): **POST /api/veiculo_nacional/report** com `{ "message": "...", "context"?: "...", "conversation"?: [...] }`. Isso notifica o time da MCP.AI.

## Endpoints (1)

#### `veiculo_nacional_consultar`

Dados cadastrais de um veículo a partir da placa em base nacional: marca, modelo, ano de fabricação, cor e demais características. _(POST /api/veiculo_nacional/consultar)_

| Parâmetro | Tipo | Obrigatório | Descrição |
|---|---|---|---|
| `Placa` | string | Sim | Parâmetro de consulta "Placa". |
| `completo` | boolean | Não | Opcional. Por padrão (false) listas longas vêm resumidas aos primeiros itens, com a contagem total preservada. Use true para a resposta COMPLETA na mesma consulta. |

---

Este MCP também funciona via **conexão MCP** (Claude / Cursor) em `https://api.mcp.ai/p_veiculo_nacional` — veja o [README](../../README.md). A skill acima é pra consumir a **REST API** direto (agente próprio / código).
