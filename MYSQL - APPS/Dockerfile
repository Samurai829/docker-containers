FROM mysql:latest
MAINTAINER samurai829

VOLUME ["/mysql-data/", "/var/lib/mysql"]
ENV MYSQL_ROOT_PASSWORD=123
ENV MYSQL_DATABASE=dba_user

EXPOSE 3306/tcp

# docker run -dp 3000:3000 \
# --network net0 
# -e MYSQL_HOST=mysql \
# -e MYSQL_USER=root \
# -e MYSQL_PASSWORD=123 \
# -e MYSQL_DB=todos \
# app:latest

# docker run -dp 3306:3306 \
# -e MYSQL_ROOT_PASSWORD=123 \
# -e MYSQL_DATABASE=todos \
# --network net0 --network-alias mysql \
# mysql:5.7
