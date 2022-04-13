FROM alpine:3.15

RUN apk --no-cache add php8=8.0.14-r0 \
    php8-ctype \
    php8-curl \
    # php8-dom \
    php8-fileinfo \
    php8-fpm \
    php8-gd \
    # php8-iconv \
    # php8-intl \
    php8-mbstring \
    # php8-opcache \
    # php8-openssl \
    # php8-pecl-imagick \
    # php8-phar \
    php8-session \
    php8-simplexml \
    # php8-soap \
    php8-xml \
    # php8-xmlreader \
    # php8-zip \
    # php8-zlib \
    # php8-pdo \
    # php8-xmlwriter \
    # php8-tokenizer \
    nginx=1.20.2-r0



WORKDIR /opt
ADD ./oracle-instantclient-basic_21.5.0.0.0-2_amd64.deb  /opt

RUN apt-get install libaio1 
RUN dpkg -i oracle-instantclient.deb




#RUN ln -s /usr/bin/php8 /usr/bin/php
RUN mkdir -p /var/www/html

COPY config/nginx.conf  /etc/nginx/nginx.conf
COPY config/fpm.conf    /etc/php8/php-fpm.d/www.conf
COPY config/php.ini     /etc/php8/conf.d/custom.ini
COPY src/               /var/www/html/

RUN chown -R nobody.nobody /var/www/html && \
  chown -R nobody.nobody /run && \
  chown -R nobody.nobody /var/lib/nginx && \
  chown -R nobody.nobody /var/log/nginx

USER nobody

CMD php-fpm8; nginx -g "daemon off;"
