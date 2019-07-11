FROM dockerboxes/docker-ubuntu-bionic-apache2

MAINTAINER shashank jaiswal <shashank.jaiswal@aventri.com>

RUN apt-get update

RUN a2dismod mpm_event
RUN a2enmod mpm_prefork
RUN a2enmod ssl
RUN a2enmod rewrite
RUN a2enmod proxy
RUN a2enmod proxy_fcgi
RUN a2enmod proxy_http
RUN a2enmod headers
RUN a2enmod actions

COPY ./conf/ssl /var/www/config/ssl

RUN rm /etc/apache2/sites-enabled/000-default.conf
COPY ./conf/*.conf /etc/apache2/sites-enabled/

EXPOSE 80 443

WORKDIR /root

CMD apachectl -D FOREGROUND


