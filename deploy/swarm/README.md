# CRM no Docker Swarm

Stack equivalente ao `docker-compose.prod.yml`, para um Swarm com Traefik e o
Supabase self-hosted na mesma rede (`MV8Net`).

| Serviço | Imagem | Rede |
|---|---|---|
| `crm-app` | `ghcr.io/eliasglaucio/deskcommcrm` | `MV8Net` + `interna` |
| `crm-worker` | `ghcr.io/eliasglaucio/deskcomm-worker` | `MV8Net` + `interna` |
| `crm-scheduler` | `ghcr.io/eliasglaucio/deskcomm-scheduler` | `interna` |
| `crm-waha` | `devlikeapro/waha:latest-2026.7.2` | `interna` |
| `crm-redis`, `crm-srh` | `redis:7-alpine`, `hiett/serverless-redis-http` | `interna` |
| opcionais (desligados) | `crm-wacalls`, `crm-asterisk`, `crm-voice-agent` | `interna` |

**Por que duas redes.** A `MV8Net` é compartilhada com o Supabase e outras
stacks. Só o app (Traefik e Kong) e o worker (Postgres) precisam dela, e com
nomes únicos `crm-*`. Redis, WAHA e SRH ficam na rede `interna`, privada da
stack, sem risco de um `redis` de outra stack responder no lugar do seu. O
scheduler tem `http://app:3000` fixo, e o Asterisk tem `voice-agent:9092`
fixo; esses nomes existem como alias só na rede `interna`.

## Antes do primeiro deploy

1. **As imagens precisam existir.** Dê push no `main` do fork e espere o
   workflow *Publicar imagem Docker (GHCR)* terminar (4 imagens x 2
   arquiteturas). Sai `latest`.
2. **Visibilidade dos pacotes.** Se nascerem privados, ou torne-os públicos
   (GitHub › Packages › cada pacote › Settings), ou faça no manager
   `docker login ghcr.io -u eliasglaucio` com um token `read:packages` e use
   `--with-registry-auth` (já está no comando abaixo).
3. **Volumes** (a stack os trata como externos, sobrevivem a `docker stack rm`):

   ```bash
   docker volume create waha_data
   docker volume create waha_media
   docker volume create wacalls_data
   docker volume create asterisk_data
   docker volume create asterisk_logs
   ```
4. **Variáveis**: `cp crm.env.example crm.env && chmod 600 crm.env` e preencha.
   Gere os segredos com `openssl rand -hex 32`.
5. **Banco**: o schema do Supabase tem de estar em dia com a imagem. Reaplique
   `supabase/baseline.sql` quando subir uma versão com migrations novas (o
   deploy da stack **não** faz isso).
6. O Auth do Supabase precisa aceitar o domínio (`GOTRUE_URI_ALLOW_LIST`):
   `https://crm.cppem.com.br/**`.

## Deploy

```bash
cd deploy/swarm
set -a; . ./crm.env; set +a
docker stack deploy --with-registry-auth -c crm.stack.yml crm
docker stack services crm
```

## Atualizar para uma versão nova (`latest`)

O Swarm resolve a tag para um digest no momento do deploy. Para pegar o `latest`
novo, repita o deploy, ou force um serviço:

```bash
docker service update --force --with-registry-auth --image ghcr.io/eliasglaucio/deskcommcrm:latest crm_crm-app
docker service update --force --with-registry-auth --image ghcr.io/eliasglaucio/deskcomm-worker:latest crm_crm-worker
docker service update --force --with-registry-auth --image ghcr.io/eliasglaucio/deskcomm-scheduler:latest crm_crm-scheduler
```

Atualize **app, worker e scheduler juntos**: eles saem do mesmo commit.
Para usar `stable` depois: crie uma tag `vX.Y.Z` no fork (o workflow move o
canal) e troque `CRM_TAG=stable` no `crm.env`.

## Cuidados

- **Um worker só** (`replicas: 1`, `update_config: stop-first`). Dois workers ao
  mesmo tempo disputam a fila do `event_log`.
- **WAHA é um só** e dono do volume de sessões (`waha_data`). Perder o volume
  obriga a ler o QR de novo.
- O painel do WAHA está desligado (`WAHA_DASHBOARD_ENABLED=false`) e nenhuma
  porta dele é publicada: ele só é alcançável pelo app.
- `crm-asterisk` **não foi testado no Swarm**: o `ingress` reescreve o IP de
  origem de SIP/RTP. Valide com uma ligação real antes de depender dele.
- Logs: `docker service logs -f crm_crm-worker` (idem `crm_crm-app`, etc.).
- Segredos nunca vão para o git: `crm.env` está no `.gitignore` desta pasta.
