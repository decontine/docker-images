FROM alpine:3.15

RUN apk --no-cache add php8=8.0.17-r0 \
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

RUN mkdir -p /var/www/html

COPY ./docker/config/nginx.conf   /etc/nginx/nginx.conf
COPY ./docker/config/fpm.conf     /etc/php8/php-fpm.d/www.conf
COPY ./docker/config/php.ini      /etc/php8/conf.d/custom.ini
COPY ./docker/ssl/certificate.crt /etc/ssl/certificate.crt
COPY ./docker/ssl/private.key     /etc/ssl/private.key
COPY src/                         /var/www/html/

RUN chown -R nobody.nobody /var/www/html && \
    chown -R nobody.nobody /run && \
    chown -R nobody.nobody /var/lib/nginx && \
    chown -R nobody.nobody /var/log/nginx
USER nobody

CMD php-fpm8; nginx -g "daemon off;"
