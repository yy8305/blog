# 개요 (Overview)
- aws s3 버킷생성 및 정적 웹사이트 호스팅 설정 방법 입니다.

- aws ui가 변경 됨에 따라 과정이 달라 졌을수 있다는점 유의 바랍니다.

# s3 버킷 생성
- aws console 접속 → s3 이동

- 버킷만들기 버튼 클릭

    1.  입력후 다음
        - 버킷 이름 : 아무렇게나 입력해도 되나 cloud flare 와 연동시 버킷이름은 사용할 dns 하고 같아야합니다. ex) example.com

        - 리전 : 리전 선택 ex) 아시아 태평양(서울)

    2.   다음

    3. 모든 퍼블릭 액세스 차단 해제 후 다음

- 버킷만들기 클릭하여 완료

# 정적 웹사이트 호스팅 설정
- 버킷리스트에서 해당 하는 버킷 클릭

- 속성탭 → 정적 웹 사이트 호스팅

    - "이 버킷을 사용하여 웹사이트를 호스팅합니다." 체크

    - 인덱스 문서 : index.html 입력

    - 오류문서 : 잘못된 url 접근시 에러 페이지 표시

    - 저장 클릭

- 권한탭 → 버킷정책 탭

    - 아래 내용 입력 후 저장 클릭

        ```json
        {
            "Version": "2012-10-17",
            "Statement": [
                {
                    "Sid": "PublicReadGetObject",
                    "Effect": "Allow",
                    "Principal": "*",
                    "Action": "s3:GetObject",
                    "Resource": "arn:aws:s3:::버킷명/*"
                }
            ]
        }
        ```

- 권한탭 → 액세스 제어 목록

    - 퍼블릭 액세스 → everyone  클릭 → 버킷 읽기 권한 체크






# 참고 url
- https://docs.aws.amazon.com/ko_kr/AmazonS3/latest/user-guide/static-website-hosting.html

- https://webruden.tistory.com/115