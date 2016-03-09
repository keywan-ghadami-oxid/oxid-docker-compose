FROM php:7-fpm
ENV COMPOSER_VERSION master
ENV DEBIAN_FRONTEND noninteractive

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN apt-get update 

RUN apt-get install -y  --no-install-recommends apt-utils


# package git is needed for composer install command
RUN apt-get install -y  --no-install-recommends git 

# php gd support: libjpeg62-turbo-dev libpng12-dev gd
RUN apt-get install -y  --no-install-recommends libjpeg62-turbo-dev libpng12-dev libfreetype6-dev
RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ 
RUN docker-php-ext-install -j$(nproc) gd

#mycrypt
#RUN apt-get install -y  --no-install-recommends libmcrypt
#RUN docker-php-ext-install -j$(nproc) mcrypt

RUN docker-php-ext-install -j$(nproc) mbstring iconv  bcmath

#PHP soap support: 
RUN DEBIAN_FRONTEND=noninteractive \
 apt-get install -y  --no-install-recommends libxml2-dev && docker-php-ext-install -j$(nproc) soap

#PHP database extensions database (mysql)
RUN docker-php-ext-install -j$(nproc) mysqli pdo pdo_mysql

ENV DEBIAN_FRONTEND interactive

#PHPFPM runs as www-data, so change the uid to match the host user
#by using an extra script
COPY start.sh /root/start.sh
CMD /root/start.sh

