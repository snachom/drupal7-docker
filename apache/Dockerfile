FROM php:5.5-apache
RUN apt-get update && apt-get install -y \
	git \
	wget \
	zlib1g-dev \
	zip \
	vim \
	mysql-client \
	libpng12-dev \
	&& docker-php-ext-install mbstring \
	&& docker-php-ext-install mysql \
	&& docker-php-ext-install mysqli \
	&& docker-php-ext-install gd

RUN curl -sS https://getcomposer.org/installer | php \
	&& mv composer.phar /usr/bin/composer

RUN composer global require drush/drush:7.x \
	&& ln -s /root/.composer/vendor/bin/drush /usr/bin/drush

RUN docker-php-ext-install pdo pdo_mysql

RUN a2enmod rewrite

ADD scripts/ /tmp/scripts
ADD templates/apache2.conf /etc/apache2/
ADD templates/php.ini /usr/local/etc/php/
