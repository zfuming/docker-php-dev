FROM php:7.1.3-fpm
ENV DRUSH_VERSION 8.1.2

RUN apt-get clean -y
# Install the PHP extensions we need

RUN apt-get update && \
apt-get install -y --no-install-recommends \
    curl \
    mysql-client \
    libmemcached-dev \
    libz-dev \
    libzip-dev \
    libpq-dev \
    libjpeg-dev \
    libpng12-dev \
    libfreetype6-dev \
    libicu-dev \
    libssl-dev \
    libmemcached-dev \
    zlib1g-dev \
    libmcrypt-dev && \
    docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr && \
    docker-php-ext-install gd pdo_mysql mysqli opcache intl bcmath zip mcrypt sockets && \
    docker-php-ext-enable bcmath zip pdo_mysql mcrypt sockets

# install memcached 
RUN pecl install memcached

# install xdebug
RUN pecl install xdebug

# drush command
ADD ./drush.phar /usr/local/bin/drush
RUN chmod +x /usr/local/bin/drush

# install composer
ADD ./composer.phar /usr/local/bin/composer
RUN chmod +x /usr/local/bin/composer

# config china mirror
RUN composer config -g repo.packagist composer https://packagist.phpcomposer.com

# install drupal console
RUN curl https://drupalconsole.com/installer -L -o drupal.phar && \
    mv drupal.phar /usr/local/bin/drupal && \
    chmod +x /usr/local/bin/drupal

VOLUME /app/web
WORKDIR /app/web
