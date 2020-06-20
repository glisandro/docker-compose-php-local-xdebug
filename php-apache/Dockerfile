FROM php:7.2-apache

RUN apt-get update
RUN apt-get install -y zlib1g-dev libicu-dev g++
RUN docker-php-ext-configure intl
RUN docker-php-ext-install intl

RUN docker-php-ext-install pdo pdo_mysql

RUN pecl install -f xdebug \
&& echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo 'xdebug.default_enable=1' >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo 'xdebug.remote_enable=1' >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo 'xdebug.remote_connect_back=1' >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo 'xdebug.remote_autostart=1' >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo 'xdebug.remote_handler="dbgp"' >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo 'xdebug.remote_port=9000' >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo 'xdebug.remote_host=localhost' >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo 'xdebug.max_nesting_level=250' >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo 'xdebug.remote_log=/var/www/xdebug.log' >> /usr/local/etc/php/conf.d/xdebug.ini

RUN a2enmod rewrite
RUN a2enmod headers