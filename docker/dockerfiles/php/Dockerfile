# kalabox-php
FROM ubuntu:14.04
MAINTAINER Mike Pirog <mike@kalamuna.com>

# Get the most recent things
RUN apt-get update
RUN apt-get upgrade -y

# Install basic utilities
RUN apt-get install -y -q iputils-ping wget curl tree vim

# php-fpm config
RUN sed -i -e "s/;cgi.fix_pathinfo=1/cgi.fix_pathinfo=0/g" /etc/php5/fpm/php.ini
RUN sed -i -e "s/;daemonize\s*=\s*yes/daemonize = no/g" /etc/php5/fpm/php-fpm.conf
RUN sed -i -e "s/memory_limit = 128M/memory_limit = 512M/g" /etc/php5/fpm/php.ini
RUN sed -i -e "s/post_max_size = 8M/post_max_size = 100M/g" /etc/php5/fpm/php.ini
RUN sed -i -e "s/upload_max_filesize = 2M/upload_max_filesize = 100M/g" /etc/php5/fpm/php.ini
RUN find /etc/php5/cli/conf.d/ -name "*.ini" -exec sed -i -re 's/^(\s*)#(.*)/\1;\2/g' {} \;
RUN sed -i -e "s/listen = 127.0.0.1:9000/listen = \/var\/run\/php5-fpm.sock/g" /etc/php5/fpm/pool.d/www.conf
RUN sed -i -e "s/;listen.owner = www-data/listen.owner = www-data/g" /etc/php5/fpm/pool.d/www.conf
RUN sed -i -e "s/;listen.group = www-data/listen.group = www-data/g" /etc/php5/fpm/pool.d/www.conf
RUN sed -i -e "s/;listen.mode = www-data/listen.mode = 0660/g" /etc/php5/fpm/pool.d/www.conf

# php5-apc
RUN sed -i '$a apc.shm_size=128M' /etc/php5/conf.d/apc.ini
RUN sed -i '$a apc.include_once_override=0' /etc/php5/conf.d/apc.ini

# php5-xdebug
# @todo this assumes 1.3.3.1 is your host machine, need to abstract out
# in the future
RUN sed -i '$a xdebug.remote_host="1.3.3.1"' /etc/php5/conf.d/xdebug.ini
RUN sed -i '$a xdebug.remote_enable=1' /etc/php5/conf.d/xdebug.ini
RUN sed -i '$a xdebug.remote_port=9000' /etc/php5/conf.d/xdebug.ini
RUN sed -i '$a xdebug.remote_handler="dbgp"' /etc/php5/conf.d/xdebug.ini
RUN sed -i '$a ;remote_autostart causes php-fpm pool to take 4eva to respond on windows' /etc/php5/conf.d/xdebug.ini
RUN sed -i '$a ;xdebug.remote_autostart=1' /etc/php5/conf.d/xdebug.ini

EXPOSE 80
CMD ["/etc/init.d/php5-fpm", "start"]