FROM php:7.4-apache
WORKDIR /var/www/html
# Extensions
RUN pecl install xdebug-2.9.4 \
   && docker-php-ext-enable xdebug \
   && docker-php-ext-install pdo pdo_mysql

# Config
COPY php.ini /usr/local/etc/php/php.ini