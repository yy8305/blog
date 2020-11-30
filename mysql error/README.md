# 개요 (Overview)
- mysql 에러를 정리해봅니다.

# 에러
- 
    ```
    SQL 오류 (1075): Incorrect table definition; there can be only one auto column and it must be defined as a key
    ```

    - 해결방법
        ```
        아래와 같이 primary 키가 하나 포함되 있고 auto_increment 가 두개 일경우 발생하기 때문에 하나는 제외 시켜야 할것 같습니다.

        CREATE TABLE `test_table` (
            `no` BIGINT NOT NULL AUTO_INCREMENT COMMENT '번호',
            `sub_no` BIGINT NOT NULL AUTO_INCREMENT COMMENT '번호',
            PRIMARY KEY (`no`) USING BTREE
        )
        COLLATE='utf8_unicode_ci'
        ENGINE=InnoDB
        ;
        ```