# Make new project

1. Create folder dockerApache

```
mkdir dockerApache
cd dockerApache

```

2. Use the echo command as follows to create a new index.html for our project:

```
echo 'Docker Apache static site by nixCraft' > index.html

```

3. Make a new Dockerfile using a text editor such as nano command or vim command:

```
vim Dockerfile

```

4. Append the following config for your Amazon Linux container:

```
FROM rockylinux/rockylinux:latest
 
MAINTAINER nixCraft
LABEL Remarks="RockyLinux test image for installing static webpage with Apache2"
 
# Install apache2 with less
RUN yum -y update && \
yum -y install httpd && \
yum clean all
 
# Sample index.html for test 
COPY index.html /var/www/html/index.html
 
# Port and set entry point for container 
EXPOSE 80
ENTRYPOINT /usr/sbin/httpd -DFOREGROUND

```

5. Build it:

```
sudo docker build -t staticsite01 .

```

6. Output:

```
httpd-2.4.37-51.module+el8.7.0+1155+5163394a.1.x86_64                         
  httpd-filesystem-2.4.37-51.module+el8.7.0+1155+5163394a.1.noarch              
  httpd-tools-2.4.37-51.module+el8.7.0+1155+5163394a.1.x86_64                   
  mailcap-2.1.48-3.el8.noarch                                                   
  mod_http2-1.15.7-5.module+el8.6.0+823+f143cee1.x86_64                         
  rocky-logos-httpd-86.3-1.el8.noarch                                           

Complete!
25 files removed
Removing intermediate container 1423d76a13e8
 —> b0a30d8a4f4b
Step 5/7 : COPY index.html /var/www/html/index.html
 —> a127c2aa7b17
Step 6/7 : EXPOSE 80
 —> Running in 2966dbcde864
Removing intermediate container 2966dbcde864
 —> 5872bfacc187
Step 7/7 : ENTRYPOINT /usr/sbin/httpd -DFOREGROUND
 —> Running in 1b7930df36df
Removing intermediate container 1b7930df36df
 —> 3bc29b58b2b4
Successfully built 3bc29b58b2b4
Successfully tagged staticsite01:latest

```

7. List images:

```
sudo docker images

```

```
REPOSITORY              TAG       IMAGE ID       CREATED          SIZE
staticsite01            latest    3bc29b58b2b4   43 seconds ago   415MB
mysql                   latest    4073e6a6f542   7 days ago       530MB
nginx                   latest    904b8cb13b93   2 weeks ago      142MB
rockylinux/rockylinux   latest    523ffac7fb2e   8 months ago     196MB

```

```
sudo docker run -d -p 80:80 --name staticsite01 staticsite01
sudo docker ps
sudo docker port staticsite01
curl 127.0.0.1:80

```
