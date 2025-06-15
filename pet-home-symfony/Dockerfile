FROM php:8.1-apache

# Instala extensiones necesarias, etc. (si no lo has hecho ya)

COPY apache.conf /etc/apache2/sites-available/000-default.conf

RUN a2enmod rewrite

WORKDIR /var/www/html

COPY . .

RUN composer install

RUN chown -R www-data:www-data /var/www/html
