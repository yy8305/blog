# mongo db 설치 (in windows)

## 설치파일 다운로드

- [공식홈페이지](https://www.mongodb.com/try/download/community) 에서 다운로드

- 버전은 최신버전으로 나머지는 사진대로 선택후 Download 버튼 클릭

    ![screenshot1](http://cfile10.uf.tistory.com/image/99646F426029EF181CA3E1)

## 설치파일 실행

- 설치된 msi 파일 실행후 Next 클릭

    ![screenshot2](http://cfile23.uf.tistory.com/image/993259356029EF181C9D41)

- I accept ~ 체크후 Next 클릭

    ![screenshot3](http://cfile1.uf.tistory.com/image/9948DE3A6029EF191C4E9D)

- 일반적인 설치를 하실경우 Complete 클릭

    ![screenshot4](http://cfile1.uf.tistory.com/image/994C0E446029EF1A1C1C1B)

- Next 클릭

    ![screenshot5](http://cfile5.uf.tistory.com/image/999AC9486029EF1A1CB7F4)

- 왼쪽아래 "Install MongoDB Compass" 체크유지 및 Next 클릭   
    (mongodb GUI 툴을 설치하고 싶지 않으신분은 체크 해제)

    ![screenshot6](http://cfile30.uf.tistory.com/image/993264356029EF1A1C78BF)

- Install 클릭

    ![screenshot7](http://cfile26.uf.tistory.com/image/994C07446029EF1B1C1DAC)

- 설하는도중 아래 팝업이 뜰텐데 저의 경우 실행하고 있는게 많아 "Do not~" 체크후 OK 클릭   
    (대신에 나중에 꼭 재시작 해야합니다.)   
    만약 실행하고 있는 프로그램들이 닫혀도 상관없다면 "Close the~" 체크후 OK 클릭

    ![screenshot8](http://cfile25.uf.tistory.com/image/99DBED456029EF1B1C3F6C)

- 설치가 끝나고 바로 Compass 창이 뜰텐데 여기서 저는 자동 업데이트만 원하기 때문에 아래 처럼 체크후 "star ~" 클릭   
    (이후 창은 닫아도 됩니다.)

    ![screenshot9](http://cfile1.uf.tistory.com/image/99E6E0466029EF1C1C9FF8)

- Finish 클릭

    ![screenshot10](http://cfile5.uf.tistory.com/image/9947DA446029EF1C1D41F5)

- 지금 바로 시작하지 않을거면 No, 지금 바로 시작해도 되면 Yes

    ![screenshot11](http://cfile26.uf.tistory.com/image/99E6FC376029EF1C1C1828)


## 환경변수 설정

- 아래 경로로 이동해서 해당경로 복사
    ```
    C:\Program Files\MongoDB\Server\[버전]\bin
    ```

- 환경변수 등록페이지로 이동

    - 환경변수 페이지 접근방법 : 제어판 -> 시스템 및 보안 -> 시스템 -> 왼쪽 메뉴중에 고급 시스템 설정 -> 아래 환경변수 버튼 클릭

- 환경변수 등록

    - 아래 시스템 변수 리스트중에 "Path" 클릭후 아래 편집 버튼 클릭

    - 오른쪽에 새로만들기 버튼 클릭 -> 아까 복사한 mongodb 경로 붙여넣기 -> 확인 클릭

- 설치 확인

    - cmd에서 "set path" 입력


## mongodb 실행하기

- cmd 창에서 아래 명령어 실행 (서버 실행), 경로에다가는 데이터 저장할 경로 입력
    ```
    > mongod --dbpath=[경로]
    ```

- 새로운 cmd 창 열어서 아래 명령어 실행해서 접속 확인 (서버 접속)
    ```
     > mongo
    ```

## mongodb 관련 프로그램
- nosql booster (gui tool) : https://nosqlbooster.com/downloads

- Jetbrains datagrip (rdb 문법 -> mongo 문법 변환) : https://www.jetbrains.com/ko-kr/datagrip/