FROM php:8.0.11-fpm-alpine

WORKDIR /var/www

RUN apk -v --update add \
    zip \
    mc \
    unzip \
    git \
    curl \
    sqlite

RUN rm -rf /var/lib/apt/lists/*

RUN apk add zlib-dev libzip-dev freetype-dev libxml2-dev \
    && docker-php-ext-install pdo zip

RUN curl -sS https://getcomposer.org/installer | php -- \
        --filename=composer \
        --install-dir=/usr/local/bin && \
        echo "alias composer='composer'" >> /root/.bashrc && \
        composer

RUN addgroup -S www && adduser -S www -G www

RUN chown www:www -R /var/www/

USER www

ADD --chown=www:www . /var/www

RUN composer install \
    && cp .env.example .env  \
    && php artisan key:generate  \
    && php artisan migrate

CMD ["php", "artisan", "serve", "--host", "0.0.0.0"]
