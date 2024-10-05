FROM php:8.2-apache

RUN apt-get update && apt-get install -y \
    libzip-dev \
    unzip \
    git \
    && docker-php-ext-install zip pdo_mysql

COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

RUN a2enmod rewrite

COPY ./apache/vhost.conf /etc/apache2/sites-enabled/000-default.conf

WORKDIR /var/www

EXPOSE 80
