---
name: specsfy-specialist-technical-research
description: Investigar questões técnicas em fontes primárias, código, padrões e experimentos, produzindo síntese rastreável. Use quando decisões dependem de APIs atuais, comparação de tecnologias ou fatos incertos; salve pesquisa somente no local autorizado pela spec do projeto consumidor.
---

# Pesquisa técnica

## Fluxo

1. Formular pergunta, decisão suportada, escopo e recência necessária.
2. Definir evidência capaz de confirmar ou refutar alternativas.
3. Priorizar especificações, documentação oficial, source e releases.
4. Verificar versão, data e aplicabilidade ao ambiente observado.
5. Triangular afirmações críticas e executar experimento quando necessário.
6. Separar fatos, inferências, riscos e lacunas.
7. Sintetizar com links diretos e implicação para a decisão.

## Padrões

- Não usar snippet ou blog como autoridade de API quando existe fonte primária.
- Citar a página específica próxima da afirmação.
- Evitar transcrição extensa; sintetizar e preservar contexto.
- Registrar versão e data quando o comportamento pode mudar.
- Declarar conflito entre fontes sem escolher silenciosamente.
- Não criar `research.md` paralelo; seguir a fonte autorizada do projeto.
- Tratar benchmark de fornecedor como evidência interessada.

## Validação

- Cada conclusão importante possui evidência direta.
- Fontes correspondem à versão e ao runtime do projeto.
- Experimentos são reproduzíveis e não alteram produção.
- Lacunas e incerteza residual estão explícitas.

Leia [references/standards.md](references/standards.md) para hierarquia de
fontes, avaliação e formato de síntese.
