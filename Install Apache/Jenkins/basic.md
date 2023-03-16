# Create image and run 

```
docker run -d --name jenkins -p 81:8080 jenkins:2.60.3

```

```

docker run -d --name wordpress -p 80:80 wordpress

docker ps -a
CONTAINER ID   IMAGE            COMMAND                  CREATED              STATUS              PORTS                                              NAMES
3c0975d0c94d   wordpress        "docker-entrypoint.s…"   About a minute ago   Up About a minute   0.0.0.0:80->80/tcp, :::80->80/tcp                  wordpress
6bd010acc659   jenkins:2.60.3   "/bin/tini -- /usr/l…"   4 minutes ago        Up 4 minutes        50000/tcp, 0.0.0.0:81->8080/tcp, :::81->8080/tcp   jenkins

```

If use command for stop

```
docker stop container_id 
```

My application won't work.


