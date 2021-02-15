# pypi 배포하기

## 가입하기
- https://pypi.org/ 접속

- 오른쪽 위에 register 버튼 클릭

    ![screenshot1](http://cfile21.uf.tistory.com/image/99DC0D436029F3EF1E81EC)

- 정보 입력후 가입하기
    - Name : 이름

    - Email address : 이메일 주소

    - Username : 닉네임 (로그인시 아이디로 사용됨)

    - Password : 로그인 암호

    ![screenshot2](http://cfile1.uf.tistory.com/image/99E563376029F3F01E5839)


## 필요 패키지 다운로드
```
pip install setuptools wheel twine

pip install m2r    # markdown 파일 rst 로 변환
```

## md 파일 rst로 변환
```
# cmd 창에서 해당 명령어 실행
# 완변하게 변환되지 않기 때문에 변환후에 파일 한번 확인 필요

> m2r ./README.md 
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