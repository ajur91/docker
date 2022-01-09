FROM php:8.0-fpm

LABEL "AUTHOR" Alberto Urbaez <albertourbaez20@gmail.com>

# SET DEFAULT ENVIRONMENT
# -----------------------------
ENV COMPOSER_VERSION="2.0.11" \
    NODE_VERSION="setup_14.x"

# INSTALL SYSTEM DEPENDENCIES
# -----------------------------
RUN apt-get update && apt-get install -y \
    libfreetype6-dev \
    libicu-dev \
    libjpeg62-turbo-dev \
    libmcrypt-dev \
    libpng-dev \
    libxslt1-dev \
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

# INSTALL NODE, NPM
# -----------------------------
RUN curl -fsSL https://deb.nodesource.com/${NODE_VERSION} | bash - && \
    apt-get update && \
    apt-get install -y --no-install-recommends nodejs && \
    npm install -g npm
    
# INSTALL COMPOSER
# -----------------------------
RUN curl -sS https://getcomposer.org/installer | php -- \
--install-dir=/usr/bin --filename=composer --version=${COMPOSER_VERSION} && chmod +x /usr/bin/composer 

WORKDIR /var/www
COPY . .