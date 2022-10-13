## Creating sample app as container 

### taking code 

```
git clone https://github.com/schoolofdevops/html-sample-app
```
### adding dockerfile 

```
FROM nginx
LABEL name=ashutoshh
COPY html-sample-app /usr/share/nginx/html/
```

### Docker-compose file 

```
version: '3.8'
services:
  ashuapp1:
    image: ashucisco:webappv1  # image i want to build 
    build:  # location & name of dockerfile 
      context: . 
      dockerfile: day4.dockerfile
    container_name: ashuwebc1 # after image build the container i want to create
    ports: # port forwarding 
    - 1234:80 

```

### lets build image and create container -- 

```
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose up -d
[+] Running 0/1
 ⠿ ashuapp1 Warning                                                                         3.0s
[+] Building 2.1s (8/8) FINISHED                                                                 
 => [internal] load build definition from day4app.dockerfile                                0.0s
 => => transferring dockerfile: 120B                                                        0.0s
 => [internal] load .dockerignore                                                           0.0s
 => => transferring context: 2B                                                             0.0s
 => [internal] load metadata for docker.io/library/nginx:latest                             1.8s
 => [auth] library/nginx:pull token for registry-1.docker.io                                0.0s
 => [internal] load build context                                                           0.1s
 => => transferring context: 3.55MB                                                         0.0s
 => CACHED [1/2] FROM docker.io/library/nginx@sha256:2f770d2fe27bc85f68fd7fe6a63900ef7076b  0.0s
 => [2/2] COPY html-sample-app /usr/share/nginx/html/                                       0.1s
 => exporting to image                                                                      0.1s
 => => exporting layers                                                                     0.0s
 => => writing image sha256:c8ae9279394921869ea3a09442c0584270854fa2db91c0bd541ba5003d1bd4  0.0s
 => => naming to docker.io/library/ashucisco:webappv1                                       0.0s
[+] Running 2/2
 ⠿ Network ashu-container-apps_default  Created                                             0.0s
 ⠿ Container ashuwebc1                  Started                                             0.7s
[ashu@ip-172-31-44-55 ashu-container-apps]$ 
```

### checking 

```
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose  images
Container           Repository          Tag                 Image Id            Size
ashuwebc1           ashucisco           webappv1            c8ae92793949        145MB
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose  ps
NAME                COMMAND                  SERVICE             STATUS              PORTS
ashuwebc1           "/docker-entrypoint.…"   ashuapp1            running             0.0.0.0:1234->80/tcp, :::1234->80/tcp
[ashu@ip-172-31-44-55 ashu-container-apps]$ 
```

### compsoe commands 

```
 299  docker-compose  -f  docker-compose1.yaml  ps 
  300  docker-compose  -f  docker-compose1.yaml  down 
  301  docker-compose  -f  docker-compose1.yaml  up -d
  302  docker-compose  -f  docker-compose1.yaml  ps
  303  docker-compose  -f  docker-compose1.yaml  stop 
  304  history 
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose ps 
NAME                COMMAND                  SERVICE             STATUS              PORTS
ashuwebc1           "/docker-entrypoint.…"   ashuapp1            exited (0)          
[ashu@ip-172-31-44-55 ashu-container-apps]$ docker-compose start
[+] Running 1/1
 ⠿ Container ashuwebc1  Started                                                             0.5s
[ashu@ip-172-31-44-55 ashu-container-
```

### lets automate entire container images builds and test process using CI tool jenkins

<img src="j.png">

