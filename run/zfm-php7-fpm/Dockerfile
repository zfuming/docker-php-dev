FROM php:7.1-fpm
ENV DRUSH_VERSION 8.1.2

RUN apt-get clean -y
# Install the PHP extensions we need
RUN apt-get update && \
apt-get install -y --no-install-recommends \
    curl \
    mysql-client \
    libmemcached-dev \
    libz-dev \
    libpq-dev \
    libjpeg-dev \
    libpng12-dev \
    libfreetype6-dev \
    libicu-dev \
    libssl-dev \
    libmcrypt-dev && \
    docker-php-ext-configure gd --with-png-dir=/usr --with-jpeg-dir=/usr && \
    docker-php-ext-install gd pdo_mysql mysqli opcache intl bcmath zip && \
    docker-php-ext-enable bcmath zip pdo_mysql
# drush command
RUN curl -fsSL -o /usr/local/bin/drush "https://github.com/drush-ops/drush/releases/download/$DRUSH_VERSION/drush.phar" && \
  chmod +x /usr/local/bin/drush
# install composer
RUN php -r "readfile('https://getcomposer.org/installer');" > composer-setup.php \
		&& php composer-setup.php \
		&& php -r "unlink('composer-setup.php');" \
		&& mv composer.phar /usr/local/bin/composer
# install drupal console
RUN php -r "readfile('https://drupalconsole.com/installer');" > drupal.phar \
		&& mv drupal.phar /usr/local/bin/drupal \
		&& chmod +x /usr/local/bin/drupal

VOLUME /app/web
WORKDIR /app/web