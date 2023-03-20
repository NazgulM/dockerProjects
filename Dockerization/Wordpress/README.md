# Docker

A Dockerfile is a text file that defines a Docker image. You’ll use a Dockerfile to create your own custom Docker image, in other words to define your custom environment to be used in a Docker container.

Docker’s main purpose is to give us run-time environments that we can re-create/reproduce on any machine (that runs Docker). The main advantage is to avoid the situations when we say “it worked on my machine”, because Docker containers will give us the same environment on all machines.

1; Docker containers: containers are runtime environments. You usually run one main process in one Docker container. You can think of this like one Docker container provides one service in your project.

For example you can start one container to be your MySQL database and start another container to be your Wordpress server and connect these containers together to get a Wordpress project setup.

You can start containers to run all the tech you can think of, you can run databases, web servers, web frameworks, test servers, execute big data scripts, work on shell scripts, etc.

2; Docker containers are started by running a Docker image. A Docker image is a pre-built environment for a certain technology or service. A Docker image is not a runtime, it’s rather a collection of files, libraries and configuration files that build up an environment.

The main source of Docker images online is the Docker store. You just need to search for your preferred tech component, pull the image from the store with the docker pull command and you are ready to start up containers.

Containers are started from images with the docker run command. An image, as you’ll see in the videos, is a layered representation of your environment. These layers contain the files and configuration needed by your environment.

Wordpress:

1; Create a vm in digital ocean, ssh root@ip
2; Create Dockerfile

 Every Dockerfile must start with the FROM instruction: what is the base image? In my case, I am using the official WordPress image from Docker Hub (wordpress:latest), but you can use an image from a different registry, such as a registry you manage yourself.

After we get the base image I use the RUN instruction to run a series of commands, just as if it were a Bash script. In this example, I RUN commands to do an apt update and upgrade, install Vim, install wget, and install the MariaDB Client that is needed for the WP-CLI tool.Then I use another RUN instruction again to install WP-CLI just as I did manually in the previous article. I also use this instruction to clean up the /usr/local/etc/php directory by removing php.ini-development and php.ini-production.

Next there is a COPY instruction. Not unlike the cp command, this COPY looks for a php.ini file in the directory where the Dockerfile is located and copies it to /usr/local/etc/php inside of the container.

One final point: I created the php.ini file by going into the WordPress container I customized in the previous article, copied its contents, and saved it locally as php.ini. This way, I know that it is the php.ini file that ships with the WordPress image, but that includes my changes to parameters like upload_max_filesize.

```
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
```

