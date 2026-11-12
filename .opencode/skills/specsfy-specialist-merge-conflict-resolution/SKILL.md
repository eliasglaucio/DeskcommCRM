---
name: specsfy-specialist-merge-conflict-resolution
description: Resolver conflitos Git de merge ou rebase pela intenção de cada lado, preservando comportamento e validando integração. Use quando já existe operação com arquivos unmerged; não abortar, reescrever histórico remoto ou escolher um lado inteiro sem autorização.
---

# Resolução de conflitos

## Fluxo

1. Inspecionar estado da operação, branches, commits e arquivos unmerged.
2. Para cada hunk, recuperar intenção e fonte de ambos os lados.
3. Classificar conflito como textual, estrutural, semântico ou gerado.
4. Construir resultado que preserve intenções compatíveis.
5. Quando incompatíveis, escolher pelo objetivo da integração e registrar trade-off.
6. Remover marcadores, validar sintaxe e executar checks focais.
7. Continuar a operação e executar regressão adequada.

## Padrões

- Nunca usar `ours`/`theirs` globalmente por conveniência.
- Não editar arquivo gerado sem atualizar sua fonte.
- Preservar mudanças de schema, testes e contratos relacionados.
- Reavaliar imports, renomes e chamadas mesmo sem marcador textual.
- Não introduzir comportamento novo além da resolução necessária.
- Não usar `--abort`, force push ou reset destrutivo sem pedido explícito.
- Conferir que nenhum arquivo unmerged permanece.

## Validação

- `git status` coerente e zero marcadores.
- Diff combinado revisado contra ambas as intenções.
- Typecheck/build/testes focais e regressão.
- Histórico e destino do push confirmados antes de publicar.

Leia [references/standards.md](references/standards.md) para comandos seguros,
tipos de conflito e checklist de integração.
