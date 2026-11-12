# PostgreSQL 18 for Keyzori on Railway.
#
# Keyzori's server connects as a restricted role (keyzori_server) that owns the public and drizzle schemas, never as
# the database administrator. Upstream creates that role with an init script mounted into docker-entrypoint-initdb.d;
# a Railway service cannot mount a file, so this wrapper copies the same script into the image. The script runs once,
# on an empty data directory. The volume is mounted at the PARENT, /var/lib/postgresql, so PGDATA keeps its default
# versioned subdirectory and lost+found never lands inside it.
FROM postgres:18.0@sha256:41fc5342eefba6cc2ccda736aaf034bbbb7c3df0fdb81516eba1ba33f360162c

ENV POSTGRES_DB=keyzori \
    POSTGRES_USER=keyzori

COPY --chmod=0755 01-roles.sh /docker-entrypoint-initdb.d/01-roles.sh

EXPOSE 5432
