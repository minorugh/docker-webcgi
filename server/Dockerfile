# Specify docker image
FROM php:7.4-apache

# Read configuration file to PHP and Apache in docker container
COPY ./php/php.ini /usr/local/etc/php/
COPY ./apache/000-default.conf /etc/apache2/conf-available/

# Install
# Specify and install any middleware you need with `apt-get install`
# `a2enmod rewrite` allows you to overwrite Apache settings with .htaccess
RUN apt-get update \
&& apt-get install -y --no-install-recommends \
git \
zip \
unzip \
nano \
python3 \
ruby \
&& apt-get -y clean \
&& rm -rf /var/lib/apt/lists/* \
&& a2enmod cgid \
&& a2enmod include \
&& a2enmod rewrite \
&& a2enconf 000-default

RUN useradd -o -U -m -u 1000 minoru
WORKDIR /var/www
