# docker-ml
This repository contains Dockerfile to build MarkLogic images

## Setup
From Docker Machine clone the repo:  
```
git clone https://github.com/rlouapre/docker-ml.git
```
Change working directory to the targetted OS centos/6 or centos/7:  
```
cd docker-ml/$(os-version)
```
Download MarkLogic rpm with curl:
- For CentOS7 use REHL 7
```
curl -k -o MarkLogic.rpm {marklogic-dowload-url}
```
Build Docker Image:  
```
docker build --rm=true -t "centos6-ml" .
```
Run Docker Container named ml from the new Docker Image:  
```
docker run --name ml -d -p 8000:8000 -p 8001:8001 -p 8002:8002 -p 9200:9200 -p 9201:9201 -v /var/lib/docker:/var/opt/MarkLogic centos6-ml
```