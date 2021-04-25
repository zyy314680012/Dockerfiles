FROM php:7.3-fpm

# 更换 apt 源为 中科大
RUN mv /etc/apt/sources.list /etc/apt/sources.list.bak \
&& echo "deb http://mirrors.ustc.edu.cn/debian stable main contrib non-free" >> /etc/apt/sources.list \
&& echo "deb http://mirrors.ustc.edu.cn/debian stable-proposed-updates main contrib non-free" >> /etc/apt/sources.list

## 更新软件源
RUN apt-get clean && apt-get update

#
RUN apt-get install -y apt-transport-https ca-certificates

# 安装 php 扩展
RUN docker-php-ext-install gettext calendar mbstring mysqli pdo_mysql exif shmop sockets sysvmsg sysvsem sysvshm

## 安装  phpredils
RUN mkdir -p /usr/src/php/ext/redis \
&& curl -L https://github.com/phpredis/phpredis/archive/3.1.6.tar.gz | tar xvz -C /usr/src/php/ext/redis --strip 1 \
&& echo 'redis' >> /usr/src/php-available-exts \
&& docker-php-ext-install redis

## 安装 gd
RUN apt-get install -y libwebp-dev libjpeg-dev libpng-dev libfreetype6-dev \
&& docker-php-ext-install gd

# 安装 bz2 
RUN apt-get install -y --no-install-recommends libbz2-dev \
&& docker-php-ext-install bz2

# 安装 gmp
# 软链接
RUN ln -s /usr/include/x86_64-linux-gnu/gmp.h /usr/include/gmp.h 
RUN apt-get install -y --no-install-recommends libgmp-dev \
&& docker-php-ext-install gmp

# 安装 intl
RUN apt-get install -y --no-install-recommends libicu-dev \
&& docker-php-ext-install intl

# 安装 mcrypt
RUN apt-get install -y --no-install-recommends libmcrypt-dev \
&& pecl install mcrypt
# && docker-php-ext-install mcrypt

#安装 zip
RUN apt-get install -y --no-install-recommends libzip-dev \
&& docker-php-ext-install zip

# 安装 wddx 
RUN apt-get install -y --no-install-recommends libxml2-dev libtidy-dev libxslt1-dev \
&& docker-php-ext-install soap wddx xmlrpc tidy xsl

# 安装 bcmath 扩展
RUN docker-php-ext-install bcmath