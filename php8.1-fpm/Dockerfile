FROM php:8.1-fpm

RUN apt-get update && \
    apt-get install -y \
        wget \
        git \
        libicu-dev \
        unzip

RUN docker-php-ext-install \
        intl \
        opcache && \
    docker-php-ext-enable \
        intl \
        opcache

RUN echo "short_open_tag = Off" > $PHP_INI_DIR/php.ini

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN echo 'deb [trusted=yes] https://repo.symfony.com/apt/ /' | tee /etc/apt/sources.list.d/symfony-cli.list && \
    apt update && \
    apt install symfony-cli
