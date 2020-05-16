FROM php:7.4-apache

MAINTAINER Tomas Bodnar <bodnarto@gmail.com>

ENV NODE_MAJOR_VERSION=12
ENV APACHE_DOCUMENT_ROOT=/var/www/html/public

# Update apt repository and install tools
RUN DEBIAN_FRONTEND=noninteractive apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y --no-install-recommends apt-transport-https git zip unzip mariadb-client \
    nano wget lsb-release gnupg ca-certificates curl iputils-ping telnet sudo libzip-dev libmcrypt-dev libpng-dev && \
    apt-get clean && rm -rf /var/lib/apt/lists/*

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install nodejs
RUN curl -sL https://deb.nodesource.com/setup_${NODE_MAJOR_VERSION}.x | sudo -E bash - && apt-get install -y nodejs

# Change document root
RUN sed -ri -e 's!/var/www/html!${APACHE_DOCUMENT_ROOT}!g' /etc/apache2/sites-available/*.conf

# enable mode rewrite
RUN a2enmod rewrite

# install necessary php plugins
RUN docker-php-ext-configure zip && \
    docker-php-ext-install pdo_mysql bcmath zip gd

# install and enable xdebug
RUN pecl install xdebug-2.9.5 && \
    docker-php-ext-enable xdebug
