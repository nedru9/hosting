FROM php:8.2-fpm

RUN echo 'deb http://mirror.yandex.ru/debian/ bookworm main contrib non-free non-free-firmware deb-src http://mirror.yandex.ru/debian/ bookworm main contrib non-free non-free-firmware deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware deb-src http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware deb http://mirror.yandex.ru/debian/ bookworm-updates main contrib non-free non-free-firmware deb-src http://mirror.yandex.ru/debian/ bookworm-updates main contrib non-free non-free-firmware' > /etc/apt/sources.list


RUN apt-get update && apt-get install -y \
      apt-utils \
      libpq-dev \
      libpng-dev \
      libzip-dev \
      zip unzip \
      git && \
      docker-php-ext-install pdo_mysql && \
      docker-php-ext-install bcmath && \
      docker-php-ext-install gd && \
      docker-php-ext-install zip && \
      apt-get clean && \
      rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

COPY ./_docker/app/php.ini /usr/local/etc/php/conf.d/php.ini


ENV COMPOSER_ALLOW_SUPERUSER=1
RUN curl -sS https://getcomposer.org/installer | php -- \
    --filename=composer \
    --install-dir=/usr/local/bin

WORKDIR /var/www
