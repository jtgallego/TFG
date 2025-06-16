FROM php:8.1-apache

# Instala extensiones necesarias para Symfony
RUN apt-get update && apt-get install -y \
    unzip \
    git \
    zip \
    libicu-dev \
    libonig-dev \
    libzip-dev \
    && docker-php-ext-install intl pdo pdo_mysql zip

# Habilita mod_rewrite de Apache (Symfony lo necesita)
RUN a2enmod rewrite

# Instala Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Establece el directorio de trabajo
WORKDIR /var/www/html

# Copia el contenido del proyecto
COPY . .

# Instala dependencias PHP con Composer
RUN composer install --no-interaction

# Da permisos a Apache
RUN chown -R www-data:www-data /var/www/html

# Expone el puerto 80 (por si lo necesitas para configurarlo)
EXPOSE 80
