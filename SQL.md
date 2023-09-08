# SQL

>데이터베이스에서 데이터를 추출하고 조작하는 데에 사용하는 구조적 쿼리 언어
<br/>

# SQL 문법
## Common Commands

- SELECT 
```MySQL
SELECT <col_name>, <col_name> FROM <table_name> LIMIT <num_rows> ;
```
-> returns all the rows and columns using *  
-> SELECT DISTINCT를 이용하여 중복없이 뽑을 수 있다.

- - -

- INSERT INTO (행 삽입)
```MySQL
INSERT INTO <table_name> (col_2, col_3) VALUES (val2, val3) ;
```
-> 다른 컬럼은 default 값을 가지게 된다.  
-> 모든 컬럼에 값을 넣을 때는 컬럼명을 쓰지 않아도 된다.  
<br/>
** Inserting Multiple Rows (많은 값을 입력할 때)
 ```MySQL
INSERT INTO <table_name>
VALUES (val1, val2, val3), (val4, val5, val6), (val7, val8, val9);
``` 

- - -

- UPDATE (데이터 값 변경)
```MySQL
UPDATE <table_name> SET <col1>=<val1>, <col2>=<val2> WHERE condition;
```

- - -

- Copying Tables (테이블 복사)
```MySQL
CREATE TABLE <copy_table_name> AS (SELECT * FROM <table_name>);
```
-> 그러나 auto-incremented primary key 는 복제되지 않는다.

<br/>
<br/>

## DB-related Commands
- SHOW (데이터베이스, 테이블 확인)
```MySQL
SHOW DATABASES;
SHOW TABLES;
```

- - -

- CREATE DATABASES (데이터베이스 생성)
```MySQL
CREATE DATABASES <db_name>;
```

- - -

- USE (사용할 데이터베이스 선택)
```MySQL
USE <db_name>;
```

- - -

- SELCET DATABASE() (선택된 데이터베이스 확인)
```MySQL
SELCET DATABASE();
```

- - -

- DESCRIBE (테이블 구조 확인)
```MySQL
DESCRIBE <table_name>;
```

- - -

- DROP _ IF EXISTS (데이터베이스, 테이블 삭제)
```MySQL
DROP DATABASE IF EXISTS <db_name>;
DROP TABLE IF EXISTS <table_name>;
```

- - -

- CREATE TABLE (테이블 생성)
```MySQL
CREATE TABLE table1 (
col_1 data_type condition,
col_2 data_type condition,
PRIMARY KEY (col_1),
FOREIGN KEY (col_2),
REFERENCES table2(col_2)
);
```
-> Primary key 는 2개가 될 수도 있다.  
  
** Foreigh Key

<br/>
<br/>

## Table-related Commands













