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
-> Matrix는 two vector로 이루어져 있다.
-> Array는 매트릭스의 확장으로, 3 dimension 이상이다.

- Create
```R
array(n, dim=c(n1, n2, n3))
```
-> n1개의 행, n2개의 열 n3개로 이루어진 array가 생성된다.  

<n/>

## List
-> A list objector is vector.  

- Create
```R
x = list(component1 = value, component2 = value)
y = list(val_1, val_2, val_3)
z = vector(mode = 'list', length)
```
-> 리스트는 다른 타입의 데이터를 합쳐 만들 수 있다.  

- Indexing
```R
list$component
list[[index]]
list[['component']]
```
-> list[n]을 하면 해당 위치의 $component와 값이 함께 반환된다.  
-> NULL 갑을 대입해 해당 위치를 삭제할 수 있다.  

- Operations
  - names(list) : component 이름을 보여준다.
  - unlist(list) : accessing valuse in list components
  - applying function
    - lapply(list, function) : component 별로 함수를 적용한다.
    - sapply(list, function) : 결과를 vector 혹은 matrix로 반환한다.
   
- Recursive lists
  - list 안에 list를 넣을 수 있다.
 
</n>

## Dataframe
-> Data frame is a list.

- Create
```R
data.frame(col_name = vector1, col_name = vector2 ...)
data.frame(vector1, vector2, vector3, stringsAsFactors=F)
```
-> stringsAsFactors = T/F default는 T.  
-> F로 하면 character vector를 factor로 변환하는 것을 막는다.

<n/>

- Indexing
```R
df[row, col]
df[row, ]

df[, col]
df[, col_name]
df$col_name
```
-> 리스트, 매트릭스와 동일하게 접근 가능하다.  
-> 아래 3개의 코드 결과는 같다.  
-> 데이터프레임에서 컬럼의 이름을 알고 싶다면 names(df)  
-> df[row, col, drops = FALSE] 를 이용하면 data.frame의 형태를 유지한다.  
-> 조건을 넣어 인덱싱할 수 있다.  

**dim()**
```R
dim(df[[n]])
dim(df[n])
```
-> NULL. df[[n]]는 matrix가 아니다.  
-> df[n]는 결과가 나온다.

- attributes
```R
attributes(df)
```
-> 해당 데이터 프레임의 속성들을 나타낸다.  
-> $names, $class, $row.names

- Removing NAs
```R
complete.case(df)
df[complete.case(df)]
```
-> NA면 FALSE  
-> df[complete.case(df)]를 통해 NA가 포함된 행 제거

- Adding observations
```R
rbind(df_1, df_2)
rbind(df, list)
df[n1:n2, ] = value
```
-> component가 같은 요소끼리 행 기준 합친다.  
-> 반환된 자료는 데이터프레임 형식이다.  
-> 데이터프레임끼리 합칠 때는 상관없으나, list 등과 합칠 때는 stringAsFactors = FALSE로 한 데이터프레임과 합쳐야 한다.  
-> 데이터프레임은 문자형 자료를 factor로 전환하기 때문이다.  
-> df[n1:n2, ]를 통해 n1부터 n2행까지 자료를 넣는다.  

```R
cbind(df, matrix)
df&col_name = value
df[[n]] = value
df[n1:n2] = value
```
-> df의 기존 열에 조건을 부여하여 합칠 수 있다.  
-> df[[n]]은 n 열에 자료를 넣는다.  
-> df[n1:n2]는 n1부터 n2열까지 자료를 넣는다.  

- Merging Data Frames
```R
merge(d1, d2, by = 'col_name', all = T)
```
-> by를 기준으로 데이터 프레임을 합친다.  
-> by 기준으로 두 데이터 프레임에 겹치는 내용이 없다면 반환되지 않는다.  
-> all = T를 통해 겹치지 않는 자료가 있어도 전부 출력한다. 빈 부분은 NA.
-> all.x = T를 하면 d1의 모든 행을, all.y = T를 하면 d2의 모든 행을 반환한다.  
-> 자료는 같으나 column name이 다를 경우 by.x = 'col_name_d1', by.y = 'col_name_d2'  

- Applying Functions
  - apply(df, 1 / 2 , function)
  - lapply(df, function) : list로 반환.
 
- is.data.frame() : 데이터프레임인지 아닌지 확인.  

<n/>

## Factor
-> 추가적인 정보(level)를 가지고 있는 vector  

- Create
```R
factor(vector)
```

- Level
```R
levels(df$col_name) <- c('val_1', 'val_2')
```
-> level로 설정한 값이 들어가지 않을 수는 있지만, 설정하지 않은 값이 대입될 수는 없다.  

- tapply(x, f, g)
```R
tapply(factor1, factor2, function)
```
-> factor1과 factor2의 length는 같아야 한다.    
-> vector or matrix로 반환한다.  

- split(x, f)
```R
split(df, df$factor_col_name)
```
-> dataframe or vector  
-> 해당 factor의 레벨로 그룹화한다.  
-> list(df$col_name, df$col_name)을 통해 여러 factor로 그룹화할 수 있다. 

- by(x, f, g)
```R
split(df, factor, function)
```
-> tapply의 경우 x가 vector여야 했으나, by는 matrix, data frame에 적용 가능하다.

<n/>

## Function

### Built-in function
- typeof()
  - 자료형 확인  

- str()
  - R object의 structure 보여준다.
 
