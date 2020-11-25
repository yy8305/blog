# 개요 (Overview)
- 난독화, 암호화 방법에 대해 기술하였습니다.

- 난독화가 암호화에 해당하지는 않지만 남이 소스를 편하게 볼수 없게는 만들수 있다고 생각됩니다.

# php 소스 암호화 방법

## 방법1 - 난독화

- [https://encoder.conory.com/](https://encoder.conory.com/)

    - 난독화 방법 : 들여쓰기 제거 + base64 encode

- [https://encoder.hoto.dev/](https://encoder.hoto.dev/)

    - 난독화 방법 : 원소스를 base64 encode

    - 문제점 : base64로 디코딩 할경우 원소스로 확인 가능

## 방법 2 - 암호화

- bczen

    - 문제점 : extention 설정해야됨, php 7.2 버전만 지원

    - github : [https://github.com/vjardin/bcgen/blob/PHP-7.2/tests/test-helper.php](https://github.com/vjardin/bcgen/blob/PHP-7.2/tests/test-helper.php)

- 상용솔루션

    - [Zend Guard](http://www.zend.com/en/products/guard/)

        - 가격 : 600 달러,   패키지(zend studio, server, guard) = 799 달러

    - [IonCube](http://www.ioncube.com/php_encoder.php)

        - php 코드 암호화 상용 솔루션

        - 가격 : 199 달러 (약 20만원)

        - 문제점 : 복호화 해주는 사이트가 존재하긴 합니다만 낮은 버전에서만 복호화가 가능하고 license key 하고 같이 암호화시 복호화 불가능 합니다.

        - 참고내용

            - [https://m.blog.naver.com/PostView.nhn?blogId=nicecoding&logNo=220604935750&proxyReferer=https:%2F%2Fwww.google.com%2F](https://m.blog.naver.com/PostView.nhn?blogId=nicecoding&logNo=220604935750&proxyReferer=https:%2F%2Fwww.google.com%2F)

    - [SourceGuardian](http://www.sourceguardian.com/text-features-page-160.html)

        - trial = 14일

        - 가격 : 199 달러 (약 20만원)

    - [phpSHIELD](http://www.phpshield.com/)

        - 가격 : 199 달러 (약 20만원)

    - [phpBolt (free)](https://phpbolt.com/)

        - php.ini 에 설정해야됨 (extension='/absolute-path/bolt.so' in php.ini)