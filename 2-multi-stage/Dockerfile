FROM composer as backend

WORKDIR /app

COPY composer.json composer.lock /app/
RUN composer install \
	-ingore-platform-eqs \
	-no-ansi \
	-no-autoloader \
	-no-dev \
	-no-interaction \
	-no-script

COPY . /app/
RUN composer dump-autoload --no-dev -optimize --classmap-authoritative


FROM php:7.4-apache

RUN pecl install xdebug-2.9.4
RUN docker-php-ext-enable xdebug
RUN docker-php-ext-install pdo pdo_mysql

WORKDIR /app
COPY --from=backend /app /var/www/html/
COPY php.ini /usr/local/etc/php/php.ini