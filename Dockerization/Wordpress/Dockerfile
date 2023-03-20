# Set the base image
FROM centos:7

# Pre-reqs
RUN yum clean all && \
yum -y update && \
yum -y install httpd mod_rewrite mod_ssl mod_env php php-common php-cli php-mysql mysql-server unzip wget  && \
rm -fr /var/cache/*

# Application install
RUN wget -P /var/www/html https://wordpress.org/latest.zip && \
unzip /var/www/html/latest.zip -d /var/www/html/ && \
rm -fr /var/www/html/latest.zip

RUN cp /var/www/html/wordpress/wp-config-sample.php /var/www/html/wordpress/wp-config.php

# Expose necessary ports
EXPOSE 80