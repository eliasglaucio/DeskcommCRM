# Padrões e referências para APIs web

## Contratos

- IDs opacos e estáveis.
- Datas ISO 8601 com timezone definido.
- Dinheiro com moeda e precisão explícitas.
- Erros com tipo, título, status, detalhe seguro e correlação.
- Paginação com links/cursor e ordenação determinística.

## Fontes primárias

- HTTP Semantics: https://www.rfc-editor.org/rfc/rfc9110
- Problem Details: https://www.rfc-editor.org/rfc/rfc9457
- Idempotency-Key: https://datatracker.ietf.org/doc/html/draft-ietf-httpapi-idempotency-key-header
- OpenAPI 3.1: https://spec.openapis.org/oas/v3.1.0
- JSON Schema: https://json-schema.org/specification
- OAuth 2.0 Security BCP: https://www.rfc-editor.org/rfc/rfc9700
- Webhook Standard: https://www.standardwebhooks.com/
