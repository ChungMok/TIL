## SQL

<pre><code>데이터베이스에서 데이터를 추출하고 조작하는 데에 사용하는 구조적 쿼리 언어</code></pre>

# SQL 문법

1. SELECT, FROM, LIMIT

-> SELECT (컬럼명) FROM (테이블명) LIMIT (보고 싶은 행의 수)
->＊를 사용하면 전체 컬럼의 데이터를 불러옴

2. 비교연산자와 논리연산자
-> WHERE 절 이용
-> 비교 연산자, 특정 컬럼이 특정 값을 가지는 데이터만 불러오기 위해서 사용
-> AND, OR, LIKE, IN (), BETWEEN () AND ()
-> NULL, NaN (Not a Number)을 확인하기 위해선 IS (NOT) NULL 이용

# LIKE 심화 
% : 와일드카드 (\%가 우리가 생각하는 % 기호)
_ : 특정하지는 않지만 몇 개의 문자가 들어가는지는 알려줌
