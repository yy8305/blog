# mongo db 명령어

## mongodb 실행하기

- 서버 실행
    ```
    > mongod --dbpath=[경로]
    ```

- 서버 접속
    ```
     > mongo
    ```

## 조회 (select document)

- 일반적인 조회
    ```sql
    db.collection.find( { status: "A" } )

    # rdb 문법
    SELECT * FROM collection WHERE status = "A"
    ```

- _id 로 조회시
    ```sql
    db.collection.find( { _id:ObjectId('hash id') } )
    ```

## 삽입 (insert document)

- 일반적인 삽입
    - 1개 document insert
        ```sql
        db.collection.insertOne(
            { item: "canvas", qty: 100, tags: ["cotton"], size: { h: 28, w: 35.5, uom: "cm" } }
        )

        # rdb 문법
        insert into collection (item, qty, tags, size) VALUES ('canvas', 100, '["cotton"]', '{ h: 28, w: 35.5, uom: "cm" }')
        ```
    
    - 여러개 document insert
        ```sql
        db.collection.insertMany([
            { item: "journal", qty: 25, tags: ["blank", "red"], size: { h: 14, w: 21, uom: "cm" } },
            { item: "mat", qty: 85, tags: ["gray"], size: { h: 27.9, w: 35.5, uom: "cm" } },
            { item: "mousepad", qty: 25, tags: ["gel", "blue"], size: { h: 19, w: 22.85, uom: "cm" } }
        ])

        # rdb 문법
        insert into collection (item, qty, tags, size) 
        VALUES 
        ('journal', 25, '["blank", "red"]', '{ h: 28, w: 35.5, uom: "cm" }'),
        ('mat', 85, '["gray"]', '{ h: 28, w: 35.5, uom: "cm" }'),
        ('mousepad', 25, '["gel", "blue"]', '{ h: 28, w: 35.5, uom: "cm" }')
        ```

## 수정 (update document)

- 일반적인 수정
    - 1개 document update
        ```sql
        db.collection.updateOne(
            { item: "paper" },
            {
                $set: { "size.uom": "cm", status: "P" },
                $currentDate: { lastModified: true }
            }
        )

        # rdb 문법
        update collection set size.uom = 'cm', status = 'P', lastModified = NOW()
        where item = 'paper'
        ```
    
    - 여러개 document update
        ```sql
        db.collection.updateMany(
            { "qty": { $lt: 50 } },
            {
                $set: { "size.uom": "in", status: "P" },
                $currentDate: { lastModified: true }
            }
        )

        # rdb 문법
        update collection set size.uom = 'in', status = 'P', lastModified = NOW()
        where qty < 50
        ```


## 삭제 (delete document)
- 일반적인 삭제


# 참고

- https://docs.mongodb.com/manual/crud/