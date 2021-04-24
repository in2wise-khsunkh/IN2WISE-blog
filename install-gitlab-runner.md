# Gitlab-Runner
## Gitlab-Runner 설치
```sh
curl -L "https://packages.gitlab.com/install/repositories/runner/gitlab-runner/script.deb.sh" | sudo bash
export GITLAB_RUNNER_DISABLE_SKEL=true; sudo -E apt-get install gitlab-runner
```

## Gitlab-Runner 생성
```sh
sudo gitlab-runner register
```
coordinator URL : (local gitlab - Project - setting - CI/CD - Runners - Expand - 
Specific runners - Set up a specific runner manually - URL)

token : (local gitlab - Project - setting - CI/CD - Runners - Expand - 
Specific runners - Set up a specific runner manually - toekn)

description : (e.g. this is gitlab CICD tutorial)
tags (comma separated) : (e.g. stage, qa, build, deploy)
run untagged builds [true/false] : No (?)
lock the runner to current project [true/false] : true
please enter the executor : docker, shell, virtualbox, docker-ssh+machine, kubernetes, docker-ssh, ssh, docker+machine : shell

###Check installation on local gitlab
local gitlab - Project - setting - CI/CD - Runners - Expand - available specific runners(below Specific runners)
