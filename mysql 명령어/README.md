# mysql 명령어

## 조회 (select)

- 일반적인 조회
    ```sql
    SELECT * FROM [테이블명] 
    
    WHERE [조건] 
    
    ORDER BY [정렬할 컬럼명] [정렬 방법(ASC, DESC)]

    GROUP BY [그룹할 컬럼]

    LIMIT [조회 개수]
    ```

- UTC 시간 변환 조회
    ```sql
    SELECT CONVERT_TZ( NOW(), 'GMT', '-04:00')
    ```

- 시간 추가 조회
    ```sql
    - 1초 추가
    SELECT DATE_ADD( NOW() , INTERVAL 1 SECOND)

    - 1분 추가
    SELECT DATE_ADD( NOW() , INTERVAL 1 MINUTE)

    - 1시간 추가
    SELECT DATE_ADD( NOW() , INTERVAL 1 HOUR)

    - 1일 추가
    SELECT DATE_ADD( NOW() , INTERVAL 1 DAY)

    - 1달 추가
    SELECT DATE_ADD( NOW() , INTERVAL 1 MONTH)

    - 1년 추가
    SELECT DATE_ADD( NOW() , INTERVAL 1 YEAR)
    ```

- 다른 테이블 select 된거 제외
    ```sql
    SELECT *
    FROM table1
    WHERE (no) NOT IN(SELECT no FROM table2 WHERE [검색조건])
    ```


## 삽입 (insert)

- 일반적인 삽입
    ```sql
    INSERT INTO [테이블명] ( [컬럼명들 ','로 구분] ) VALUES ( [값들 ','로 구분] )
    ```

- 데이터 복사 삽입
    ```sql
    INSERT INTO [테이블명] ( [컬럼명들 ','로 구분] ) 
    SELECT [컬럼명들] FROM [다른테이블명] WHERE 조건
    ```

## 수정 (update)

- 일반적인 수정
    ```sql
    UPDATE [테이블명] SET [컬럼명] = [변경값] WHERE [변경할 대상 조건]
    ```

## 삭제 (delete)

- 일반적인 삭제
    ```sql
    DELETE FROM [테이블명] WHERE  [삭제할 대상 조건]
    ```