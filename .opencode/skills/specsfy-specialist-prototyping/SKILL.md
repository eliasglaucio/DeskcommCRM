---
name: specsfy-specialist-prototyping
description: Construir protótipos descartáveis para responder uma pergunta técnica, de interação ou visual com custo e fidelidade mínimos. Use para spikes, provas de conceito e exploração de alternativas; não promover protótipo a produção sem reimplementação e validação.
---

# Prototipação

## Fluxo

1. Formular uma pergunta única e critério de decisão.
2. Definir o que precisa ser real e o que pode ser simulado.
3. Escolher fidelidade, tempo limite e local descartável.
4. Construir alternativas quando comparação for mais informativa.
5. Executar o cenário e coletar evidência observável.
6. Responder à pergunta e registrar limitações.
7. Descartar ou arquivar explicitamente sem criar dependência.

## Padrões

- Não confundir demo convincente com arquitetura válida.
- Manter dados, credenciais e integrações reais fora do protótipo salvo necessidade.
- Para UI, usar conteúdo realista e estados extremos.
- Para lógica, expor transições e invariantes em interface mínima.
- Não gastar tempo com abstração, cobertura ou acabamento fora da pergunta.
- Marcar código como descartável e impedir import acidental.
- Converter aprendizado em requisito, decisão ou teste no owner correto.

## Validação

- Critério definido antes e resultado reproduzível.
- Hipótese aceita, rejeitada ou ainda inconclusiva.
- Limitações e diferenças para produção explícitas.
- Nenhum artefato descartável conectado ao runtime final.

Leia [references/standards.md](references/standards.md) para níveis de fidelidade,
experimentos técnicos e protótipos de interface.
