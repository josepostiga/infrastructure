FROM php:8.1.6-fpm-alpine

# Install language pack
RUN apk --no-cache add ca-certificates wget && \
    wget https://github.com/Lauri-Nomme/alpine-glibc-xb/releases/download/aarch64-2.33-r0/glibc-2.33-r0.apk && \
    wget https://github.com/Lauri-Nomme/alpine-glibc-xb/releases/download/aarch64-2.33-r0/glibc-bin-2.33-r0.apk && \
    wget https://github.com/Lauri-Nomme/alpine-glibc-xb/releases/download/aarch64-2.33-r0/glibc-i18n-2.33-r0.apk && \
    apk --no-cache --allow-untrusted add glibc-bin-2.33-r0.apk glibc-i18n-2.33-r0.apk glibc-2.33-r0.apk

# Iterate through all locale and install it
# Note that locale -a is not available in alpine linux, use `/usr/glibc-compat/bin/locale -a` instead
COPY locale.md /locale.md
RUN cat ./locale.md | xargs -i /usr/glibc-compat/bin/localedef -i {} -f UTF-8 {}.UTF-8

RUN apk --no-cache add \
    autoconf \
    gcc \
    make \
    musl-dev

RUN docker-php-ext-install \
    bcmath \
    pcntl

RUN pecl upgrade timezonedb-2021.5

RUN docker-php-ext-enable \
    opcache \
    timezonedb

LABEL package="PHP"
LABEL version="8.1-base-fpm"
LABEL org.opencontainers.image.source="https://github.com/josepostiga/infrastructure"
