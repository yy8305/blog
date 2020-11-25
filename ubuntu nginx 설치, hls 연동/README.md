# ubuntu nginx 설치
- 설치 명령어

    ```
    aptitude install software-properties-common
    add-apt-repository ppa:nginx/development

    #아래 메시지 출력될시  "apt-get install aptitude" 해당 명령어 실행
    The program 'aptitude' is currently not installed. You can install it by typing:
    apt install aptitude

    apt-get update
    apt-get install nginx-full

    nginx -v  #버전 확인

    service nginx status #nginx 상태 확인
    service nginx start #nginx 시작
    service nginx stop  #nginx 중지
    ```

- nginx 패키지 삭제 명령어

    ```
    sudo apt-get remove nginx    # 패키지 삭제
    apt-get --purge remove nginx # 패키지, 설정 모두 제거
    ```

- 경로

    ```
    # nginx html 위치
    /usr/share/nginx/html/

    # nginx 설정 파일
    /etc/nginx/conf/nginx.conf
    ```

- 서버 재시작시 nginx 재시작

    ```
    update-rc.d nginx defaults
    update-rc.d nginx enable
    ```

- 참고 url : [https://extrememanual.net/1842](https://extrememanual.net/1842)

# nginx ssl 적용시

- ssl 파일 생성 방법

    - /etc/nginx/ssl  #ssl 파일 담을 폴더 생성

    - 서버 인증서 + 체인 인증서 + 루트 인증서 순서로 합쳐서 crt.pem에 입력  
    key.pem은 그대로

- 참고 url
    - [https://erulabo.com/post/chain-certificate-on-nginx](https://erulabo.com/post/chain-certificate-on-nginx)

    - [https://www.comodossl.co.kr/certificate/ssl-installation-guides/Nginx.aspx](https://www.comodossl.co.kr/certificate/ssl-installation-guides/Nginx.aspx)

    - [https://cert.crosscert.com/nginx-ssl인증서-설치-매뉴얼/](https://cert.crosscert.com/nginx-ssl%EC%9D%B8%EC%A6%9D%EC%84%9C-%EC%84%A4%EC%B9%98-%EB%A7%A4%EB%89%B4%EC%96%BC/)


# nginx hls 연동

- nginx 공식 홈페이지  
    http://nginx.org/en/docs/http/ngx_http_hls_module.html#hls

- 연동법  
    https://docs.peer5.com/guides/setting-up-hls-live-streaming-server-using-nginx/


# wowza 서버 연동

- 참고 url  
    https://docs.peer5.com/guides/use-nginx-as-wowza-cache/

- /etc/nginx/nginx.conf 설정

    ```
        user nginx;
        worker_processes auto;
        pid /var/run/nginx.pid;
        worker_rlimit_nofile 1048576;

        events {
            worker_connections 1048576;
            multi_accept on;
            use epoll;
        }

        http {

            # upstream
            upstream wowza {
            ip_hash;
            # ADD YOUR SERVERS HERE - ONE PER LINE
            #server 192.168.1.2:1935;
            }

            # basic
            sendfile on;
            tcp_nopush on;
            tcp_nodelay on;
            server_tokens off;
            keepalive_timeout 300s;
            types_hash_max_size 2048;
            include /etc/nginx/mime.types;
            default_type application/octet-stream;

            # ssl
            ssl_ciphers "ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:DHE-RSA-AES256-GCM-SHA384:DHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA384:ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-SHA:ECDHE-RSA-AES128-SHA:DHE-RSA-AES256-SHA256:DHE-RSA-AES128-SHA256:DHE-RSA-AES256-SHA:DHE-RSA-AES128-SHA:ECDHE-RSA-DES-CBC3-SHA:EDH-RSA-DES-CBC3-SHA:AES256-GCM-SHA384:AES128-GCM-SHA256:AES256-SHA256:AES128-SHA256:AES256-SHA:AES128-SHA:DES-CBC3-SHA:HIGH:!aNULL:!eNULL:!EXPORT:!DES:!MD5:!PSK:!RC4";
            ssl_protocols TLSv1 TLSv1.1 TLSv1.2;
            ssl_prefer_server_ciphers on;
            ssl_session_cache shared:SSL:50m;
            ssl_session_tickets off;
            ssl_stapling on;
            ssl_stapling_verify on;
            # ssl_dhparam /etc/ssl/certs/dhparam.pem; # need to generate the .pem certifiate before using this
            resolver 8.8.4.4 8.8.8.8 valid=300s ipv6=off;
            resolver_timeout 10s;

            # logs
            access_log off;
            error_log /var/log/nginx/error.log;

            # gzip
            gzip on;
            gzip_disable "msie6";
            gzip_http_version 1.1;
            gzip_comp_level 6;
            gzip_types text/plain text/css application/json application/javascript text/javascript application/x-javascript text/xml application/xml application/xml+rss application/vnd.ms-fontobject application/x-font-ttf font/opentype font/x-woff image/svg+xml image/x-icon;

            # proxy
            proxy_redirect off;
            proxy_http_version 1.1;
            proxy_read_timeout 10s;
            proxy_send_timeout 10s;
            proxy_connect_timeout 10s;
            proxy_cache_path /var/cache/nginx/wowza_cache_temp use_temp_path=off keys_zone=wowza_cache_temp:10m max_size=20g inactive=10m;
            proxy_cache wowza_cache_temp;
            proxy_cache_methods GET HEAD;
            proxy_cache_key $uri;
            proxy_cache_valid 200 302 5m;
            proxy_cache_valid 404 3s;
            proxy_cache_lock on;
            proxy_cache_lock_age 5s;
            proxy_cache_lock_timeout 1h;
            proxy_ignore_headers Cache-Control;
            proxy_ignore_headers Set-Cookie;

            # default route
            server {
                listen 80 default_server;

                #listen 443 ssl default_server;
                #ssl_certificate /path/to/cert.crt;
                #ssl_certificate_key /path/to/cert.key;

                add_header X-Cache-Status $upstream_cache_status;

                location ~ \.(m3u8|mpd)$ {
                    proxy_cache_valid 200 302 5s;
                    proxy_pass http://wowza;
                }

                location / {
                    proxy_pass http://wowza;
                }
            }
        }
    ```

- nginx.conf 제대로 설정되었는지 테스트

    ```
        nginx -t
    ```