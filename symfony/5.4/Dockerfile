FROM php:8.0-apache

# SET DEFAULT ENVIRONMENT
# -----------------------------
ENV COMPOSER_VERSION="2.0.11" \
    NODE_VERSION="setup_14.x"

# INSTALL SYSTEM DEPENDENCIES
# -----------------------------
RUN apt-get update \
    && apt-get install -y \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libxslt1-dev \
    nano \
    wget \
    lynx \
    psmisc \
    libssl-dev \
    libedit2 \
    libxslt1-dev \
    apt-utils \
    gnupg \
    redis-tools \
    curl \
    unzip \
    tar \
    cron \
    bash-completion \
    && apt-get clean

# INSTALL DEPENDENCIES
# -----------------------------
RUN docker-php-ext-configure \
    gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/; \
    docker-php-ext-install \
    gd \
    intl \
    pdo_mysql \
    xsl \
    opcache \
    sockets \
    bcmath \
    soap

RUN apt-get update \
    && apt-get install -y \
        librabbitmq-dev \
        libssh-dev \
    && pecl install amqp \
    && docker-php-ext-enable amqp

# Install composer
RUN php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');" \
    && php composer-setup.php --install-dir=/usr/local/bin/ --filename=composer  --version=${COMPOSER_VERSION} \
    && php -r "unlink('composer-setup.php');"

# INSTALL NODE, NVM, NPM AND GRUNT
# -----------------------------
RUN apt-get update && \
    apt-get install -y --no-install-recommends gnupg && \
    curl -fsSL https://deb.nodesource.com/${NODE_VERSION} | bash - && \
    apt-get install -y --no-install-recommends nodejs && \
    apt-get update && \
    npm install -g npm

# INSTALL COMPOSER
# -----------------------------
RUN curl -sS https://getcomposer.org/installer | php -- \
--install-dir=/usr/bin --filename=composer --version=${COMPOSER_VERSION} && chmod +x /usr/bin/composer 

# CONFIGURING SYSTEM
# -----------------------------
ADD .docker/config/local.lan.conf /etc/apache2/sites-available/local.lan.conf
RUN ln -s /etc/apache2/sites-available/local.lan.conf /etc/apache2/sites-enabled/local.lan.conf \
    && a2ensite local.lan.conf \
    && a2dissite 000-default.conf

COPY .docker/bin/* /usr/local/bin/

RUN chmod +x /usr/local/bin/*
RUN chmod 777 -Rf /var/www /var/www/.* \
	&& chown -Rf www-data:www-data /var/www /var/www/.* \
	&& usermod -u 1000 www-data \
	&& chsh -s /bin/bash www-data\
	&& a2enmod rewrite \
	&& a2enmod headers