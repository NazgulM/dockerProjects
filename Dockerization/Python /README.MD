# Install the Kubernetes using Dockerfile

```
FROM centos:7
RUN cat <<EOF > /etc/yum.repos.d/kubernetes.repo
[kubernetes]
name=Kubernetes
baseurl=https://packages.cloud.google.com/yum/repos/kubernetes-el7-x86_64
enabled=1
gpgcheck=1
repo_gpgcheck=1
gpgkey=https://packages.cloud.google.com/yum/doc/yum-key.gpg https://packages.cloud.google.com/yum/doc/rpm-package-key.gpg
EOF
RUN yum install kubectl -y
```

Docker run and check if it's my image is ready:

```
docker build -t kubectl:1.0. .
docker images
kubectl                1.0       aa7caf847446   37 seconds ago   459MB
nurbakar/application   0.0.17    22d44d2b6260   4 hours ago      537MB 
docker run kubectl:1.0 kubectl
```

This image has kubectl installed.

1; Dockerization of python app (flask), every app needs some code and libraries (dependencies)
Basic Hello world app:
Create app.py file and input this code:

```
from flask import Flask

app = Flask(__name__)

@app.route('/')
def hello_world():
    return 'Hello, World!'

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0')
```

2; Create requirements.txt (what kind of dependencies should DevOps install)

```
Flask==2.0.1
```

3; Create Dockerfile

```
FROM python:3.9
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
EXPOSE 5000
CMD ["python","app.py"]

```

Base image: python:3.9
Everything needs to be done in /app directory, WORKDIR - cd
COPY  . . - everything from my computer to my current directory, if don't copy next command will fail.
Install dependencies from what kind of requirements

Next:

```
docker build -t python:1.0 .
docker images
python                 1.0       d2518b9cb600   29 seconds ago   919MB
kubectl                1.0       aa7caf847446   42 minutes ago   459MB
docker run -d --name python -p 80:5000 python:1.0
docker ps

df982093ea43   python:1.0   "python app.py"   4 seconds ago   Up 4 seconds   0.0.0.0:80->5000/tcp, :::80->5000/tcp   python
```

![python](python.png)
