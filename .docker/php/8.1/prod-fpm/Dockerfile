FROM ghcr.io/josepostiga/infrastructure/php:8.1-base-fpm

RUN apk --no-cache add \
    cronie \
    freetype-dev \
    git \
    imagemagick \
    imagemagick-dev \
    imagemagick-libs \
    jpeg-dev \
    libjpeg-turbo-dev \
    libpng-dev \
    libpq-dev \
    libsodium-dev \
    libssl1.1 \
    libxml2-dev \
    libxrender-dev \
    libzip-dev \
    openssh-client \
    patch \
    unzip \
    vim \
    zlib-dev

RUN docker-php-ext-configure gd --with-freetype --with-jpeg

RUN docker-php-ext-install \
    exif \
    gd \
    pdo_pgsql \
    pgsql \
    soap \
    sockets \
    zip

RUN pecl install imagick-3.7.0 &&  \
    pecl install redis-5.3.7

RUN docker-php-ext-enable \
    imagick \
    redis \
    sockets

RUN touch /var/log/cron.log

COPY zz-docker.conf /usr/local/etc/php-fpm.d/zz-docker.conf

ENV COMPOSER_HOME /tmp/composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

LABEL version="8.1-prod-fpm"
