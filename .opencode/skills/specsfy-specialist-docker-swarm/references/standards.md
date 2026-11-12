# Padrões e referências Docker Swarm

## Topologia

- Managers mantêm Raft; prefira 3 ou 5 e monitore disponibilidade do quorum.
- Workers executam workloads; use labels para capacidades reais.
- Faça backup protegido do estado de manager e preserve unlock keys quando usadas.

## Deploy seguro

- Defina paralelismo, delay, failure action, monitor e ordem start-first/stop-first.
- Garanta compatibilidade entre versão antiga e nova durante todo o rollout.
- Rotacione secrets criando nova versão, anexando-a ao serviço e removendo a anterior.
- Use volumes distribuídos ou placement fixo apenas com recuperação documentada.

## Fontes oficiais

- Swarm mode: https://docs.docker.com/engine/swarm/
- Conceitos: https://docs.docker.com/engine/swarm/key-concepts/
- Serviços: https://docs.docker.com/engine/swarm/services/
- Stack deploy: https://docs.docker.com/engine/swarm/stack-deploy/
- Secrets: https://docs.docker.com/engine/swarm/secrets/
- PKI: https://docs.docker.com/engine/swarm/how-swarm-mode-works/pki/
- Recuperação: https://docs.docker.com/engine/swarm/admin_guide/
