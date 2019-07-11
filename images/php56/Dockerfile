FROM dockerboxes/docker-ubuntu-bionic-php5.6

MAINTAINER shashank jaiswal <shashank.jaiswal@aventri.com>

RUN apt-get update

# install PEAR channels && packages
RUN pear channel-update pear.php.net
RUN pear install Mail 
RUN pear install Mail_Mime 
RUN pear install Mail_mimeDecode 
RUN pear install Net_SMTP

#PHP version
RUN php -version

RUN cp /etc/php/5.6/fpm/php-fpm.conf /etc/php/5.6/fpm/php-fpm-backup.conf
RUN rm -rf /etc/php/5.6/fpm/php-fpm.conf
COPY ./conf/php-fpm.conf-development /etc/php/5.6/fpm/php-fpm.conf

RUN cp -R /etc/php/5.6/fpm/pool.d /etc/php/5.6/fpm/pool.d-backup
RUN rm -rf /etc/php/5.6/fpm/pool.d
COPY ./conf/php-fpm.d /etc/php/5.6/fpm/pool.d

COPY ./conf/php.ini-development /usr/local/etc/php/5.6/php.ini

EXPOSE 9000 9010 9020 9030 9040 9050

# Include the start script
COPY start.sh /usr/local/bin/start.sh
RUN chmod +x /usr/local/bin/start.sh
WORKDIR /root

CMD ["start.sh"]
