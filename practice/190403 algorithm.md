# 190403 algorithm

## 1. Stack, Queue

queue 에 자료구조가 많이 들어갈 때에는

배열로 append, pop을 시키면, stack overflow 가 나올 수 있다. pop 자체의 복잡도가 N 이므로,

이럴 때에는 stack, queue를 c 스타일로 짜면 된다.

```python
Q = [0] * N**2
rear = -1
front = -1
def enQueue():
    global rear
    rear += 1
    Q[rear] = item
def deQueue():
    global front
    front += 1
    item = Q[front]
def empty():
    global rear, front
    if rear == front:
        return True
    return False
```



## 2. 서로소 집합들 ( Disjoint-Sets )

### 2-1. 개념

( A반_SW문제해결응용1_296/341 )

원소 중에 대표자를 뽑겠다??

x, y는 원소 이다.

- Make-Set(x) : 자기 자신(x)을 대표자로 하겠다.
- Find-Set(x) : x 가 속해있는 집단 중 대표자는 누구인가 찾는 함수.
- Union(x, y) : 두 개를 합치면 대표자 하나로 되어야 함. 대표자 쪽은 0번 인덱스로 가게끔 더하면 됨.

> 1차원 배열로 구현가능함.



### 2-2. 문제 : 최소신장트리(MST)

- 신장 트리 : N 개의 정점(노드), N-1 개의 간선 으로 이루어진 트리

- 최소신장트리 : 간선들의 가중치의 합이 최소인 시장 트리

  = 그래프에서 모든 점을 체크하는 최소 비용 문제 (간선의 합을 최소로 쓰는 방법)

ex, 송유관 건설



### 2-3. 알고리즘

- Prim :초기에 모든 점의 가중치를 무한으로 치고 , 시작점에서 갈 수 있는 방법에 대해 가중치가 최소인 점을 선택하고 , 지속적으로 최소가중치를 향해 누적.

단 순환되어서는 안됨. 

- KRUSAKL : 정리 필요

더 정리하도록.

