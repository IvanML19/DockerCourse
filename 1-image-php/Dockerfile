FROM php:7.4-apache

LABEL mantainer="ivanmartinlopez19@hotmail.com"
LABEL application="learning docker"

RUN pecl install xdebug-2.9.4
RUN docker-php-ext-enable xdebug
RUN docker-php-ext-install pdo pdo_mysql

ENV DISPLAY_ERRORS="On"

COPY php.ini /usr/local/etc/php/php.ini
COPY index.php /var/www/html/
