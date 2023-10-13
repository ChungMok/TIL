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

## Vector

- Create
```R
vector_1 = c(values)
```
-> c is to combine  
-> vector1 + 0.2 등 연산 가능

</n>
</n>

- Indexing
```R
vector_1[2]
```

## Matrix

## Dataframe
