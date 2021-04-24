# Ubuntu 18.04에 Chrome 설치
크롬 설치를 위한 인증키 등록
```sh
wget -q -O - https://dl-ssl.google.com/linux/linux_signing_key.pub | sudo apt-key add -
```
패키지를 받을 PPA를 sources.list.d에 추가
```sh
sudo sh -c 'echo "deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main" >> /etc/apt/sources.list.d/google.list'
```
PPA로부터 패키지를 받기위하여 패키지 리스트 업데이트
```sh
sudo apt-get update
```
크롬 패키지 설치
```sh
sudo apt-get install google-chrome-stable
```

### optional
패키지 리스트 파일 
```sh
sudo rm -rf /etc/apt/sources.list.d/google.list
```
