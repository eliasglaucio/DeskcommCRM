# Padrões e referências para conflitos Git

## Diagnóstico

- `git status`: operação e caminhos unmerged.
- `git ls-files -u`: stages base, ours e theirs.
- `git log --merge`: commits relevantes.
- `git diff --cc`: resultado combinado.
- `git show :1:path`, `:2:path`, `:3:path`: versões do hunk.

## Conflitos sem marcador

- Renome com import antigo.
- Mudanças concorrentes em migration/schema.
- Assinatura alterada e novo caller.
- Lockfile resolvido sem manifests coerentes.
- Testes de ambos os lados que agora interagem.

## Fontes oficiais

- git-merge: https://git-scm.com/docs/git-merge
- git-rebase: https://git-scm.com/docs/git-rebase
- git-rerere: https://git-scm.com/docs/git-rerere
- Pro Git branching: https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging
