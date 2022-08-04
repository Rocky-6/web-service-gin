FROM mysql:8.0

ENV MYSQL_ROOT_PASSWORD=my-secret-pw

ADD ./init.sql /docker-entrypoint-initdb.d/init.sql
ADD ./my.cnf /etc/mysql/conf.d/my.cnf

CMD [ "mysqld" ]