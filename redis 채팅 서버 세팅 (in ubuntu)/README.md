## redis 설치

- apt 업데이트

    ```
    sudo apt-get update
    sudo apt-get upgrade
    ```

- apt redis 설치

    ```
    sudo apt-get install -y redis-server
    ```

- redis 메모리 할당

    ```
    sudo vim /etc/redis/redis.conf # 파일 편집 -> maxmemory 찾기 -> byte 단위로 입력

    vmstat -s # 메모리 할당 확인
    ```

- 서비스 재시작

    ```
    sudo systemctl restart redis-server.service

    sudo systemctl enable redis-server.service
    ```

- 참고 url
    - [https://junghwanta.tistory.com/26](https://junghwanta.tistory.com/26)

## nodejs, pm2 세팅, redis 연동

- nodejs, npm 설치 명령어

    ```
    sudo apt-get update
    sudo apt-get install nodejs
    sudo apt-get install npm
    ```

- pm2 설치

    ```
    npm install pm2 -g
    ```

- redis 관련 pm2 설치

    ```
    pm2 install pm2-redis
    pm2 install pm2-server-monit
    pm2 install pm2-logrotate pm2 set pm2-logrotate:max_size 1G pm2 set pm2-logrotate:interval_unit 'DD'
    ```

- 채팅서버 시작

    ```
    pm2 start <chatting server config json file> # 서버 시작

    pm2 monit # 프로젝트 모니터링 (에러 나는지 확인)
    ```

    - chatting server config file

        ```
        ex) config.json

        {
            apps : [

                {
                name      : "chat_server",
                script    : "server.js",
                cron_restart : "* * 1 * *",
                env: {
                    NODE_ENV: "production",
                    SERVER_PORT: 5300
                }
                },

                {
                name      : "chat_server",
                script    : "server.js",
                cron_restart : "* * 1 * *",
                env: {
                    NODE_ENV: "production",
                    SERVER_PORT: 5301
                }
            ]
        }
        ```

## nginx 설치

- nginx 버전이 1.17.10 으로 만족한다면

    ```
    sudo apt install nginx
    ```

- 최신버전으로 설치 (2020-12-21 기준 1.19.6) (in ubuntu 20.04)

    ```
    # 최신상태로 유지
    $ sudo apt update && apt upgrade

    # nginx 설치
    $ sudo apt install curl gnupg2 ca-certificates lsb-release

    $ echo "deb http://nginx.org/packages/mainline/ubuntu `lsb_release -cs` nginx" \
    | sudo tee /etc/apt/sources.list.d/nginx.list

    $ curl -fsSL https://nginx.org/keys/nginx_signing.key | sudo apt-key add -

    $ sudo apt-key fingerprint ABF5BD827BD9BF62

    $ sudo apt update

    $ sudo apt install nginx

    # 버전 확인
    $ nginx -v
    ```

- 참고 url
    - [https://blog.dalso.org/linux/ubuntu-20-04-lts/11802](https://blog.dalso.org/linux/ubuntu-20-04-lts/11802)

## nginx 세팅

- /etc/nginx/conf.d 경로에 "도메인.conf" 파일 생성

    ```
    # 기존 default 파일 백업
    $ sudo mv default.conf default.conf.bak

    # 도메인명으로 설정파일 만들기
    $ sudo vi domain.com.conf

    # 아래 내용 복붙
    upstream socket_nodes {
        ip_hash;
        server 127.0.0.1:5300; # 채팅 서버 포트
        server 127.0.0.1:5301; # 채팅 서버 포트
    }

    server {

        server_name  domain.com;

        listen 6379; # 외부에서 접근할 포트
        listen 6380 ssl http2; # 외부에서 접근할 포트, https 포트
        ssl_certificate ssl_key.crt.pem;
        ssl_certificate_key ssl_key.key.pem;

        location / {
            proxy_set_header Upgrade $http_upgrade;
            proxy_set_header Connection "upgrade";
            proxy_http_version 1.1;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header Host $host;
            proxy_pass http://socket_nodes;
        }

    }
    ```

- 포트 해제

    ```
    6379, 6380 포트 열기
    ```