FROM php:7.2-apache

RUN apt-get update \
  && apt-get install -y libfreetype6-dev libjpeg62-turbo-dev libpng-dev libmcrypt-dev \
  && docker-php-ext-install pdo_mysql mysqli mbstring gd iconv zip\
  && pecl install mcrypt-1.0.1 \
  && pecl install xdebug \
  && docker-php-ext-enable mcrypt
RUN a2enmod rewrite
RUN a2enmod include

COPY ./base.conf /etc/apache2/sites-available/base.conf
RUN a2ensite base.conf

RUN chown www-data:www-data -R /var/www


COPY php.ini /usr/local/etc/php/


# COPY php.ini /usr/local/etc/php/NameVirtualHost *:80
# LoadModule include_module modules/mod_include.so