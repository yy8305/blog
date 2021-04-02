# Overview

m1 mac에서 개발자가 사용할 프로그램에 대해 기술합니다.

## 카카오톡 (m1 미지원)

- 아직까진 국룰이라 설치

- 앱스토어에서 다운로드

- 다운로드시 rosetta 알림이 떠서 같이 설치 가능

- 2021-04-03 기준으로 아직까진 apple m1 지원 안하는듯

## vscode

- [vscode 홈페이지](https://code.visualstudio.com) 접속 -> 아래 내리다 보면 여러 버전들이 나와 있는데 거기서 apple m1 버전 설치

- shell 에서 명령어로 입력하고 싶을 경우

    1. vscode 실행
    
    2.  command + shift + p
    
    3. shell 입력

    4. shell command: install 'code' command in path 선택
    
    5. 터미널, vscode 모두 종료

    6. 터미널 실행해서 원하는 경로에서 code ./ 입력

## iterm2

- [홈페이지](https://iterm2.com/downloads.html)에 접속해서 최신버전으로 다운로드

## Oh my zsh

- 설치전 iterm2, zsh 설치

- shell command 에서 입력  

    ```
    $ sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
    ```

- 개발자 답게 쉘 설정

    ```
    $ vi ~/.zshrc

    - 아래 내용으로 수정
    ZSH_THEME='rubbyrussell'를
    ZSH_THEME='agnoster' 으로 바꿉니다.
    ```

    - font 깨짐 해결

        - 터미널에서 아래 명령어 입력

            ```
            $ git clone https://github.com/powerline/fonts.git --depth=1
            $ cd fonts
            $ ./install.sh
            $ cd ..
            $ rm -rf fonts
            ```

        - iterm2 설정 페이지( command + , )

            - theme는 solarized dark 로 : Preference > Profile > Color > Color Preset > Solarized dark
            
            - font는 Inconsolata for Powerline 으로

## source tree (m1 지원 안함)

- [홈페이지](https://www.sourcetreeapp.com)에서 다운로드

- 현재 실행은 되나 m1 지원 안함

## homebrew

- 현재 m1 지원함

- [홈페이지](https://brew.sh)에서 명령어 복사 & 다운로드

    ```
    $ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
    ```

- zsh 일경우 경로 설정

    ```
    $ echo 'eval $(/opt/homebrew/bin/brew shellenv)' >> ~/.zprofile

    $ eval $(/opt/homebrew/bin/brew shellenv)
    ```

- 실행 확인하기

```
$ which brew : 경로확인

$ brew --version : 버전확인
```

## go 언어 설치

- 자동으로 arm64-bigsur 패키지로 설치됨

- 터미널에서 실행

    ```
    $ brew install go
    ```
# 참고 

- https://www.44bits.io/ko/post/setup-apple-silicon-m1-for-developers