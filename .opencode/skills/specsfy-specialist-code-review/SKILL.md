---
name: specsfy-specialist-code-review
description: Revisar diffs, branches e PRs por contrato, correção, segurança, arquitetura, testes e risco operacional. Use quando o usuário pedir code review ou avaliação de mudanças; é somente leitura salvo pedido explícito para corrigir.
---

# Revisão de código

## Fluxo

1. Fixar base e escopo exatos do diff.
2. Ler spec, issue, critérios e instruções aplicáveis.
3. Mapear arquivos alterados para comportamentos e boundaries.
4. Avaliar correção, falhas, segurança, dados e operação.
5. Inspecionar testes pela evidência que fornecem.
6. Confirmar achados no código e reduzir falsos positivos.
7. Relatar por severidade com localização, impacto e correção provável.

## Padrões

- Priorizar bugs e riscos; não transformar gosto em bloqueio.
- Cada achado descreve condição, consequência e evidência.
- Considerar compatibilidade, concorrência, rollback e observabilidade.
- Verificar se testes falhariam sem a mudança correta.
- Distinguir escopo ausente de melhoria opcional.
- Não repetir lint que automação já cobre.
- Declarar ausência de achados sem alegar ausência de risco.

## Validação

- Revisar diff completo e chamadas/consumidores relevantes.
- Conferir achado contra estado observado e testes.
- Ordenar severidade pela probabilidade e impacto.
- Resumir cobertura e riscos residuais.

Leia [references/standards.md](references/standards.md) para lentes, severidade
e formato de achados.
