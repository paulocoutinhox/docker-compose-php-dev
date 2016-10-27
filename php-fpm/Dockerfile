######
# See: https://hub.docker.com/_/php/
######

FROM php:7.0.12-fpm
MAINTAINER Paulo Coutinho <paulo@prsolucoes.com>

######
# You can configure php extensions using docker-php-ext-configure
# You can install php extensions using docker-php-ext-install
######

# define timezone
RUN echo "America/Sao_Paulo" > /etc/timezone
RUN dpkg-reconfigure -f noninteractive tzdata
RUN /bin/echo -e "LANG=\"en_US.UTF-8\"" > /etc/default/local

# install dependencies
RUN apt-get update
RUN apt-get install -y build-essential 
RUN apt-get install -y libfreetype6-dev
RUN apt-get install -y libjpeg62-turbo-dev
RUN apt-get install -y libmcrypt-dev
RUN apt-get install -y libpng12-dev
RUN apt-get install -y curl
RUN apt-get install -y libcurl3
RUN apt-get install -y libcurl3-dev
RUN apt-get install -y zlib1g-dev
RUN apt-get install -y libicu-dev
RUN apt-get install -y libmemcached-dev 

# install memcache manually because dont have packages for PHP7
RUN curl -L -o /tmp/memcached.tar.gz "https://github.com/php-memcached-dev/php-memcached/archive/php7.tar.gz" 
RUN mkdir -p /usr/src/php/ext/memcached
RUN tar -C /usr/src/php/ext/memcached -zxvf /tmp/memcached.tar.gz --strip 1
RUN docker-php-ext-configure memcached
RUN docker-php-ext-install memcached
RUN rm /tmp/memcached.tar.gz

# install, configure and enable all php packages
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-install -j$(nproc) intl
RUN docker-php-ext-install -j$(nproc) pdo
RUN docker-php-ext-install -j$(nproc) pdo_mysql
RUN docker-php-ext-install -j$(nproc) curl
RUN docker-php-ext-install -j$(nproc) iconv
RUN docker-php-ext-install -j$(nproc) mcrypt

RUN pecl install xdebug
RUN docker-php-ext-enable xdebug