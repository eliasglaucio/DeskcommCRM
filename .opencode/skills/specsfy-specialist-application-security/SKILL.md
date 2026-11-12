---
name: specsfy-specialist-application-security
description: Modelar ameaças e revisar segurança de aplicações, APIs, autenticação, autorização, dados, dependências, secrets e infraestrutura. Use para mudanças com trust boundaries, identidade, entrada externa, dados sensíveis ou revisão de segurança; não declare segurança sem evidência.
---

# Segurança de aplicações

## Fluxo

1. Mapear ativos, atores, trust boundaries, entradas e efeitos.
2. Definir ameaças plausíveis e impacto antes dos controles.
3. Verificar autenticação, autorização por objeto e separação de tenants.
4. Validar entrada, normalizar saída e proteger operações mutáveis.
5. Revisar secrets, criptografia, sessões, dependências e configuração.
6. Materializar testes positivos e negativos nos boundaries críticos.
7. Registrar risco residual, owner, observabilidade e resposta.

## Padrões

- Negar por padrão e conceder menor privilégio.
- Autorizar no servidor em toda operação e objeto.
- Tratar upload, URL, template, query e deserialize como entradas hostis.
- Não criar criptografia própria nem logar segredo, token ou dado sensível.
- Rotacionar credenciais e preferir identidade temporária.
- Mitigar abuso com limites por ator e recurso, não apenas IP.
- Corrigir causa e adicionar regressão sem divulgar exploração desnecessária.

## Validação

- Casos sem autenticação, identidade errada, tenant errado e replay.
- Análise de dependências e secrets com ferramentas do projeto.
- Configuração segura de produção, headers, cookies e CORS.
- Evidência de controle e risco residual, sem linguagem absoluta.

Leia [references/standards.md](references/standards.md) para threat modeling,
ASVS, APIs, supply chain e resposta.
