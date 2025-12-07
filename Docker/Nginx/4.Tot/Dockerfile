FROM php:fpm

# Instalar extensiones de base de datos
RUN docker-php-ext-install pdo pdo_mysql

# Crear las carpetas destino
RUN mkdir -p /var/www/camisetes.com
RUN mkdir -p /var/www/db.com

# COPIAR TU CONTENIDO
# Copiamos tu carpeta "llista-camisetes-main" a "/var/www/camisetes.com"
COPY ./llista-camisetes-main /var/www/camisetes.com

# Copiamos tu carpeta "llibres-database" a "/var/www/db.com"
COPY ./llibres-database /var/www/db.com

# Permisos para que el servidor pueda leer los archivos
RUN chown -R www-data:www-data /var/www/*