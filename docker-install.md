## Install OS
Ubuntu 18.04 install

## 업데이트 및 업그레이드 수행
```sh
sudo apt-get update
sudo apt-get upgrade
```

## 구 버전 Docker 삭제
```sh
sudo apt-get remove docker docker-engine docker.io containerd runc
```

## Docker 설치

#### Reposigory를 사용한 설치

###### Repository 설정
 - apt 패키지 업데이트 및 HTTPS를 통해 Repository를 사용하기 위한 패키지 설치
```sh
sudo apt-get update

sudo apt-get install \
  apt-transport-https \
  ca-certificates \
  curl \
  gnupg \
  lsb-release
```

 - Docker 공식 GPG Key 추가
```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg

```
 - x86_64 / amd64 경우
```sh
echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

###### Docker Engine 설치
```sh
sudo apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io
```
 - 다른 버전의 도커를 설치할 경우
```sh
apt-cache madison docker-ce
```
<package_name> | <version_string> | < ? > | < ? > | < ? > | < ? >
```sh
sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```

###### (Optional) Verify the DOcker Engine
```sh
sudo docker run hello-world
```

#### Package를 사용한 설치
https://download.docker.com/linux/ubuntu/dists/ 에서 OS 버전 선택 후 pool/stable에서 환경 프로세서에 따라 amd64, arm64 armhf 등 중 선택

설치를 원하는 Docker Engine에 해당하는 .deb 파일을 다운로드
ex) docker-ce_20.10.6~3-0~ubuntu-bionic_amd64.deb 을 ~/Downloads 에 저장

```sh
sudo dpkg -i /path/to/package.deb
```
ex) sudo dpkg -i ~/Downloads/docker-ce_20.10.6~3-0~ubuntu-bionic_amd64.deb

###### (Optional) Verify the DOcker Engine
```sh
sudo docker run hello-world
```
