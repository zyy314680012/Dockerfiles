FROM php:8.3-fpm

# 更换 apt 源为 中科大
RUN cp /etc/apt/sources.list.d/debian.sources /etc/apt/sources.list.d/debian.sources.bak \
sed -i 's/deb.debian.org/mirrors.ustc.edu.cn/g' /etc/apt/sources.list.d/debian.sources

## 更新软件源
RUN apt-get clean && apt-get update

#
RUN apt-get install -y apt-transport-https ca-certificates

# 安装 php 扩展
RUN apt-get install -y libonig-dev
RUN docker-php-ext-install gettext calendar mbstring mysqli pdo_mysql exif shmop sockets sysvmsg sysvsem sysvshm

## 安装  phpredils
COPY 6.0.2.tar.gz /tmp/6.0.2.tar.gz
RUN mkdir -p /usr/src/php/ext/redis \
# && curl -L https://github.com/phpredis/phpredis/archive/3.1.6.tar.gz | tar xvz -C /usr/src/php/ext/redis --strip 1 \
# && curl -L https://d.zdic.lol/6.0.2.tar.gz | tar xvz /tmp/6.0.2.tar.gz -C /usr/src/php/ext/redis --strip 1 \
&& tar xvzf /tmp/6.0.2.tar.gz -C /usr/src/php/ext/redis --strip 1 \
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
&& printf "\n" | pecl install mcrypt
RUN docker-php-ext-enable mcrypt

#安装 zip
RUN apt-get install -y --no-install-recommends libzip-dev \
&& docker-php-ext-install zip

# 安装 bcmath 扩展
RUN docker-php-ext-install bcmath