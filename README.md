##  Micro-services and its deployment using COntainers & kubernetes 

### Microservices planning and deployment 

<img src="micro.png">

### microservices & Containers 

<img src="cont.png">

### APPlication containerization 

<img src="appcont.png">

### CNA along with Containerization --  standard -- OCI 

<img src="oci.png">

### Link for OCI 

[click_here](https://opencontainers.org/)

## Taking sample UI app -- hosting into container 

### take app code 

```
  28  mkdir  myapps 
   29  ls
   30  pwd
   31  ls
   32  git clone https://github.com/ShaifArfan/one-page-website-html-css-project.git
   33  history 
[ashu@ip-172-31-44-55 myapps]$ ls
one-page-website-html-css-project
[ashu@ip-172-31-44-55 myapps]$ ls
ui-app
```

### add any container image building tool to build image -- 

### Dockerfile 

```
FROM nginx 
# this is pre-defined docker image by docker 
LABEL name=ashutoshh
LABEL email=ashutoshh@linux.com 
# just to share image creator info for help purpose 
COPY ui-app /usr/share/nginx/html/
# copy code to nginx app server 
```

### lets build image 

```
[ashu@ip-172-31-44-55 myapps]$ ls
Dockerfile  ui-app
[ashu@ip-172-31-44-55 myapps]$ docker  build -t  ashuapp:v1  . 
Sending build context to Docker daemon  794.1kB
Step 1/4 : FROM nginx
 ---> 51086ed63d8c
Step 2/4 : LABEL name=ashutoshh
 ---> Running in 348d411b6312
Removing intermediate container 348d411b6312
 ---> b28c6f4f1536
Step 3/4 : LABEL email=ashutoshh@linux.com
 ---> Running in 6e763d8be3cc
Removing intermediate container 6e763d8be3cc
 ---> 4593c46a2053
Step 4/4 : COPY ui-app /usr/share/nginx/html/
 ---> af9e6784238e
Successfully built af9e6784238e
Successfully tagged ashuapp:v1
```

### checking images 

```
[ashu@ip-172-31-44-55 myapps]$ docker  images
REPOSITORY   TAG       IMAGE ID       CREATED          SIZE
ashuapp      v1        af9e6784238e   19 seconds ago   142MB
nginx        latest    51086ed63d8c   6 days ago       142MB
[ashu@ip-172-31-44-55 myapps]$ 
```

### creating container 

```
[ashu@ip-172-31-44-55 myapps]$ docker run -d --name ashuapp1 -p 1234:80  ashuapp:v1 
f45b637b3ded26398eef84f04886be8080b4375a35d108207c9e5ef053e78ec2
[ashu@ip-172-31-44-55 myapps]$ docker  ps
CONTAINER ID   IMAGE        COMMAND                  CREATED         STATUS         PORTS                                   NAMES
f45b637b3ded   ashuapp:v1   "/docker-entrypoint.…"   3 seconds ago   Up 2 seconds   0.0.0.0:1234->80/tcp, :::1234->80/tcp   ashuapp1
[ashu@ip-172-31-44-55 myapps]$ 

```

### Scripting docker steps 

<img src="compose.png">

### running compose 

```
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose  up -d
[+] Running 2/2
 ⠿ Network ashu-container-apps_default  Created                                   0.1s
 ⠿ Container ashuc1                     Started                                   0.7s
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose  ps
NAME                COMMAND                  SERVICE             STATUS              PORTS
ashuc1              "/docker-entrypoint.…"   ashu-ui-app         running             0.0.0.0:1234->80/tcp, :::1234->80/tcp
[ashu@ip-172-31-44-55 ashu-container-apps]$ 


```

### to destroy all 

```
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose  up -d
[+] Running 2/2
 ⠿ Network ashu-container-apps_default  Created                                   0.1s
 ⠿ Container ashuc1                     Started                                   0.7s
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose  ps
NAME                COMMAND                  SERVICE             STATUS              PORTS
ashuc1              "/docker-entrypoint.…"   ashu-ui-app         running             0.0.0.0:1234->80/tcp, :::1234->80/tcp
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose  down 
[+] Running 2/2
 ⠿ Container ashuc1                     Removed                                                  0.8s
 ⠿ Network ashu-container-apps_default  Removed                                                  0.1s
[ashu@ip-172-31-44-55 ashu-container-apps]$ 

```
### SOme standards 

<img src="std.png">

### Deploying containers based application in Distributed environment is having some known issues 

<img src="prob.png">

## Introduction to k8s 

<img src="k8s.png">

### k8s on cloud 

<img src="k8scloud.png">

### k8s benefits on cloud 

<img src="benefit.png">

### k8s client 

<img src="client.png">

### checking client 

```
[ashu@ip-172-31-44-55 ashu-container-apps]$ 
[ashu@ip-172-31-44-55 ashu-container-apps]$ kubectl  version --client 
Client Version: version.Info{Major:"1", Minor:"23", GitVersion:"v1.23.6", GitCommit:"ad3338546da947756e8a88aa6822e9c11e7eac22", GitTreeState:"clean", BuildDate:"2022-04-14T08:49:13Z", GoVersion:"go1.17.9", Compiler:"gc", Platform:"linux/amd64"}
[ashu@ip-172-31-44-55 ashu-container-apps]$ 

```




