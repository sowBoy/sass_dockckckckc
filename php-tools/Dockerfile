#php-tools/Dockerfile
FROM php:7.2-apache
RUN docker-php-source extract \
    && docker-php-source delete
RUN apt-get update && apt-get install -y \
    git \
    unzip\
    libcurl3-dev\
    libpng-dev\
    libicu-dev\
    g++\
    exiftool\
    gnupg2\
    gcc\
    make
#php zip
RUN apt-get update && \
    apt-get install -y \
        zlib1g-dev\
        curl\
        libzip-dev
# Install Composer
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer
RUN composer --version
#install symfony
RUN mkdir -p /usr/local/bin
RUN curl -LsS https://symfony.com/installer -o /usr/local/bin/symfony
RUN chmod a+x /usr/local/bin/symfony
#libxml2
RUN apt-get install libxml2-dev
# Set timezone
#RUN rm /etc/localtime
#RUN rm /etc/timezone
#RUN ln -s /usr/share/zoneinfo/Europe/Paris /etc/localtime
#RUN ln -s /usr/share/zoneinfo/Europe/Paris /etc/timezone
RUN ln -snf /usr/share/zoneinfo/Europe/Paris /etc/localtime \
	&& echo Europe/Paris > /etc/timezone \
        && dpkg-reconfigure -f noninteractive tzdata
RUN "date"

# Memory Limit
RUN echo "memory_limit=-1" > $PHP_INI_DIR/conf.d/memory-limit.ini

#node js
RUN curl -sL https://deb.nodesource.com/setup_10.x | bash -
RUN apt-get install -y nodejs
# Add source for yarn
RUN curl -sS http://dl.yarnpkg.com/debian/pubkey.gpg | apt-key add -
RUN echo "deb http://dl.yarnpkg.com/debian/ stable main" | tee /etc/apt/sources.list.d/yarn.list

# Install dependencies
RUN apt-get update && apt-get install -y yarn

RUN docker-php-ext-configure intl
# Type docker-php-ext-install to see available extensions
RUN docker-php-ext-install pdo pdo_mysql zip curl gd intl exif soap bcmath 
RUN ["apt-get", "update"]
RUN ["apt-get", "install", "-y", "vim"]
VOLUME ["/var/www"]
WORKDIR /var/www

