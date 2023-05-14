FROM php:8.0-apache

RUN apt-get update \
	&& apt-get install -y \
		zip \
		unzip \
		vim \
		wget \
		curl \
		git \
		moreutils \
		dnsutils \
		zlib1g-dev \
		libicu-dev \
    && rm -rf /var/lib/apt/lists/*

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

RUN docker-php-ext-configure intl \
    && docker-php-ext-install pdo pdo_mysql intl \
    && a2enmod headers \
        expires \
        rewrite \
        ssl

COPY apache2/host.conf /etc/apache2/sites-available/000-default.conf
COPY php.ini /usr/local/etc/php/conf.d/zzzz-php.ini

WORKDIR /app
