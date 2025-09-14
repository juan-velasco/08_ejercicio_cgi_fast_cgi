FROM ubuntu:24.04

RUN apt-get -y update && apt-get install -y apache2 libapache2-mod-fcgid php8.3-fpm

RUN a2enmod proxy proxy_fcgi setenvif

COPY ./php-fpm-site.conf /etc/apache2/sites-available/php-fpm-site.conf

# Enable site
RUN a2ensite php-fpm-site

RUN mkdir -p /var/www/php-fpm
COPY ./index.php /var/www/php-fpm/

EXPOSE 80

# Ejecutar start.sh al iniciar el contenedor
COPY start.sh /start.sh
RUN chmod +x /start.sh
CMD ["/start.sh"]
