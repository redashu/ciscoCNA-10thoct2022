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



