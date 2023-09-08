## SQL

<pre><code>데이터베이스에서 데이터를 추출하고 조작하는 데에 사용하는 구조적 쿼리 언어</code></pre>

# SQL 문법

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
  
* Inserting Multiple Rows (많은 값을 입력할 때)
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

- DROP TABLE IF EXISTS (테이블 삭제)
```MySQL
DROP TABLE IF EXISTS <table_name> ;
```

- - -

- Copying Tables (테이블 복사)
```MySQL
DROP TABLE IF EXISTS <table_name> ;
```
  
2. 비교연산자와 논리연산자
-> WHERE 절 이용
-> 비교 연산자, 특정 컬럼이 특정 값을 가지는 데이터만 불러오기 위해서 사용
-> AND, OR, LIKE, IN (), BETWEEN () AND ()
-> NULL, NaN (Not a Number)을 확인하기 위해선 IS (NOT) NULL 이용

LIKE 심화 
% : 와일드카드 (\%가 우리가 생각하는 % 기호)
_ : 특정하지는 않지만 몇 개의 문자가 들어가는지는 알려줌
