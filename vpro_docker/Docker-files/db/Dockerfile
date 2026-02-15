FROM mysql:8.0.33

ENV MYSQL_ROOT_PASSWORD="vprodbpass"
ENV MYSQL_DATABASE="accounts"

ADD db_backup.sql /docker-entrypoint-initdb.d/db_backup.sql

EXPOSE 3306


# Universal code multistage build where first part clones repo and gets the backup file
# and 2nd part gets file from 1st part to complete operation
# can be used anywhere without acutually having the db_backup.sql file on your local machine

#FROM alpine/git AS fetcher
#WORKDIR /temp
#RUN git clone -b docker https://github.com/hkhcoder/vprofile-project.git

## STAGE 2: The Database
#FROM mysql:8.0.33

#ENV MYSQL_ROOT_PASSWORD="vprodbpass"
#ENV MYSQL_DATABASE="accounts"

## Grab ONLY the specific SQL file from the first stage
# Note the full path: /temp/[repo-name]/[path-in-repo]
#COPY --from=fetcher /temp/vprofile-project/dockerfiles/db/db_backup.sql /docker-entrypoint-initdb.d/db_backup.sql

#EXPOSE 3306