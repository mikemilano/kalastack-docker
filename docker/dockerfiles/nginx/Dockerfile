# kalabox-nginx
FROM ubuntu:14.04
MAINTAINER Mike Pirog <mike@kalamuna.com>

# Get the most recent things
RUN apt-get update
RUN apt-get upgrade -y

# Install basic utilities
RUN apt-get install -y -q iputils-ping wget curl tree vim

# Install nginx
RUN apt-get install -y -q nginx

# Add files
ADD . /src
RUN cp -rf /src/files/* /
RUN rm -rf /src

# Modify default config
RUN sed -i -e"s/keepalive_timeout\s*65/keepalive_timeout 2/" /etc/nginx/nginx.conf
RUN echo "daemon off;" >> /etc/nginx/nginx.conf

EXPOSE 80
CMD ["/usr/sbin/nginx"]