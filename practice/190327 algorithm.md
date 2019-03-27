# 190327 , 완전 검색 & 그리디

## 1. 완전 검색 & 그리디

```python
# 순열

def perm(n, k):
    if n == K:
        print(a)
    else:
        for i in range(k, n):
            a[i], a[k] = a[k], a[i]
            perm(n, k+1)
            a[i], a[k] = a[k], a[i]
           
a = [1,2,3]
perm(3, 0)

'''
[1, 2, 3]
[1, 3, 2]
[2, 1, 3]
[2, 3, 1]
[3, 2, 1]
[3, 1, 2] 나옴
'''
        
```



