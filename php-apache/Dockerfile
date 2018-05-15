FROM php:7.2.5-apache

RUN echo 'deb http://httpredir.debian.org/debian jessie contrib' >> /etc/apt/sources.list \
  && apt-get update && apt-get upgrade -y --no-install-recommends apt-utils

# Install zip
RUN apt-get install -y \
        libzip-dev \
        zip \
  && docker-php-ext-configure zip --with-libzip \
  && docker-php-ext-install zip

# Install intl
RUN apt-get install -y \
        libicu-dev \
        g++ \
  && docker-php-ext-install intl

# Install gd
RUN apt-get install -y libfreetype6-dev libjpeg62-turbo-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install gd

# Install mysql
RUN docker-php-ext-install pdo pdo_mysql

# enable Apache mod_rewrite
RUN a2enmod rewrite

# Install nano
RUN apt-get install -y nano

# Install PHP composer
RUN php -r "readfile('https://getcomposer.org/installer');" | \
  php -- --install-dir=/usr/local/bin --filename=composer
ENV COMPOSER_ALLOW_SUPERUSER=1


