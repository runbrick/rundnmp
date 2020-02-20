FROM php:7.3-fpm-alpine

RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.aliyun.com/g' /etc/apk/repositories

RUN apk update \
 && apk add --no-cache \
    autoconf g++ libtool make curl-dev \
    libxml2-dev linux-headers m4 autoconf \
    bzip2 bzip2-dev icu-dev libzip libzip-dev \
    libmemcached-dev zlib libwebp-dev libjpeg-turbo-dev \
    libpng-dev libzip-dev libxpm-dev freetype \
    libtool freetype-dev postgresql-dev openssl openssl-dev

RUN docker-php-ext-install intl pcntl shmop soap sockets sysvsem xmlrpc
RUN docker-php-ext-install bz2 mysqli pdo_mysql zip pdo_pgsql
RUN docker-php-ext-configure gd \
	--with-png-dir \
	--with-jpeg-dir \
	--with-xpm-dir \
	--with-webp-dir \
	--with-freetype-dir \
	&& docker-php-ext-install -j$(nproc) gd

RUN pecl install msgpack \
 && pecl install igbinary \
 && docker-php-ext-enable igbinary msgpack \
 && pecl install swoole \
 && pecl install redis \
 && pecl install memcached \
 && pecl install mongodb \
 && pecl install xdebug \
 && docker-php-ext-enable redis memcached mongodb xdebug swoole

RUN curl -sS https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer \
    && composer config -g repo.packagist composer https://mirrors.aliyun.com/composer/ \
    && composer clear-cache

