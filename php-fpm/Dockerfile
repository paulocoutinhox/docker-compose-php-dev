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

# install and configure all php packages
RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libmcrypt-dev \
        libpng12-dev \
        curl \
        libcurl3 \
        libcurl3-dev \
		zlib1g-dev \
		libicu-dev \
		g++ \
		libmemcached-dev

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install -j$(nproc) gd
RUN docker-php-ext-install -j$(nproc) intl
RUN docker-php-ext-install -j$(nproc) pdo
RUN docker-php-ext-install -j$(nproc) pdo_mysql
RUN docker-php-ext-install -j$(nproc) curl
RUN docker-php-ext-install -j$(nproc) iconv
RUN docker-php-ext-install -j$(nproc) mcrypt

RUN pecl install memcached
RUN pecl install xdebug

docker-php-ext-enable memcached
docker-php-ext-enable xdebug