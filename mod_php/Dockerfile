FROM ubuntu:24.04

RUN apt-get -y update && apt-get install -y apache2 libapache2-mod-php8.3 php8.3
RUN a2enmod php8.3

COPY ./php-mod-site.conf /etc/apache2/sites-available/php-mod-site.conf

# Enable site
RUN a2ensite php-mod-site

RUN mkdir -p /var/www/php-mod
COPY ./index.php /var/www/php-mod/

EXPOSE 80

CMD ["/usr/sbin/apache2ctl", "-D", "FOREGROUND"]
