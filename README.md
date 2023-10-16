# docker-practice
## 駆け出しエンジニアのためのDocker入門

```
docker ps -a
docker run --name asada-container hello-world
docker run --name rmtest --rm hello-world

docker run -it --name mycentos  centos:8 /bin/bash
docker start mycentos
docker ps
docker stop 4dbaaa400851
docker restart mycentos

docker exec -it mycentos /bin/bash
cat /etc/redhat-release
docker exec mycentos cat /etc/redhat-release

docker rm e394e928c4c8
docker rm mycentos -f

docker images
docker rmi b038788ddb22

docker build test
docker images

docker run -it --name mycentos  centos:8 /bin/bash
docker start mycentos
docker cp command/sample.txt mycentos:/opt
docker exec -it mycentos /bin/bash
cd opt
vi container.txt
docker cp mycentos:/opt/container.txt ./sample.txt
```
