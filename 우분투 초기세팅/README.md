# 우분투 초기 세팅

## apt 최신버전으로 업데이트
```
$ sudo apt update

$ sudo apt upgrade
```

## git 설치
```
$ sudo apt-get install git
```

## curl 설치
```
$ sudo apt install curl

$ curl -V  # 버전 확인
```

## zsh  설정
```
$ sudo apt install zsh

$ chsh -s /usr/bin/zsh  # 권한 변경

$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"

$ vi .zshrc

## 아래 내용으로 수정
ZSH_THEME='rubbyrussell'를
ZSH_THEME='agnoster' 으로 바꿉니다.
```


## deb 파일 설치 방법
```
$ sudo dpkg -i code_1.40.2-1574694120_amd64.deb
```

## apt 자동 삭제
```
$ sudo apt autoremove
```
