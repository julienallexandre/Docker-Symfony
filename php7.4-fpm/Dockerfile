FROM php:7.4-fpm

RUN apt-get update && \
    apt-get install -y \
        wget \
        git \
        libicu-dev \
        unzip \
        zip

RUN docker-php-ext-install \
        intl \
        opcache && \
    docker-php-ext-enable \
        intl \
        opcache

RUN echo "short_open_tag = Off" > $PHP_INI_DIR/php.ini

COPY --from=composer /usr/bin/composer /usr/bin/composer

RUN wget https://get.symfony.com/cli/installer -O - | bash && \
    mv /root/.symfony/bin/symfony /usr/local/bin/symfony
