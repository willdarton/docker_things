FROM hypriot/rpi-node

MAINTAINER Will Darton <willdarton@gmail.com>

RUN \
  apt-get update && \
  apt-get install -y nginx php5-fpm && \
  apt-get autoclean && apt-get clean && \
  rm -rf /var/lib/apt/lists/* && \
  echo "\ndaemon off;" >> /etc/nginx/nginx.conf && \
  chown -R www-data:www-data /var/lib/nginx

ADD default /etc/nginx/sites-enabled/default

# Define mountable directories.
VOLUME ["/etc/nginx/certs", "/etc/nginx/conf.d", "/var/log/nginx", "/var/www/html"]

# Define working directory.
WORKDIR /etc/nginx

# Expose ports.
EXPOSE 80
EXPOSE 443

# Define default command.
CMD /usr/sbin/php5-fpm -c /etc/php5/fpm && nginx

