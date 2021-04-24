## Dockerfile 만들기
vi Dockerfile
```sh
FROM ubuntu:18.04
RUN apt-get -y update
RUN apt-get -y install apache2
EXPOSE 80
CMD apachectl -D FOREGROUND
```
FROM ubuntu:18.04 - 18.04 버전의 Ubuntu를 기반으로 도커 생성
RUN apt-get -y update - 업데이트
RUN apt-get -y install apache2 - apache2 설치
EXPOSE 80 - 80번 포트 노출
CMD apachectl -D FOREGROUND - apache 컨트롤 명령어 실행 (FOREGROUND라는 명칭으로)
```sh
sudo docker build -t custom_image .
```
sudo docker build <src_path(files location or URL)>
sudo docker build -t <DockerName>:<Tag> <src_path(files location or URL)>
ex) $ docker build http://server/context.tar.gz # http://server의 context.tar.gz 파일을 사용하여 빌드

## 생성된 Docker Image 확인
```sh
sudo docker image list -a
```
>```
>REPOSITORY     TAG       IMAGE ID       CREATED         SIZE
>custom_image   latest    30c2abab6e3e   4 minutes ago   196MB
>ubuntu         18.04     4eb8f7c43909   16 hours ago    63.1MB
>```
docker build를 통해 생성된 custom_image와 custom_image를 생성하는데 사용된 ubuntu docker image가 저장된 것을 확인 할 수 있음

## 생성된 Docker Image의 정상 동작 확인
생성된 Docker Image를 사용하여 container 실행
```sh
sudo docker run -dit -p 80:80 custom_image
```
포트 개방을 단순히 "EXPOSE 80"으로 수행하였기 때문에 -p XXXX:80 옵션이 없으면 동작하지 않음.
Explore / Chrome 을 통해서 localhost 접속 시 Apache2 Ubuntu Default Page를 확인할 수 있음.
