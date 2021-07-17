# php-alpine (17mb)

docker build . -t user/app

docker run -d -p 8888:8080 user/app

http://localhost:8888/
