# How to modify while my containers are running

1; Delete all running containers:

```
docker rm -f containerId
```

Build an image and run it, whatever inside of my working directory pls copy to /var/www/html

```
docker build -t nurbakar/application:0.0.17 .
docker run -d --name web -v "${PWD}:/var/www/html" -p 80:80 nurbakar/application:0.0.17
```

Now my app is working, and it shows only the Apache server page, for debugging

```
docker exec -it containerID bash
cd /var/www
chmod 777 html
exit 
```

My application shows the simple html page

For changing the content of html I go to the my current directory which is root, not container, change the content of html, if refresh the web page it will show the changing content, so I can do the live changes to my app.
Change the color of background only in the index.html

![text](white.png)

![pink](pink.png)
