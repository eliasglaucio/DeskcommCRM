# Padrões e referências de diagnóstico

## Técnicas

- Bisseção: localizar mudança mínima que introduziu a falha.
- Differential debugging: comparar input/ambiente bom e ruim.
- Delta debugging: reduzir caso preservando falha.
- Tracing: seguir causalidade entre boundaries.
- Profiling: localizar consumo antes de otimizar.
- Fault injection: validar hipótese de dependência somente em ambiente seguro.

## Fontes

- Git bisect: https://git-scm.com/docs/git-bisect
- Chrome DevTools: https://developer.chrome.com/docs/devtools/
- Python debugging: https://docs.python.org/3/library/pdb.html
- PostgreSQL monitoring: https://www.postgresql.org/docs/current/monitoring.html
- OpenTelemetry traces: https://opentelemetry.io/docs/concepts/signals/traces/
