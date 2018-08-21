#apache-tools/Dockerfile
FROM ubuntu:18.04

# Install apache, PHP, and supplimentary programs. openssh-server, curl, and lynx-cur are for debugging the container.
RUN apt-get update && apt-get -y upgrade && DEBIAN_FRONTEND=noninteractive apt-get -y install \
    apache2 php7.2 php7.2-mysql php7.2-xml libapache2-mod-php7.2 php7.2-curl libcurl3-dev curl lynx-common lynx php7.2-gd

# Enable apache mods.
RUN a2enmod php7.2
RUN a2enmod rewrite

# Update the PHP.ini file, enable <? ?> tags and quieten logging.
RUN sed -i "s/short_open_tag = Off/short_open_tag = On/" /etc/php/7.2/apache2/php.ini
RUN sed -i "s/error_reporting = .*$/error_reporting = E_ERROR | E_WARNING | E_PARSE/" /etc/php/7.2/apache2/php.ini
# Manually set up the apache environment variables
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_LOCK_DIR /var/lock/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
#RUN ln -snf /usr/share/zoneinfo/Europe/Paris /etc/localtime \
        #&& echo Europe/Paris > /etc/timezone \
        #&& dpkg-reconfigure -f noninteractive tzdata
#RUN "date"

# Expose apache.
EXPOSE 80
#CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]
CMD /usr/sbin/apache2ctl -D FOREGROUND

