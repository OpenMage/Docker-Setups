FROM php:7.3-fpm
RUN apt-get update && apt-get install -y \
  cron \
  git \
  gzip \
  libfreetype6-dev \
  libicu-dev \
  libjpeg62-turbo-dev \
  libmcrypt-dev \
  libpng-dev \
  libxslt1-dev \
  lsof \
  mysql-client \
  vim \
  libzip-dev \
  zip


RUN docker-php-ext-configure \
  gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/

RUN docker-php-ext-install \
  bcmath \
  gd \
  intl \
  mbstring \
  opcache \
  pdo_mysql \
  soap \
  xsl \
  zip

RUN pecl channel-update pecl.php.net \
  && pecl install xdebug \
  && docker-php-ext-enable xdebug \
  && sed -i -e 's/^zend_extension/\;zend_extension/g' /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini

RUN curl -sS https://getcomposer.org/installer | \
  php -- --install-dir=/usr/local/bin --filename=composer




# Install magerun
RUN curl -o magerun https://files.magerun.net/n98-magerun.phar && \
    chmod +x ./magerun && \
    cp ./magerun /usr/local/bin/ && \
    rm ./magerun && \
    apt-get update && \
    apt-get install -qy mysql-client


#COPY conf/php-fpm.conf /usr/local/etc/php-fpm.d/
#COPY conf/pool.d /usr/local/etc/pool.d
COPY conf/php.ini /usr/local/etc/php/conf.d/10-php.ini
COPY conf/n98-magerun.yaml /etc/n98-magerun.yaml

# RUN /usr/local/bin/magerun install --dbHost="db" --dbUser="magento" --dbPass="magento" --dbName="magento" --installSampleData=yes --useDefaultConfigParams=yes --magentoVersionByName="openmage-lts-1.9.3.x" --installationFolder="/var/www/" --baseUrl="http://www.openmage.test/"
# RUN /usr/local/bin/magerun install --dbHost="db" --dbUser="magento" --dbPass="magento" --dbName="magento" --installSampleData=yes --useDefaultConfigParams=yes --magentoVersionByName="openmage-lts-1.9.4.x" --installationFolder="/var/www/" --baseUrl="http://www.openmage.test/"


VOLUME /var/www

#WORKDIR /var/www

EXPOSE 9001
