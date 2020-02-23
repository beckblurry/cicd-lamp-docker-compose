FROM php:7.1.20-apache

RUN apt-get -y update --fix-missing
RUN apt-get upgrade -y

RUN apt-get -y install apt-utils nano wget dialog

RUN apt-get -y install --fix-missing apt-utils build-essential git curl libcurl3 libcurl3-dev zip

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN pecl install xdebug-2.5.0
RUN docker-php-ext-enable xdebug

RUN apt-get -y install libmcrypt-dev
RUN docker-php-ext-install mcrypt

RUN apt-get -y install libsqlite3-dev libsqlite3-0 mysql-client
RUN docker-php-ext-install pdo_mysql pdo_sqlite mysqli curl tokenizer json 

RUN a2enmod rewrite headers

COPY www/ /var/www/html/
COPY php.ini /usr/local/etc/php/php.ini
COPY default.conf /etc/apache2/sites-enabled/default.conf
COPY ioncube_loader_lin_7.1.so /usr/local/lib/php/extensions/no-debug-non-zts-20160303/
