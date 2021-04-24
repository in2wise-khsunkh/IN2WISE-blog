# Docker Engine 기반 Gitlab 설치
## Bind Mount를 사용한 데이터 저장 설정
별도의 볼륨 생성 없이 데이터를 저장할 수 있음
컨테이너가 삭제되지 않는 한 데이터의 저장 상태를 유지할 수 있음
컨테이너가 삭제된 후 컨테이너 재생성 시 데이터 손실됨
```sh
export GITLAB_HOME=/srv/gitlab

export GITLAB_HOME=$HOME/gitlab

sudo docker run --detach \
  --hostname gitlab.example.com \
  --publish 443:443 --publish 80:80 --publish 22:22 \
  --env GITLAB_OMNIBUS_CONFIG="external_url 'http://gitlab.company.com'" \
  --name gitlab \
  --restart always \
  --volume $GITLAB_HOME/config:/etc/gitlab \
  --volume $GITLAB_HOME/logs:/var/log/gitlab \
  --volume $GITLAB_HOME/data:/var/opt/gitlab \
  gitlab/gitlab-ee:latest
```

## Volume을 사용한 데이터 저장 설정별
Bind Mount와 달리 별도의 볼륨 생성이 필요함
컨테이너가 삭제되더라도 Docker Engine이 Volume을 관리하고 있음
컨테이너 재생성 시 데이터 복구 가능
단, 볼륨 삭제 시 복구 불가능
```sh
sudo docker volume create --name config
sudo docker volume create --name logs
sudo docker volume create --name data
  
sudo docker run --detach \
  --hostname gitlab.example.com \
  --publish 443:443 --publish 80:80 --publish 22:22 \
  --env GITLAB_OMNIBUS_CONFIG="external_url 'http://gitlab.company.com'" \
  --name gitlab \
  --restart always \
  --volume config:/etc/gitlab \
  --volume logs:/var/log/gitlab \
  --volume data:/var/opt/gitlab \
  gitlab/gitlab-ee:latest
```

### option
--hostname <홈페이지 이름?>

--env GITLAB_OMNIBUS_CONFIG="external_url 'http://gitlab.company.com'" \ -> http://<ip주소 또는 도메인>을 외부 URL로하는 OMNIBUS 설정 값으로 환경을 

--publish <외부port:내부port>

--restart always -> 컴퓨터 재부팅시 자동 실행

--volume <Host 경로:Container 경로>
--volume <Volume 명:Container 경로>
