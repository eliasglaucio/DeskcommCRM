# Padrões de revisão de código

## Lentes

- Contrato: requisitos e comportamento.
- Correção: estados, erros, limites e concorrência.
- Segurança: trust boundaries, identidade e dados.
- Design: ownership, coupling e dependências.
- Operação: migrations, config, deploy, telemetry e rollback.
- Evidência: testes, tipos e checks.

## Severidade

- Crítica: exploração, perda de dados ou indisponibilidade ampla provável.
- Alta: comportamento incorreto importante sem mitigação.
- Média: falha limitada ou dívida com impacto concreto.
- Baixa: robustez ou manutenção com benefício demonstrável.

## Referências

- Google Engineering Practices: https://google.github.io/eng-practices/review/
- OWASP Code Review Guide: https://owasp.org/www-project-code-review-guide/
- Conventional Comments: https://conventionalcomments.org/
