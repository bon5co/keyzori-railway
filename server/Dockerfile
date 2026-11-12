# Keyzori server for Railway.
#
# Keyzori (keyzori/Keyzori, MIT) is a self-hosted licensing server: licence keys with expiry dates, usage limits and
# device/IP caps, behind a REST API authenticated by a root master key. The upstream image is distroless and runs as
# uid 65532, so there is no shell to run an entrypoint in. It listens on KZ_API_PORT (default 6284), which Railway's
# edge does not know about. A public service must leave Railway's injected PORT alone and be reached on 8080, so this
# wrapper only bakes KZ_API_PORT=8080 (plus the log level and pool size, so none of them publish as blank required
# template variables). The application is otherwise untouched.
FROM ghcr.io/keyzori/server:2.0.3@sha256:64963856fb0e9a7020ae048a4c8acd56c9b1fd4ea4de5d06518eaf6745091c05

ENV KZ_API_HOST=0.0.0.0 \
    KZ_API_PORT=8080 \
    KZ_DATABASE_POOL_SIZE=10 \
    KZ_LOG_LEVEL=info

EXPOSE 8080
