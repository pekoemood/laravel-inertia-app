FROM php:8.4-fpm

ENV COMPOSER_ALLOW_SUPERUSER=1 \
  COMPOSER_HOME=/composer

COPY --from=composer:2.2 /usr/bin/composer /usr/bin/composer

RUN apt-get update && \
  apt-get -y install --no-install-recommends git vim unzip libpq-dev libzip-dev libicu-dev libonig-dev && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  docker-php-ext-install pdo_pgsql zip intl bcmath

COPY ./php.ini /usr/local/etc/php/php.ini

EXPOSE 9000

RUN 

WORKDIR /data

CMD [ "php-fpm" ]