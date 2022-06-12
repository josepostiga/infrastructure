FROM ghcr.io/josepostiga/infrastructure/php:8.1-prod-fpm

RUN pecl install xdebug-3.1.4 && docker-php-ext-enable xdebug

ENV GIT_SSH_COMMAND "ssh -o StrictHostKeyChecking=no"

LABEL version="8.1-dev-fpm"
