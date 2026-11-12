---
name: specsfy-specialist-web-accessibility
description: Implementar e auditar acessibilidade web com WCAG, HTML semântico, teclado, foco, nomes acessíveis, contraste, zoom e tecnologias assistivas. Use para componentes, páginas, formulários, dashboards e revisões de conformidade; automação não substitui teste manual.
---

# Acessibilidade web

## Fluxo

1. Definir público, nível WCAG requerido e fluxos críticos.
2. Usar elemento HTML nativo antes de ARIA ou widget customizado.
3. Verificar estrutura, landmarks, headings, labels e nomes acessíveis.
4. Implementar teclado, ordem de foco, foco visível e gestão após mudanças.
5. Validar cor, contraste, zoom, reflow, movimento e mídia.
6. Executar análise automática e inspeção manual.
7. Testar fluxos críticos com leitor de tela e documentar limitações.

## Padrões

- Nenhuma ação depende apenas de hover, cor, gesto ou pointer preciso.
- Todo controle tem nome, papel, valor e estado corretos.
- Modal prende foco, fecha por mecanismo previsível e devolve foco.
- Erros são associados aos campos e resumidos quando necessário.
- Updates assíncronos anunciam somente informação relevante.
- Charts oferecem texto/tabela equivalente e não dependem de cor.
- ARIA nunca corrige semântica nativa incorreta.

## Validação

- Teclado completo sem armadilha.
- Zoom 200%, reflow 400%, contraste e forced colors quando aplicável.
- Axe/linter mais inspeção do accessibility tree.
- Leitor de tela nos fluxos de maior risco.

Leia [references/standards.md](references/standards.md) para critérios WCAG,
padrões APG, formulários, dashboards e testes.
