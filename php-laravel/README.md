# PHP Laravel image
Image customized for developers to run Laravel based on official PHP Apache image.

* php-laravel:php73 based on php:73-apache
* php-laravel:php74 based on php:74-apache
* php-laravel:latest => php-laravel:php74

# Customizations of image
## System Tools and libraries
* install useful system tools and libraries:
  * apt-transport-https 
  * git
  * zip
  * unzip
  * mariadb-client
  * nano
  * wget
  * lsb-release
  * gnupg
  * ca-certificates
  * curl 
  * iputils-ping
  * telnet
  * sudo
  * libzip
  * libmcrypt
  * libpng
* install useful web dev tools:
  * composer (latest version)
  * nodejs (12.x) with npm

## PHP
* installs PHP extensions:
  * pdo_mysql
  * bcmath
  * zip
  * mcrypt
  * xdebug (v2.9.5)

## Apache
* change vhost document root to laravel public dir
* enables mode rewrite`a2enmod rewrite`