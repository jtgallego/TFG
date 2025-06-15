FROM php:8.2-apache

# Instala utilidades y extensiones necesarias para Composer
RUN apt-get update && apt-get install -y \
    git \
    unzip \
    zip \
    libzip-dev \
    && docker-php-ext-install pdo pdo_mysql zip

# Habilita el mod_rewrite para Symfony
RUN a2enmod rewrite

# Copia Composer desde la imagen oficial
COPY --from=composer:latest /usr/bin/composer /usr/bin/composer

# Directorio de trabajo
WORKDIR /var/www/html

# Copia tu código
COPY . .

# Instala dependencias PHP
RUN composer install --no-interaction --prefer-dist --optimize-autoloader

# Permisos para Apache
RUN chown -R www-data:www-data /var/www/html
