# Set the base image
FROM centos:7

# Pre-reqs
RUN yum clean all && \
yum -y update && \
yum -y install httpd mod_rewrite mod_ssl mod_env php php-common php-cli php-mysql mysql-server unzip wget  && \
rm -fr /var/cache/*
FROM centos:7
RUN yum install -y httpd \
    && yum install -y wget \ 
    && yum install -y unzip \
    && yum install -y https://rpms.remirepo.net/enterprise/remi-release-7.rpm \
    && yum-config-manager --enable remi-php74 \
    && yum install -y epel-release \
    && yum install -y php \
    && yum install -y php-mysql
ADD https://wordpress.org/latest.tar.gz .
RUN tar -xf latest.tar.gz -C /var/www/html/ && \
    mv /var/www/html/wordpress/* /var/www/html/ && \
    chown -R apache:apache /var/www/html/
CMD ["/usr/sbin/httpd","-D","FOREGROUND"]
EXPOSE 80