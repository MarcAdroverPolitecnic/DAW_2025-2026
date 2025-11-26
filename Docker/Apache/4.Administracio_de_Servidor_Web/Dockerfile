FROM php:apache

# Carpetes de les webs
RUN mkdir -p /var/www/camisetes.com
RUN mkdir -p /var/www/llibres.com
RUN mkdir -p /var/www/db.com

# Contingut de les webs
COPY ./llista-camisetes-main /var/www/camisetes.com
COPY ./llibres-json /var/www/llibres.com
COPY ./llibres-database /var/www/db.com

# VirtualHosts (assegura't que són .conf)
COPY virtualHosts/* /etc/apache2/sites-available/

# Certificats
COPY certs/*.key /etc/ssl/private/
COPY certs/*.crt /etc/ssl/certs/
RUN chmod 600 /etc/ssl/private/*
RUN chmod 600 /etc/ssl/certs/*

# Modules Apache
RUN a2enmod ssl
RUN a2enmod rewrite
RUN a2enmod proxy
RUN a2enmod proxy_http

# Activar HTTPS VirtualHosts
RUN a2ensite camisetes.com-ssl.conf
RUN a2ensite llibres.com-ssl.conf
RUN a2ensite db.com-ssl.conf

# Activar HTTP VirtualHosts
RUN a2ensite camisetes.com.conf
RUN a2ensite llibres.com.conf
RUN a2ensite db.com.conf

# Extensions PHP
RUN docker-php-ext-install pdo pdo_mysql

# Permisos
RUN chown -R www-data:www-data /var/www/*