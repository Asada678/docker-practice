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

docker exec -it mycentos /bin/bash
cat /etc/redhat-release
docker ps
docker logs mycentos

docker inspect mycentos

docker pull php:8.0

docker commit mycentos asada0923/asada-centos:v1

docker push asada0923/asada-centos:v1

docker pull mongo-express
docker history mongo-express:latest
```

### Dockerコンテナのストレージ
- ホストマシンのディスクに書き込む
- 共有しているホストのマシンにもデータを書き込める
```
docker run -v ホストのパス:コンテナのパス イメージ名

docker run --name mynginx -p 8080:80 nginx:1.16
docker ps -a
docker rm mynginx

docker run -v ./test/:/usr/share/nginx/html --name mynginx -p 8080:80 nginx:1.16
# 別タブ 
docker exec -it mynginx /bin/bash
cd /usr/share/nginx/html
cat index.html
```
- 本番環境では
  - サーバ個々に状態を持たない設計をする
  - Aurora
    - 状態を持つDBサーバはAurora一つにする
  - ハイスペックなDBサーバ一つを用意して、他のコンテナと連携する

###　Dockerfile
- Dockerイメージのコード化
```
RUN：Dockerfile→イメージ
CMD：イメージ→コンテナ
```
- RUNの数だけレイヤが作成される

```
docker build -t dockerfile-run-nginx run
docker images
# -d はバックグラウンド起動
docker run -d -p 8081:80 --name dockerfile-run-nginx dockerfile-run-nginx
```

```
COPY：推奨、余計な機能があるより安全
ADD：機能が多い、圧縮ファイルも扱える
```

```
docker build -t dockerfile-copy-nginx copy
docker run -d -p 8082:80 --name dockerfile-copy-nginx  dockerfile-copy-nginx
docker ps
```

### 環境変数
```
docker build -t dockerfile-env-nginx env
docker run -d -p 8083:80 --name dockerfile-env-nginx dockerfile-env-nginx
```

### MariaDBイメージ
```
docker build -t mymariadb mariadb
docker images
docker run -d --name mymariadb mymariadb

```