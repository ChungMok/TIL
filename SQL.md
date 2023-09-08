# SQL

>데이터베이스에서 데이터를 추출하고 조작하는 데에 사용하는 구조적 쿼리 언어
<br/>

# SQL 문법
## Common Commands

- SELECT 
```MySQL
SELECT <col_name>, <col_name>
FROM <table_name>
WHERE condition
GROUP (BY)
HAVING
ORDER (BY) <col_name> DESC/ASC
LIMIT <num_rows> ;
```
-> returns all the rows and columns using *  
-> SELECT DISTINCT를 이용하여 중복없이 뽑을 수 있다.
-> SELECT 뒤에 함수(col_name) 혹은 사칙연산 사용 가능 

<br/>
**ORDER BY**
1. DESC (내림차순)
2. ASC (오름차순, 디폴트값)

- - -

- INSERT INTO (행 삽입)
```MySQL
INSERT INTO <table_name> (col_2, col_3) VALUES (val2, val3) ;
```
-> 다른 컬럼은 default 값을 가지게 된다.  
-> 모든 컬럼에 값을 넣을 때는 컬럼명을 쓰지 않아도 된다.  

<br/>
**Inserting Multiple Rows (많은 값을 입력할 때)**
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
ON _____ CASCADE
);
```
-> Primary key 는 2개가 될 수도 있다.
-> Primary Key와 달리 Foreign Key는 유니크하지 않아도 되며, NULL 값도 가질 수 있다. 

<br/>
**Data types**
1. string
2. numeric
   -> Integer Types : TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT
   -> UNSIGNED : only numbers >=0 디폴트 값은 SIGNED
4. datetime
5. date : YYYY-MM-DD
6. time : HH:MM:SS
7. datetime/timestamp : YYYY-MM-DD HH:MM:SS
8. ENUM : a string with a value chosen from a list of permitted values
9. BOOLEANs : 0(FALSE), 1(TRUE)

<br/>
**Foreigh Key**
1. Adding FK (외래키 추가)
```MySQL
ALTER TABLE <table1>
ADD FOREIGN KEY (col_2)
REFERENCES table2(col_2);
```
  
2. Dropping FK (외래키 삭제)
```MySQL
ALTER TABLE <table1>
DROP FOREIGN KEY (col_2);
```
     
3. SET referential constraints to FK (제약조건 설정)
- ON DELETE CASCADE
- ON UPDATE CASCADE
- ON UPDATE CASCADE IN DELETE CASCADE

<br/>
## Table-related Commands

- Add column (컬럼 추가)
```MySQL
ALTER TABLE <table_name>
ADD col_3 datatype condition
AFTER col_2;
```
-> AFTER 이용해 위치를 정할 수 있다.

- - -

- Drop column (컬럼 삭제)
```MySQL
ALTER TABLE <table_name>
DROP col_3;
```

- - - 

- Delete all rows
```MySQL
TRUNCATE TABLE <table_name>;
```

- - -

- Rename
```MySQL
ALTER TABLE <table_name>
CHANGE <col_before> <col_after> datatype condition;
```
-> 컬럼 변경

```MySQL
RENAME TABLE <table_before> to <table_after>; 
```
-> 쉼표를 통해 여러 테이블의 이름을 함께 변경 가능

<br/>

## Operators
- AND &&
- OR ||
- NOT !
- BETWEEN (숫자/문자) AND (숫자/문자)
- LIKE : 와일드카드 %, 문자의 개수 _
- IN (values) 
- YEAR() MONTH() : 연도,월 추출
- IS (NOT) NULL : NULL, NaN (Not a Number)을 확인








