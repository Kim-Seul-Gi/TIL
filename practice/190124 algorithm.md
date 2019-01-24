# 190124 algorithm

## 0. remind

### 0.1 2차원 배열의 입력

```python
# 2차원의 배열 만드는 법
# n:행, m:열

n, m = map(int,input().split())
mylist = [[0 for _ in range(m)] for _ in range(n)] 

for i in range(n):
	mylist[i]=list(map(int,input().split()))
print(mylist)
```

### 0.2 비트 연산자

68p 참고

### 연습문제

