# kalabox-mysql
FROM ubuntu:14.04
MAINTAINER Mike Pirog <mike@kalamuna.com>

# Get the most recent things
RUN apt-get update
RUN apt-get upgrade -y

# Install basic utilities
RUN apt-get install -y -q iputils-ping wget curl tree vim

# Add files
ADD . /src
RUN cp -rf /src/files/* /
RUN rm -rf /src

RUN chown -R mysql.mysql /etc/mysql
RUN rm -Rf /var/lib/mysql

EXPOSE 3306
CMD ["/usr/bin/mysqld_safe"]