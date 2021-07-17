FROM alpine
EXPOSE 8080
RUN apk add --no-cache php7-cli php7-json php7-openssl; \
mkdir -p /var/www/html; \
echo '<?php phpinfo();' > /var/www/html/index.php
CMD ["/usr/bin/php", "-S", "0.0.0.0:8080", "-t", "/var/www/html"]
