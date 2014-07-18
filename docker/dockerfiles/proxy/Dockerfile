# kalabox-proxy
FROM ubuntu:14.04

# Get the most recent things
RUN apt-get update
RUN apt-get upgrade -y

# Install basic utilities
RUN apt-get install -y -q iputils-ping wget curl tree vim

# Install Nginx.
RUN add-apt-repository -y ppa:nginx/stable

RUN apt-get update
RUN apt-get install -y nginx
RUN echo "daemon off;" >> /etc/nginx/nginx.conf

EXPOSE 80
CMD ["/usr/sbin/nginx"]