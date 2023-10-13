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

## Matrix

- Create
```R
matrix(vector, nrow= n, ncol= n, byrow= TRUE)
```
-> nrow, ncol로 행과 열의 수를 지정
-> byrow=TRUE 로 설정하면 행 기준으로 먼저 채운다.  

```R
vec_1 = c(values)
vec_2 = c(values)
rbind(vec_1, vec_2)
cbind(vec_1, vec_2)
```
-> 벡터들의 합으로 매트릭스를 생성할 수 있다.  
-> rbind는 행을 기준으로 아래로, cbind는 열을 기준으로 옆으로 합친다.  

</n>

- Indexing
```R
matrix[row, col]
matrix[row, ]
matrix[, col]
```
-> matrix[row, ]는 해당 행의 모든 열을 보여준다.  
-> matrix[, col]는 해당 열의 모든 행을 보여준다.

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
