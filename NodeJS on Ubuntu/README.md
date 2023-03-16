# Use Docker with NodeJS Projects

Install Docker

```
sudo yum install -y yum-utils
sudo yum-config-manager \
    --add-repo \
    https://download.docker.com/linux/centos/docker-ce.repo

```

```
sudo systemctl start docker
sudo docker run hello-world

```

Create Dockerfile 

```
vim Dockerfile

```

Create a dockerignore file
We can further optimize our Docker image by avoiding copying some resources into the application. Create a .dockerignore file and paste the following code there

Let’s build our image by running the following command.

```
sudo docker build . -t express-typescript-docker

```

```
sudo docker images
docker run -p 3000:3000 -d express-typescript-docker:latest

```
Notice the -p an option that maps the exposed docker port with our local machine port. In our Dockerfile, we exposed port 3000. And we mapped that same port to our machine.

See the running containers.
Run the following command.

```
docker ps

```
Which should give you the following output

```
ONTAINER ID   IMAGE  COMMAND  CREATED STATUS PORTS   NAMES
  
9be24fc778bb   
express-typescript-docker:latest   
"docker-entrypoint.s…"   
8 seconds ago   
Up 7 seconds   
0.0.0.0:3000->3000/tcp, 
8080/tcp   
eager_bardeen
```

Test the endpoint
Now go to your browser or some HTTP client like Postman and hit the following URL.

```
http://localhost:3000

# Result
{ "message": "Hello World!" }

```

Also, you can see the logs inside the container by running the following command. Get the container_id from docker ps the command we ran earlier.

```
docker logs container_id
Connected successfully on port 3000
{ message: 'Hello World'}

```

Stop the container.
You can stop the running container by running the following command.

```
docker stop container_id

```




