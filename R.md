## Operator

**CAREFUL**
```R
x = sqrt(3)^2
x == 3
```
-> Result is False, because floating-point error  
  
USING near function
```R
x = sqrt(3)^2
dplyr::nead(x, 3)
```
-> Result is True

**NA/NULL**
- NA는 Not Available. 카운팅되나 계산할 수 없다.
- NULL은 NOT counted value. 카운팅되지 않으며 해당 값을 제외하고 계산된다.

</n>
</n>

## file data

- Working Directory
```R
getwd()
setwd("주소")
```
-> getwd()를 이용하여 현재 위치를 파악할 수 있다.  
-> setwd()를 이용하여 작업공간의 위치를 설정해줄 수 있다.  
-> 현재 위치보다 높은 곳을 표시할 때는 "../"를 이용한다.  

  
- Read file
```R
data = read.csv(file.choose(), header=TRUE)
data = read.csv("파일주소", header=TRUE)
```
-> file.choose()를 이용해 마우스로 클릭한 파일을 불러올 수 있다.  
-> header=TRUE를 이용하면 1행을 무시하고 가져온다.  

- Save file
```R
save(value, file = 'file name')
save.image('image file name')
```

- Load file
```R
load('file name')
```

## Vector

- Create
```R
vector_1 = c(values)
```
-> c is to combine  
-> vector1 + 0.2 등 연산 가능  

</n>

- Indexing
```R
vector_1[2]
```
-> 괄호 안에는 조건이 들어가도 된다.

- is.vector()
  - 벡터인지 아닌지 확인. TRUE/FALSE

- Repeating vector
```R
rep(value, n)
rep(c(val_1, val_2), n)
rep(c(val_1, val_2), each = n)
```
-> each가 없으면 벡터가 반복되고, each가 존재하면 벡터값이 각자 반복된다.  
-> Ex. val_1, val_2, val_1, val_2 / val_1, val_1, val_2, val_2  

- Operations
  - ^n  
  - sqrt()  
  - exp()
  - log()
  - ceiling() 올림
  - floor() 내림
  - %% 나머지

</n>

## Sequence

- Create
```R
seq(from = n1, to = n2, by = n)
```
-> n1부터 n2까지 n만큼의 간격으로 시퀀스를 생성  

- along
```R
seq_along(n)
```
-> 1부터 시작하는 시퀀스를 생성

## Matrix

- Create
```R
matrix(vector, nrow= n, ncol= n, byrow= TRUE)
```
-> nrow, ncol로 행과 열의 수를 지정
-> byrow=TRUE 로 설정하면 행 기준으로 먼저 채운다. defalut는 false

```R
vec_1 = c(values)
vec_2 = c(values)
rbind(vec_1, vec_2)
cbind(vec_1, vec_2)
```
-> 벡터들의 합으로 매트릭스를 생성할 수 있다.  
-> rbind는 행을 기준으로 아래로, cbind는 열을 기준으로 옆으로 합친다.  
-> rbind, cbind를 진행할 때 dimension이 맞지 않으면 오류가 발생한다.  

</n>

- Indexing
```R
matrix[row, col]
matrix[row, ]
matrix[, col]
```
-> matrix[row, ]는 해당 행의 모든 열을 보여준다.  
-> matrix[, col]는 해당 열의 모든 행을 보여준다.  
-> 해당 행, 열 위치에 조건을 넣어 filtering할 수 있다.

</n>

- Operations
  - vector에서 사용가능한 모든 operation
    - +, -, *, /, ^, sqrt(), log, exp()
  - %*% : matrix multiplation. 행렬곱.
  - solve() : inverse matrix
  - eigen() : eigenvalue & eigenvectors
    - eigen(matrix)$values : 고유값
    - eigen(matrix)$vectors : 고유벡터
  - t() : Transpose. 전치.
    - symmetry matrix를 만들기 위해선 (matrix + t(matrix))/2
 
</n> 

- rownames() / colnames()
```R
rownames(matrix) = LETTERS[1:3]
colnames(matrix) = c('a', 'b')
```
-> 행의 이름이 A, B, C로 정해진다.  
-> 열의 이름은 a, b로 정해진다.

</n> 

## Array
- Matrix는 two vector로 이루어져 있다.
- Array는 매트릭스의 확장으로, 3 dimension 이상이다.

</n>

## Dataframe
- Create
```R
data.frame(col_name = vector1, col_name = vector2 ...)
```

<n/>

- Indexing
```R
df[row, col]
df[row, ]

df[, col]
df[, col_name]
df$col_name
```
-> 매트릭스와 동일하게 사용가능하다.  
-> 아래 3개의 코드 결과는 같다.  
-> 데이터프레임에서 컬럼의 이름을 알고 싶다면 names(df)  

- attributes
```R
attributes(df)
```
-> 해당 데이터 프레임 안의 열과 해당 열 안의 값을 다 나타낸다.

## Function

### Built-in function
- typeof()
  - 자료형 확인  
 
- length()
  - 길이 확인
  - vector, matrix 등 안에 들어있는 element의 총 갯수를 반환한다.
 
- dim()
  - matrix와 array에 적용  
 
- nrow() / ncol()
  - matrix에 적용, 행과 열의 갯수를 반환

- sum(x, na.rm = TRUE)
  - 합, TRUE라면 NA값을 제외하고 계산  
 
- mean(x, na.rm = TRUE)
  - 평균, TRUE라면 NA값을 제외하고 계산    

- any() / all()
  - any() : 조건에 해당하는 것이 하나라도 있다면 TRUE
  - all() : 조건에 모두 해당해야 TRUE  
 
- identical()
  - 값, 타입 등 모든 것이 같으면 TRUE 반환  

- filtering
  - subset(x, condition)
    - 조건에 해당하는 x 안의 값을 반환
  - which(condition)
    - 조건에 해당하는 인덱스 값을 반환
   - ifelse(condition, if의 결과, else의 결과)
     - vector 값을 반환  
    
- 정렬
  - sort(x, decreasing=T/F)
    - T로 하면 내림차순
  - order(x)
    - 정렬한 인덱스를 반환  
  
- apply(m, p, f, farg)
  - m : matrix or array object  
  - p : dimension code (row=1, column=2)  
  - f : R function
  - farg : an optional set of arguments of f  
    - trim = n : 양극단(상/하한)의 일정 비율을 제거한다.  
    - na.rm = TRUE  

- Transform
  - as.vector() : matrix or array -> vector object  
  - as.matrix() : vector of array -> matrix object  
