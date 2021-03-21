FROM php:fpm-alpine3.12

RUN docker-php-ext-install mysqli pdo pdo_mysql

ADD https://raw.githubusercontent.com/mlocati/docker-php-extension-installer/master/install-php-extensions /usr/local/bin/
RUN chmod +x /usr/local/bin/install-php-extensions \
    && sync \
    && install-php-extensions gd gettext zip
