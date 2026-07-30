FROM govpf/postgres:16

LABEL maintainer="PostGIS Project - https://postgis.net" \
      org.opencontainers.image.description="PostGIS spatial database extension with PostgreSQL 17" \
      org.opencontainers.image.source="https://github.com/postgis/docker-postgis"

ENV POSTGIS_MAJOR=3

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        ca-certificates \
        postgresql-$PG_MAJOR-postgis-$POSTGIS_MAJOR \
        postgresql-$PG_MAJOR-postgis-$POSTGIS_MAJOR-scripts \
    && rm -rf /var/lib/apt/lists/*

RUN mkdir -p /docker-entrypoint-initdb.d

COPY initdb-postgis.sh /docker-entrypoint-initdb.d/10_postgis.sh
COPY update-postgis.sh /usr/local/bin