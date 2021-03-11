# vue 기초

## 프로젝트(cli) 만들고 실행하기

- 프로젝트 생성

    ```
    vue create my-project
    # OR
    vue ui
    ```

    - 세부설정

        ```
        ? Please pick a preset: 
            Manually select features  # 원하는 모듈하고 같이 설치



        ? Check the features needed for your project: Vue version, Babel, Router, Vuex, CSS Pre-processors, Linter

            (*) Babel   # javascript 컴파일러, 오래된 버전의 브라우저나 ECMA 5 자바스크립트 연동해주는것
            ( ) TypeScript
            ( ) Progressive Web App (PWA) Support   # 웹을 앱으로 사용하게끔 해주는것
            (*) Router   # vue router 사용여부 (웹페이지간 이동 라이브러리)
            (*) Vuex     # 중앙 집중식 저장소 역할, store 통해서 데이터 교환 가능
            (*) CSS Pre-processors   # css 전처리기(Sass 등) 사용여부
            (*) Linter / Formatter   # Linter(javascript 코드 문법, 구조등을 정해서 그거에 맞게 코딩) 사용여부
            ( ) Unit Testing
            ( ) E2E Testing



        ? Choose a version of Vue.js that you want to start the project with 2.x



        ? Use history mode for router? (Requires proper server setup for index fallback in production) (Y/n) Yes
                Y : hash 없이 기본url로 사용할경우, 이럴경우 페이지를 새로고침할때 페이지 경로 인식? 이 안되기 때문에 .htaccess 설정필요 ex) test.com/book
                N : URL을 hash 형태로 사용할경우 ex) test.com/#book



        ? Pick a CSS pre-processor (PostCSS, Autoprefixer and CSS Modules are supported by default): 
                > Sass/SCSS (with dart-sass)
                Sass/SCSS (with node-sass)  # 현재 유지관리 되고 있으나 폐지됨. 재구현된 dart-sass 쓰는걸로
                Less
                Stylus



        ? Pick a linter / formatter config: 
                ESLint with error prevention only
                ESLint + Airbnb config
                ESLint + Standard config
                > ESLint + Prettier



        ? Pick additional lint features: Lint on save, Lint and fix on commit
                (*) Lint on save   # 저장시 lint 검사를 제공
                (*) Lint and fix on commit   # 저장시 자동으로 fix가 가능한 것은 Fix까지 해줌



        ? Where do you prefer placing config for Babel, ESLint, etc.? In package.json
                In dedicated config files   # 따로 설정파일 만듬
                > In package.json             # package.json에 설정 추가



        # 현재 선택한 옵션을 다음번 프로젝트 생성시에 불러올것인지
        ? Save this as a preset for future projects? No 
        ```

- 프로젝트 실행

    ```
    cd my-project

    npm run serve
    ```

- vue 라이브러리
    - vue bootstrap

        ```
        # 설치
        npm install vue bootstrap bootstrap-vue

        # 참고
        https://bootstrap-vue.org/
        ```

## 프로젝트 에러 발생시 캐시 초기화
- npm 캐시 삭제: npm cache clean --force
- 프로젝트/node_modules 삭제 -> npm i (다시 설치)

# 참고
- https://cli.vuejs.org/