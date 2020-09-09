FROM alpine:3.12
LABEL author="Serge NOEL <serge.noel@easylinux.fr>" \
      description="Apache avec Php"

# Copier l'arborescence dans l'image
ADD Files /

# installation d'Apache, Php 
RUN apk add php7-apache2 php7-ldap \
    && sed -i "s|/var/www/localhost/htdocs|/var/www/html|g" /etc/apache2/httpd.conf \
    && ln -s /dev/stdout /var/log/apache2/access.log \
    && ln -s /dev/stderr /var/log/apache2/error.log \
    && chown apache: /var/www/html/documents

EXPOSE 80
# Depots des documents gérés par l'application
VOLUME /var/www/html/documents
# Configuration de la base de données (identifiants, ...) 
VOLUME /var/www/html/config/config.ini

CMD /usr/sbin/httpd -D FOREGROUND
