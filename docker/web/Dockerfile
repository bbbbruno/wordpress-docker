FROM php:7.4-apache

COPY php.ini /usr/local/etc/php

RUN apt-get update \
  && apt-get install -y --no-install-recommends \
  libonig-dev \
  libfreetype6-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng-dev \
  libzip-dev \
  && docker-php-ext-configure gd \
  && docker-php-ext-install -j$(nproc) gd exif

RUN apt-get update \
  && apt-get install -y libonig-dev \
  && docker-php-ext-install mysqli pdo_mysql zip \
  && a2enmod rewrite

WORKDIR /var/www/html

EXPOSE 80
