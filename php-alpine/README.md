# php-alpine

## Dockerfile-slim (17MB)

PHP 7

```
docker build . -t alp:1.0

docker run -d -p 8888:8080 alp:1.0

http://localhost:8888/
```


## Dockerfile (44MB)

PHP 8 + NGINX + HTTPS

Put certificate.crt and private.key into docker/ssl

```
docker build . -t alp:1.0

docker run -d -p 443:443 alp:1.0

https://localhost/
```
