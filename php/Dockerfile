FROM php:7.4-fpm
LABEL maintaner="378772944@qq.com"

# 使用 阿里源 替换
RUN sed -i "s@http://deb.debian.org@http://mirrors.aliyun.com@g" /etc/apt/sources.list && rm -Rf /var/lib/apt/lists/* &&  cat /etc/apt/sources.list

RUN apt-get update && apt-get install -y \
        libfreetype6-dev \
        libjpeg62-turbo-dev \
        libpng-dev \
        vim \
    && docker-php-ext-configure gd --with-freetype --with-jpeg \
    && docker-php-ext-install -j$(nproc) gd && docker-php-ext-install pdo_mysql

# 安装 PECL 拓展，安装swoole*
RUN  pecl install swoole \
    && docker-php-ext-enable swoole

# 安装 php-redis
RUN  pecl install redis \
    && docker-php-ext-enable redis
