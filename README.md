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

```
