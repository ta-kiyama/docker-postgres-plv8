FROM postgres:10-alpine

MAINTAINER ta.kiyama

ENV PLV8_VERSION=v2.3.7

RUN apk --update add --virtual build-dependencies \
    make \
    git \
    python \
    && mkdir -p /tmp/build \
    && wget -O /tmp/build/${PLV8_VERSION}.tar.gz "https://github.com/plv8/plv8/archive/$PLV8_VERSION.tar.gz" \
    && tar -xzf /tmp/build/${PLV8_VERSION}.tar.gz -C /tmp/build/ \
    && cd /tmp/build/plv8-${PLV8_VERSION#?} \
    && make static\
    && make install\
    && strip /usr/lib/postgresql/${PG_MAJOR}/lib/plv8.so \
    && apk del build-dependencies \
    && rm -rf /tmp/build /var/lib/apt/lists/*
