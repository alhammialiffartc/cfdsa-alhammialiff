# mysql as base image
FROM mysql:5.7

ENV MYSQL_ROOT_PASSWORD=mypassword

#copy bgg.spl to /docker-entrypoint-initdb.d dir
ADD bgg.sql /docker-entrypoint-initdb.d