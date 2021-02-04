# pypi 배포하기

## 가입하기
- https://pypi.org/ 접속

- 오른쪽 위에 register 버튼 클릭

    ![screenshot1](http://cfile4.uf.tistory.com/image/99B74D33601A583B24CBF0)

- 정보 입력후 가입하기
    - Name : 이름

    - Email address : 이메일 주소

    - Username : 닉네임 (로그인시 아이디로 사용됨)

    - Password : 로그인 암호

    ![screenshot2](http://cfile2.uf.tistory.com/image/99EF0D45601A583B2372F0)


## 필요 패키지 다운로드
```
pip install setuptools wheel twine
```

## 배포 명령어
- 패키징 (※ 진행시 "프로젝트폴더/dist" 폴더 삭제)

    ```
    python setup.py sdist
    ```

- 패키징 (※ 진행시 "프로젝트폴더/dist" 폴더 삭제)

    ```
    python setup.py bdist_wheel
    ```

- 패키징 문제 없는지 테스트

    ```
    twine check dist/*
    ```

- 배포하기

    ```
    twine upload dist/[프로젝트명]-[버전]-py3-none-any.whl
    ```

    warning이 뜨긴했지만 아래와 같이 뜨면 성공
    ```
    Checking dist\[프로젝트명]-[버전]-py3-none-any.whl: PASSED, with warnings
    warning: `long_description_content_type` missing. defaulting to `text/x-rst`.
    Checking dist\[프로젝트명]-[버전].tar.gz: PASSED, with warnings 
    warning: `long_description_content_type` missing. defaulting to `text/x-rst`.
    ```

- 업로드된 프로젝트 다운로드

    ```
    pip install [프로젝트]
    ```

- 버전 갱신시에도 위에서부터 차례대로 진행

- 버전 갱신된 버전 다운로드시

    ```
    pip install --upgrade [프로젝트]
    ```