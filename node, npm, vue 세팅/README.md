# node, npm, vue 세팅

## node, npm 설치 (in Windows)
- 아래정보대로 접속해서 lts 버전 다운로드

    ```
    홈페이지 : https://nodejs.org/en/
    버전 : lts 버전
    ```

- node, npm 버전 확인 (in command)

    ```
    node -v
    npm -v
    ```

## node 업그레이드 (in Windows)
- 위에 설치 방법 다시 진행

## node 업그레이드 (in Ubuntu)

    ```
    $ node -v
    $ npm cache clean -f
    $ npm install -g n
    $ n lts

    ※ 윈도우에서 진행해봤는데 저는 에러 나네요..(아래 에러 내용)
    npm ERR! code EBADPLATFORM
    npm ERR! notsup Unsupported platform for n@7.0.1: wanted {"os":"!win32"} (current: {"os":"win32","arch":"x64"})
    npm ERR! notsup Valid OS:    !win32
    npm ERR! notsup Valid Arch:  undefined
    npm ERR! notsup Actual OS:   win32
    npm ERR! notsup Actual Arch: x64
    ```

## npm 업그레이드 (in Windows, Ubuntu)
- 버전 확인
    
    ```
    npm -v
    ```
- npm 다시설치

    ```
    npm install -g npm
    ```

- 버전 다시 확인
    
    ```
    npm -v
    ```

## vue 파일 종류

- vue.js = 개발용 (모든 오류 메시지 및 디버그 모드)

- vue.min.js = 프로덕션 (오류 메시지 없음, 30.67kb min+gzip)

## vue cdn

```
<!-- 개발버전, 도움되는 콘솔 경고를 포함. -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>

<!-- 상용버전, 속도와 용량이 최적화됨. -->
<script src="https://cdn.jsdelivr.net/npm/vue"></script>
```

## vue, vue cli 설치
- vue 설치

    ```
    # 최신 안정화 버전
    $ npm install vue

    # 버전확인
    vue --version
    ```

- vue cli 설치

    ```
    npm install -g @vue/cli
    # OR
    yarn global add @vue/cli
    ```

- vue cli 업그레이드

    ```
    npm update -g @vue/cli

    # OR
    yarn global upgrade --latest @vue/cli
    ```

# 참고

- https://cli.vuejs.org/guide/installation.html