# Keyzori on Railway

Wrapper images for the Railway template of [Keyzori](https://github.com/keyzori/Keyzori), a self-hosted licensing server.

- `server/` bakes `KZ_API_PORT=8080` onto the upstream distroless image `ghcr.io/keyzori/server:2.0.3`, so a public Railway domain reaches it. Built as `ghcr.io/bon5co/keyzori-railway`.
- `postgres/` is `postgres:18.0` with Keyzori's role bootstrap script (`01-roles.sh`, copied unmodified from upstream `deploy/postgres/`) baked into `docker-entrypoint-initdb.d`. Built as `ghcr.io/bon5co/keyzori-postgres-railway`.

`make-spec.py` writes `scripts/specs/keyzori.json`; run it as `uv run --no-project keyzori/make-spec.py <server digest> <postgres digest>`.
