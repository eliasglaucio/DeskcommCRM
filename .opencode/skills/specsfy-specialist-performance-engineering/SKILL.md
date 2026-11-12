---
name: specsfy-specialist-performance-engineering
description: Diagnosticar e melhorar performance com orçamento, medição, profiling, testes de carga, Web Vitals e regressão. Use para lentidão, throughput, uso de recursos, bundle ou capacidade; não otimizar sem baseline e hipótese.
---

# Engenharia de performance

## Fluxo

1. Definir jornada, métrica, percentil, carga e orçamento.
2. Reproduzir com ambiente e dados representativos.
3. Medir baseline e decompor tempo por boundary.
4. Formular uma hipótese e usar profiler/trace adequado.
5. Alterar um fator relevante e medir novamente.
6. Testar correção, capacidade e degradação.
7. Criar guardrail contra regressão.

## Padrões

- Usar percentis e distribuição, não apenas média.
- Separar latência cliente, rede, aplicação, banco e dependências.
- Medir cold/warm cache e condições concorrentes.
- Não adicionar cache antes de provar custo e estratégia de invalidação.
- Preservar correção sob carga, timeout e retry.
- Controlar observer effect e aquecimento.
- Definir capacidade e headroom com cenário de pico.

## Validação

- Benchmark repetível com baseline arquivado.
- Profiling de CPU, memória, I/O ou queries conforme evidência.
- Teste de carga com critérios e limites seguros.
- Regressão automática proporcional à estabilidade da métrica.

Leia [references/standards.md](references/standards.md) para Web Vitals,
benchmark, carga, profiling e budgets.
