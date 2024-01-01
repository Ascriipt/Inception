FROM debian:bullseye

RUN apt-get update -y \
    && apt-get upgrade -y \
    && apt-get install mariadb-server -y \
    && apt-get install mariadb-client -y \
    && apt-get install procps -y

COPY conf/50-server.cnf /etc/mysql/mariadb.conf.d/50-server.cnf

RUN mkdir -p /var/run/mysqld /var/lib/mysql
RUN chown mysql:mysql /var/run/mysqld/
RUN chmod -R 755 /var/run/mysqld/
RUN chown mysql:mysql /var/lib/mysql/
RUN chmod -R 755 /var/lib/mysql/

EXPOSE 3306

COPY tools/dbscript.sh .
RUN chmod +x ./dbscript.sh

ENTRYPOINT ["bash", "./dbscript.sh"]
