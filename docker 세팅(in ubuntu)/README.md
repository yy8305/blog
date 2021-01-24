# Docker repository로 설치

## 오래된 버전 삭제

```
$ sudo apt-get remove docker docker-engine docker.io containerd runc
```

## docker 저장소 설치

```
$ sudo apt-get update

$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg-agent \
    software-properties-common
```

## docker 공식 GPG키 추가
```
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -

```

## 키확인 
```
$ sudo apt-key fingerprint 0EBFCD88
```

## repository 추가
```
$ sudo add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
   $(lsb_release -cs) \
   stable"
```

## docker engine 설치
```
$ sudo apt-get update

$ sudo apt-get install docker-ce docker-ce-cli containerd.io
```

## 특정 버전의 Docker engine 설치
```
- 저장소에서 사용 가능한 버전 확인
$ apt-cache madison docker-ce

- 원하는 버전으로 설치
$ sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io
```

## docker 실행 확인하기
```
$ sudo docker run hello-world
```

## docker engine 제거
```
- 패키지 제거
$ sudo apt-get purge docker-ce docker-ce-cli containerd.io

- 컨테이너 볼륨 제거
$ sudo rm -rf /var/lib/docker
```

# repository로 설치시 docker-engine 업그레이드 방법
```
$ sudo apt-get update

업데이트후 설치 지침대로 다시 설치 (라고 공식 홈페이지에 나와있음)
```

# 패키지 파일로 설치
1. https://download.docker.com/linux/ubuntu/dists/ 에서 우분투용 파일(.deb) 설치

2. 패키지 설치
```
$ sudo dpkg -i /path/to/package.deb
```

3. 설치 확인
```
$ sudo docker run hello-world
```

# 참고 url
- https://docs.docker.com/engine/install/ubuntu/