- length()
  - 길이 확인
  - vector, matrix, factor 등은 안에 들어있는 element의 총 갯수를 반환한다.
  - list나 dataframe은 component의 갯수를 반환한다.
  - length(level(factor)) 하면  level의 갯수를 반환한다.
 
- dim()
  - matrix와 array에 적용  
 
- nrow() / ncol()
  - matrix에 적용, 행과 열의 갯수를 반환

- sum(x, na.rm = TRUE)
  - 합, TRUE라면 NA값을 제외하고 계산  
 
- mean(x, na.rm = TRUE)
  - 평균, TRUE라면 NA값을 제외하고 계산
 
- range(x)
  - 최솟값, 최댓값을 반환.
 
- quantile(x, prob=c(n1, n2, n3 ...))
  - n분위수를 반환.  

- any() / all()
  - any() : 조건에 해당하는 것이 하나라도 있다면 TRUE
  - all() : 조건에 모두 해당해야 TRUE  
 
- identical()
  - 값, 타입 등 모든 것이 같으면 TRUE 반환  

- filtering
  - subset(x, condition)
    - 조건에 해당하는 x 안의 값을 반환  
    - NA 값을 무시한다.  
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
  - as.data.frame() : convert object into data frames
 
- Table()
  - matrix or data frame에 적용할 수 있다.
  - addmargins(table, margin = 1 / 2) : 테이블에서 행과 열의 합을 반환한다. margin = 부분이 없으면 둘 다 반환.
  - dimnames(table)$col_name <- c(values) 이름을 설정해줄 수 있다.

- aggregate(x, by = col_name, function)
  - by 대신 list(df$col_name)이 들어갈 수 있다.
  - tapply() 와 다르게 x 자리에 여러 열을 가진 값이 들어갈 수 있다.
 
- cut(x, i, labels = FALSE)
  ```R
  x = c(2, 5, 10, 15 ,17)
  y = seq(from = 0, to = 20, by=2)
  cut(x, y)
  ```
  - x를 y를 기준으로 자른다.  
  - (0, 2], (4, 6] (8, 10], (14, 16], (18, 20] x가 y에 포한된 간격이 반환된다.
  - labels = FALSE로 자르면 몇번째 간격에 포함되는지 반환된다. 1 3 5 8 10

- dplyr
  - 불러오기
  ```R
  library(dplyr)
  ```
  - 내장함수
    - filter(df, col_name = condition)
    - arrange(df, desc(col_name)) : 해당 컬럼을 기준으로 정렬한다. default는 Asc. 여러 열을 기준으로 할 수 있다.  
    - select(df, col_name1, col_name2, ... ) : -c(col_name:col_name) 하면 해당 컬럼들을 제외한 컬럼들을 보여준다.
      - starts_with('character') : 해당 문자열로 시작하는 컬럼을 보여준다.  
      - ends_with('character') : 해당 문자열로 끝나는 컬럼을 보여준다.  
      - contains('character') : 해당 문자열을 포함하는 컬럼을 보여준다.  
    - mutate(df, new_column_name = 기존 columns을 조합한 수식) : 새로운 파생컬럼을 생성한다.  
    - summarize(N = n(), name = function(col_name), ...)
      - n() : number or rows
    - group_by(col_name) : 해당 컬럼을 기준으로 그룹화하여 summarize 결과를 확인할 수 있다.  
      -> dataframe or tibble 을 first argument로 가진다.
      -> select(filter())로 합쳐서 사용할 수 있다.
      -> %>% operator를 통해 긴 병합을 보기 편하게 사용할 수 있다. (Ctrl + Shift + M)

### User-defined functions
```R
function_name = function(argument1, argument2, ...,  default values){
  수식
  return_value
}
```
-> default value 위치에 값을 넣지 않으면 디폴트 값으로 계산된다.  
-> ex. fun_name = function(x, na.rm = FALSE) 에는 fun_name(x, TRUE) 로 해야 계산된다. 
-> function은 object이다. ex. f = fun_name 이면 f는 fun_name과 같은 함수다.  

- for loop
```R
for (k in x) { do something }
```
-> number of repetition = length of x  
-> break : 조건에 해당하면 for문 탈출  
-> next : 조건에 해당하면 skip  

```R
for (k in x) { read.table() }
for (k in x) { get() }
```
-> table을 읽거나, get()을 통해 object를 불러올 수 있다. 

- while 
```R
while (condition) { do something }
```
-> 조건이 TRUE인 동안 계속 반복  
-> condition이 FALSE가 되거나, break를 통해 탈출할 수 있다.  

- repeat{}
  - while과 유사하나, 조건이 없다. 따라서 break를 통해서만 탈출할 수 있다.
 
- ifelse
```R
if(condition) {
  do something
} else if (condition) {
  do something
} else {
  do something
}
```
-> 한 줄로 정리된다면 굳이 {}는 필요하지 않다.  

<n/>

## Operator
**NA는 계산 불가, 반환 시 결과는 NA**

```R
x %in% y
```
-> x is element of y  

- Logical vector  
  - '>', >=, <, <=, !=, ==  

- Bollen operator for scalar
  - & and , | Or
  - && and, || OR ; Logical scalar
 
**Logical values**
-> TRUE = 1, FALSE = 0으로 계산된다.
-> ex. sum(x >= 3) 하면 조건에 해당하는 TRUE 값이 x 안에 몇개나 있는지 셀 수 있다.  
