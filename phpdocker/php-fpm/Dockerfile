#FROM phpdockerio/php72-fpm:latest
FROM php:7.2.8-alpine3.7
WORKDIR "/application"

# Install selected extensions and other stuff
RUN apk --update add php7-pgsql php7-xdebug php7-gmp php7-imagick php7-pspell php7-tidy php7-xmlrpc php7-xsl zlib-dev php7-zip # php7-yaml

RUN docker-php-source extract \
    && docker-php-ext-install zip \
    && docker-php-ext-enable zip \
    && docker-php-source delete

# Install wget curl git
RUN apk --update add wget curl git && rm /var/cache/apk/*

# PHP modules loaded
# [PHP Modules]
# Core, ctype, curl, date, dom, fileinfo, filter, ftp, hash, iconv, json, libxml, mbstring, mysqlnd,
# openssl, pcre, PDO, pdo_sqlite, Phar, posix, readline, Reflection, session, SimpleXML, sodium, SPL, sqlite3, standard, tokenizer, xml, xmlreader, xmlwriter, zlib

# Install composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Install Laravel
RUN composer global require "laravel/installer"

# Allow to run the image in the bash shell
ENTRYPOINT ["tail", "-f", "/dev/null"]
