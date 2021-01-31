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

- 아래 내용으로 수정
ZSH_THEME='rubbyrussell'를
ZSH_THEME='agnoster' 으로 바꿉니다.

- 쉘 확인하기
$ echo $SHELL

- 글자 깨질경우
sudo apt-get install fonts-powerline
(참고 : https://github.com/powerline/fonts)

※ 우분투 재시작 해야지 적용됨

```


## deb 파일 설치 방법
```
$ sudo dpkg -i code_1.40.2-1574694120_amd64.deb
```

## apt 자동 삭제
```
$ sudo apt autoremove
```

## 우분투 wol 문제
1. 관련 패키지 설치  
$ sudo apt-get install net-tools ethtool wakeonlan

2. 네트워크 카드 이름 확인  
$ ifconfig

3. 수동 세팅 후 정상 동작 확인  
$ sudo ethtool -s [네트워크 카드 이름] wol g
$ sudo ethtool [네트워크 카드 이름]

4. 설정 파일에 관한 내용추가  
$ sudo vi /etc/network/interfaces

    ```
    post-up /sbin/ethtool -s 인터페이스명 wol g

    post-down /sbin/ethtool -s 인터페이스명 wol g 
    ```
