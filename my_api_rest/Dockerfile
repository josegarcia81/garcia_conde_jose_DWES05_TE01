# Usa la imagen oficial de PHP con Apache
FROM php:8.2-apache

# Instalar extensiones de PHP necesarias
RUN apt-get update && apt-get install -y \
    libzip-dev zip unzip git \
    && docker-php-ext-install pdo_mysql zip

# Activar mod_rewrite de Apache
RUN a2enmod rewrite

# Copiar el proyecto al contenedor
COPY . /var/www/html/

RUN mkdir -p /var/www/html/storage /var/www/html/bootstrap/cache \
    && chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache

# Establecer permisos en storage y bootstrap/cache
RUN chown -R www-data:www-data /var/www/html/storage /var/www/html/bootstrap/cache

# Instalar Composer
COPY --from=composer:2 /usr/bin/composer /usr/bin/composer

# Instalar dependencias de Laravel
RUN composer install --no-dev --optimize-autoloader

# Generar key de Laravel (puede sobrescribirse con ENV)
RUN php artisan key:generate

# Exponer puerto
EXPOSE 80

# Iniciar Apache en primer plano
CMD ["apache2-foreground"]
