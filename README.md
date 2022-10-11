## CLOUD -- Developer can use ..?

### Day 2 agenda 

<img src="ag.png">

### PAAS. 

<img src="pass.png">

### AWS PAAS 

<img src="awspaas.png">

### container services 

<img src="containers.png">

## vm vs containers 

<img src="cont1.png">

### container runtimes 

<img src="cr.png">

### Connecting to docker daemon 

```
[ashu@ip-172-31-44-55 ~]$ docker  version 
Client:
 Version:           20.10.17
 API version:       1.41
 Go version:        go1.18.3
 Git commit:        100c701
 Built:             Thu Jun 16 20:08:47 2022
 OS/Arch:           linux/amd64
 Context:           default
 Experimental:      true
Got permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.24/version": dial unix /var/run/docker.sock: connect: permission denied
[ashu@ip-172-31-44-55 ~]$ 

```

### deploy sample app in container 

```
  3  git clone https://github.com/yenchiah/project-website-template.git
    4  ls
    5  mv project-website-template/  ashuapp
    6  ls
    7  pwd
    8  docker run -itd --name ashuc1  -p 1234:80 -v /home/ashu/ashuapp:/usr/share/nginx/html/ nginx 
    9  docker  ps
   10  docker stats
   11  history 
   12  docker ps
   13  docker stats

```

### Containers vs beanstalk 

<img src="bean.png">

### CLoud native serverless computing 

<img src="serverless.png">

### AWS lambda function -- using container concept in the backend 

<img src="lambda.png">

### write code for application but still provision cloud resources manually 

<img src="res.png">

### IAC

<img src="iac.png">

### Info about terraform 

<img src="terraform.png">

### terraform workplan 

<img src="plan.png">

### terraform installed on Mac 

```
fire@ashutoshhs-MacBook-Air Desktop % ./terraform version 
Terraform v1.3.2
on darwin_amd64
fire@ashutoshhs-MacBook-Air Desktop % sudo mv terraform  /usr/local/bin 
Password:
fire@ashutoshhs-MacBook-Air Desktop % 
fire@ashutoshhs-MacBook-Air Desktop % terraform version 
Terraform v1.3.2
on darwin_amd64
fire@ashutoshhs-MacBook-Air Desktop % 


```

### Understanding terraform connection 

<img src="terraformc.png">

### Terraform sample script 

```
provider "aws" {
    region = "ap-south-1" # region name -- mumbai 
    # we will use api keys of aws cloud 
    access_key = ""
    secret_key =  ""  
}

# planning resources in aws cloud 
# aws_instance is a module we are using 
resource "aws_instance" "ashuvm1" {
    ami = "ami-01216e7612243e0ef"
    instance_type = "t2.micro"
    key_name = "ashu-private-key"
    tags = {
      "Name" = "ashuvm-by-terraform"
    }
  
}
```


