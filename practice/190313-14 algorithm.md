# 190313-14

## 1. 논리와 증명

- 귀류법 : 명제를 부정하고, 부정된 명제의 모순을 찾음으로써 명제 자체를 증명함.



## 2. 수와 표현

1. 보수 처리법 (8bit라는 가정 하)
   - 14의 2의 보수 처리를 하기 위해서는 아래와 같은 과정을 거친다
     - 14의 2진법 처리 > 00001110
     - 14의 1의 보수 > 11110001 ( 0은 1로, 1은 0으로 )
     - 14의 2의 보수 > 11110010 ( 1의 보수 값에 0000001을 더함 )
     - shift를 할 경우 : 맨 왼쪽 bit는 부호를 나타내므로, 변하면 안된다.
       - 오른쪽으로 1 shift : 10111001  ( 의미상 //진수 를 의미함)
       - 왼쪽으로 1 shift : 11100100 ( 의미상 * 진수 를 의미함)



## 3. 집합과 조합론

1. 집함 : 두 집합이 같다는 것은 서로가 서로에게 부분집합임을 증명함으로써 증명 가능.
2. 부분집합 : 이전에 for 문으로 구했던 방식은 가지치기를 할 수 없으므로, 미래지향적이지 않음.

### 3-1. 순열, 조합, 중복순열, 중복조합

- 개념
  - 순열 : P
  - 조합 : C
  - 중복순열 : 파이
  - 중복조합 : H
- 문제의 상황에 맞는 접근법으로 가야 한다.

```python

```



1. 조합

```python
def combination(n, r, q):
    if r == 0:
        myprint(q)
    else:
        if n < r:
            return
        else:
            T[r - 1] = A[n - 1]
# A 에는 원본이 들어있는 배열 ex, [1,2,3,4]
# T 에는 맨 오른쪽부터 값이 채워진다. 크기는 [0] * x 이며 x는 r 이상이여야 한다. 담기 위한 그릇이므로.
            combination(n - 1, r - 1, q)
            combination(n - 1, r, q)

def myprint(q):
    while q != 0:
        q = q - 1
        print(" %d" % (T[q]), end='')
    print()

A=[1,2,3,4,5]
T=[0,0,0,0]
combination(5,3,3) # n은 n, r은 r, q는 r과 같아야 함
```



2. 중복조합

```python
def H(n, r, q):
    if r == 0:
        myprint(q)
    elif n == 0:
        return
    else:

        T[r - 1] = A[n - 1]
# A 에는 원본이 들어있는 배열 ex, [1,2,3,4]
# T 에는 맨 오른쪽부터 값이 채워진다. 크기는 [0] * x 이며 x는 r 이상이여야 한다. 담기 위한 그릇이므로.
        H(n, r - 1, q)
        H(n - 1, r, q)

def myprint(q):
    while q != 0:
        q = q - 1
        print(" %d" % (T[q]), end='')
        # print(T[q], end='')
    print()

A=[1,2,3,4,5]
T=[0,0,0,0]
H(5,3,3) # n은 n, r은 r, q는 r과 같아야 함.
```



## 4. 기초 수식

```python
T(n) = T(n-1) + 1
# 위 식의 의미는 T(n)의 호출 횟수는 T(n-1) 호출 횟수에 1을 더한 것
# 이런 의미.

T(n) = T(n-1) + n
# 위의 경우는 T()
```



## 5. 재귀

- 재귀적 dp, 반복적 dp > memoization 을 활용한 것들이다.
  - 다만 반복적 dp가 더 효율적이다.
- 병합정렬
  - 과정 
    - 낱개단위로 쪼갬
    - 두 개의 집단의 경우 서로 맨 왼쪽에 있는 것들을 비교하고
    - 더 작은 수를 비어있는 배열에 추가하고 작은 수가 들어있던 타겟을 오른쪽으로 한 칸 이동한 다음 두 개의 집단의 맨 왼쪽+n 칸에 해당하는 수들을 비교한다.
  - 시간을 줄이는 방법 : linked list (python에서는 해당되지 않음.)

- 참고 : 자율학습 - A반_SW문제해결응용_2  131-2 ppt
- 131 : 재귀적 dp
- 133 : 반복적 dp













