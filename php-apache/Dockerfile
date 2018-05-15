FROM php:7.2.5-apache

RUN echo 'deb http://httpredir.debian.org/debian jessie contrib' >> /etc/apt/sources.list \

&& apt-get update && apt-get upgrade -y

# install zip
RUN apt-get install -y \
        libzip-dev \
        zip \
  && docker-php-ext-configure zip --with-libzip \
  && docker-php-ext-install zip

# install intl
RUN apt-get install -y \
        libicu-dev \
        g++ \
  && docker-php-ext-install intl

# install mysql
RUN docker-php-ext-install pdo pdo_mysql

# enable Apache mod_rewrite
RUN a2enmod rewrite

# install nano
RUN apt-get install -y nano

#PHP composer
RUN php -r "readfile('https://getcomposer.org/installer');" | php -- --install-dir=/usr/local/bin --filename=composer
