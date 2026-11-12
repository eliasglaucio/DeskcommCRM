---
name: specsfy-specialist-web-api-design
description: Projetar e revisar APIs HTTP com recursos, métodos, status, erros, paginação, idempotência, concorrência, autenticação e evolução compatível. Use para REST, JSON APIs, webhooks ou OpenAPI; não aplicar estilo REST a RPC sem avaliar o contrato real.
---

# Design de APIs web

## Fluxo

1. Identificar consumidores, casos de uso, latência, volume e trust boundaries.
2. Modelar recursos, identidade, relações e invariantes.
3. Definir operações, schemas, erros e semântica de retry.
4. Projetar autorização, idempotência e concorrência.
5. Especificar paginação, filtros, ordenação e limites.
6. Materializar contrato e testes de compatibilidade.
7. Definir observabilidade, depreciação e evolução.

## Padrões

- Usar semântica HTTP coerente e status específicos.
- Manter formato de erro estável, acionável e sem vazamento.
- Usar cursor quando dados mudam durante paginação extensa.
- Tornar criação/retry seguros com chave de idempotência quando necessário.
- Proteger webhooks com assinatura, timestamp, replay defense e reentrega.
- Evitar breaking changes silenciosas e campos com semântica ambígua.
- Não expor modelo de persistência como contrato por conveniência.

## Validação

- Contract tests de request, response e erro.
- Autorização por recurso e tenant.
- Retry, duplicação, timeout, concorrência e paginação mutável.
- Lint da descrição OpenAPI e exemplos executáveis quando disponível.

Leia [references/standards.md](references/standards.md) para HTTP, erros,
OpenAPI, webhooks e compatibilidade.
