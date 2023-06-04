# How to Deploy multiple application Containers using Docker Compose On Amazon EC2

Docker Compose:
docker Compose is a tool that was developed to help define and share multi container applications. With Compose we can create the YAML file to define the services with a single command we can spin everything up and can tears down.

Docker Compose is used for running multiple containers as a single service. Each of containers here runs in isolation but can interact with each other when required.

If you have an application that requires NGINX server and REdis database, can create Docker Compose File that can run both containers as a service without the need to start each one separately.

```
Step 1: Setting up EC2 Instance:
We will first create an AWS Instance (Amazon Linux) free tier eligible using the AWS console.

Step 2: Installing Docker and Docker Compose:
Apply pending updates using the yum command:
sudo yum update

Search for the Docker package:
sudo yum search docker 

Get version information:
sudo yum info docker

install Docker:
sudo yum install docker

Add group membership for the default ec2-user so you can run all docker commands without using the sudo command:
sudo usermod -a -G docker ec2-user

Enable docker service at AMI boot time
sudo systemctl enable docker. service

Start the Docker service:
sudo systemctl start docker. service

To verify the docker service status on your AMI instance, run
sudo systemctl status docker. service

To download and install Compose standalone, run:
sudo curl -SL https://github.com/docker/compose/releases/download/v2.17.2/docker-compose-linux-x86_64 -o /usr/local/bin/docker-compose

Apply executable permissions to the standalone binary in the target path for the installation.
sudo chmod +x /usr/local/bin/docker-compose