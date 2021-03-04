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

## zsh & oh-my-zsh  설치
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

## docky 설치(메뉴바)
- 파일로 설치
  - 설치
  
    ```
    $ mkdir ~/tmp

    $ cd ~/tmp

    $ wget http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-sharp2/libgconf2.0-cil_2.24.2-4_all.deb

    $ wget http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/multiarch-support_2.27-3ubuntu1_amd64.deb

    $ wget http://archive.ubuntu.com/ubuntu/pool/universe/libg/libgnome-keyring/libgnome-keyring-common_3.12.0-1build1_all.deb

    $ wget http://archive.ubuntu.com/ubuntu/pool/universe/libg/libgnome-keyring/libgnome-keyring0_3.12.0-1build1_amd64.deb

    $ wget http://archive.ubuntu.com/ubuntu/pool/universe/g/gnome-keyring-sharp/libgnome-keyring1.0-cil_1.0.0-5_amd64.deb

    $ sudo apt-get install ./*.deb

    $ wget http://archive.ubuntu.com/ubuntu/pool/universe/d/docky/docky_2.2.1.1-1_all.deb

    $ sudo apt-get install ./docky_2.2.1.1-1_all.deb
    ```
  - 삭제
- 패키지 설치 (2021-02-02 기준으로 작동안됨)
  - 설치

      ```
      $ sudo add-apt-repository ppa:docky-core/stable

      $ sudo apt-get update

      $ sudo apt-get install docky
      ```
  - 삭제

      ```
      - 설치된거 삭제
      $ sudo apt-get remove docky

      - repository 삭제
      $ sudo add-apt-repository --remove ppa:docky-core/stable
      ```

## clamav 설치 (백신)
- 패키지 설치
  
  ```
    $ sudo apt-get install clamav
  ```

- 데이터베이스 업데이트
  
  ```
    $ sudo freshclam
  ```

- 검사하기

  ```
    # home 디렉토리 하위 파일 검사
    $ sudo clamscan -r /home

    # 검사해서 감염된 파일 옮기기
    $ sudo clamscan -r /home --move=/virus
  ```
- 에러
  
  - 에러내용 1
    ```
    
    ERROR: /var/log/clamav/freshclam.log is locked by another process
    ERROR: Problem with internal logger (UpdateLogFile = /var/log/clamav/freshclam.log).
    ERROR: initialize: libfreshclam init failed.
    ERROR: Initialization error!

    - 해결방법
      $ sudo ps aux | grep fresh  #프로세스 확인
      $ sudo killall freshclam    #프로세스 죽이기
    ```
- 참고
  - https://www.clamav.net/ : 공식 홈페이지

# 각종 명령어

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


## repository 추가, 삭제 명령어
```
- repository 추가시
$ sudo add-apt-repository ppa:docky-core/ppa

- repository 삭제시
$ sudo add-apt-repository --remove ppa:docky-core/ppa
```

## 압축 명령어
- tar 압축풀기
    
  ```
  $ sudo tar -xvf [파일명.tar]
  ```
- tar.xz 압축풀기
    
  ```
  $ sudo tar Jxvf 압축파일.tar.xz
  ```
- tar.gz 압축풀기
  
  ```
  $ sudo tar -zxvf [파일명.tar.gz]
  ```
- tar로 압축하기
  ```
  $ sudo tar -cvf [파일명.tar] [폴더명]
  ```
- tar.gz로 합축하기
  ```
  $ sudo tar -zcvf [파일명.tar.gz] [폴더명]
  ```