FROM composer as builder

WORKDIR /app

COPY composer.json composer.lock /app/
RUN composer install  \
    --ignore-platform-reqs \
    --no-ansi \
    --no-autoloader \
    --no-dev \
    --no-interaction \
    --no-scripts

COPY . /app/
RUN composer dump-autoload --no-dev --optimize --classmap-authoritative


FROM php:7.4-apache

RUN pecl install xdebug-2.9.4 \
    && docker-php-ext-enable xdebug \
    && docker-php-ext-install pdo pdo_mysql

WORKDIR /app
COPY --from=builder /app /var/www/html/
COPY php.ini /usr/local/etc/php/php.ini