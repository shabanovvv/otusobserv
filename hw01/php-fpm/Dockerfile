FROM php:8.2-fpm

RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    libpng-dev \
    libonig-dev \
    libssl-dev \
    libxml2 \
    libpq-dev \
    && rm -rf /var/lib/apt/lists/* \
    && docker-php-ext-install -j$(nproc) mysqli pdo_mysql zip gd mbstring exif pcntl bcmath pgsql pdo_pgsql

RUN pecl install xdebug-3.3.0 \
    && docker-php-ext-enable xdebug

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

WORKDIR /var/www/html

COPY php-fpm.conf /usr/local/etc/php-fpm.d/zzz-custom.conf
COPY xdebug.ini /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

CMD ["php-fpm"]
