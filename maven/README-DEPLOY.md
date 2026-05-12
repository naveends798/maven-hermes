# Maven fork of Hermes Agent

This is the Maven platform's fork of [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent).
It is **not** intended for direct local use — for that, use the upstream repo.

## What's different from upstream

1. **Bridge networking** instead of `network_mode: host` in `docker-compose.yml`,
   so multiple Hermes containers can coexist on one VPS.
2. **Named volume `hermes_data`** instead of `~/.hermes` bind mount, so Coolify
   (or any container orchestrator) manages volume lifecycle per customer.
3. **`container_name:` removed** so deploys can run side-by-side without name collisions.
4. **Dashboard binds `0.0.0.0`** — REQUIRES Traefik basic-auth (or another
   authenticated reverse proxy) in front. **Never deploy this fork without
   the auth middleware.** See Maven's `infra/coolify-bootstrap.md` Step 7.
5. **API server enabled by default** with `API_SERVER_KEY` required.

## Upgrade workflow

Maven syncs this fork with upstream periodically. See `infra/upgrading-hermes.md`
in the Maven repo for the merge dance and rollout procedure.

## Attribution

All upstream Hermes code remains MIT-licensed under NousResearch.
Maven's customisations are also MIT.
