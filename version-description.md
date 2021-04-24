# docker version
1. Docker Engine
> 어플리케이션을 컨테이너화 할 수 있는 기술
ex)
```sh
sudo docker run --detach \
  --hostname gitlab.example.com \
  --publish 443:443 --publish 80:80 --publish 22:22 \
  --name gitlab \
  --restart always \
  --volume $GITLAB_HOME/config:/etc/gitlab \
  --volume $GITLAB_HOME/logs:/var/log/gitlab \
  --volume $GITLAB_HOME/data:/var/opt/gitlab \
  gitlab/gitlab-ee:latest
```
2. Docker Compose
> 컨테이너 별로 docker run ...을 수행하지 않고 docker-compose.yml을 사용하여 다수의 컨테이너를 동시에 실행시킬 수 있음
> 단, 같은 호스트에서만 컨테이너가 실행됨
3. Docker Swarm
> 여러 호스트에서 컨테이너를 실행하고 연결하는 기능을 수행. 컨테이너 관리, 스케쥴링, 고장에 따른 자동 실행, 네트워킹 등을 제공
> 도커 기반 오케스트레이션 도구이며, 쿠버네티스와 그 목적이 같음.

# Kubernetes
1. Lightweight Kubernetes
1개의 Master와 2개 이상의 Node로 구성되는 Kubernestes와 달리 하나의 호스트에서 Master와 Node를 생성할 수 있음
실험, 개발, 테스트 등에 활용
  1. k3s
    + RANCHER 진영
  2. Minikube 
    + Kubernetes 진영
  3. MicroK8s
    + CANONICAL(Ubuntu) 진영
2. K8S
  + kubeadm : 클러스터를 부트스트랩하는 명령 
  + kubelet : 클러스터의 모든 머신에서 실행되는 파드와 컨테이너 시작과 같은 작업을 수행하는 컴포넌트
  + kubectl : 클러스터와 통신하기 위한 커맨드 라인 유틸리티이다.
