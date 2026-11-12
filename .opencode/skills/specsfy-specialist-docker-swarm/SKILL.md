---
name: specsfy-specialist-docker-swarm
description: Projetar, implantar e operar stacks Docker Swarm com serviços, overlay networks, secrets, configs, placement, rollout, rollback e recuperação do quorum. Use para swarm init, docker stack, services, managers, workers e arquivos de stack; não use Compose local como evidência de comportamento do Swarm.
---

# Docker Swarm

## Fluxo

1. Mapear managers, workers, zonas, labels, quorum e dependências externas.
2. Validar imagens publicadas e compatibilidade do arquivo com `docker stack deploy`.
3. Definir services, redes, ports, volumes, configs e secrets por owner.
4. Configurar replicas, placement, resources, health e restart policy.
5. Projetar `update_config`, `rollback_config` e compatibilidade durante rollout.
6. Validar a stack em swarm representativo e observar convergência.
7. Documentar deploy, rollback, rotação, backup do estado e recuperação.

## Padrões

- Manter número ímpar de managers e proteger quorum.
- Publicar imagens imutáveis acessíveis por todos os nodes.
- Usar secrets/configs versionados por nome; nunca embutir segredo no YAML.
- Separar ingress, redes internas e tráfego de dados.
- Definir reservations e limits; não depender de capacidade implícita.
- Aplicar constraints somente com labels administradas.
- Não assumir que toda opção moderna do Compose é aceita por stack deploy.

## Validação

- Executar `docker stack config` ou validação equivalente antes do deploy.
- Observar `service ps`, replicas, health, logs e eventos durante rollout.
- Simular falha de worker e, em ambiente autorizado, perda de manager.
- Provar rollback de aplicação e compatibilidade de migrations.

Leia [references/standards.md](references/standards.md) para topologia, serviços,
secrets, redes, rollout e disaster recovery.
