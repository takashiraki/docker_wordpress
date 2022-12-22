FROM php:fpm

COPY php.ini /usr/local/etc/php/
COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN apt-get update \
  && apt-get install -y default-mysql-client \
  && docker-php-ext-install pdo_mysql

RUN apt-get update
RUN apt-get -y install libzip-dev
RUN docker-php-ext-install zip

WORKDIR /var/www/html