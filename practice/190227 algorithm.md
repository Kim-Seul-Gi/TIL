# 190227 algorithm

## 1. Queue

스택과 큐의 차이점을 이해하고 있어야 한다.

BFS - Queue(FIFO)

DFS - stack(LIFO, 가장 늦게 들어온 원소가 빨리 삭제된다.), 재귀

- Queue - 넣은 순서대로 저장/ 먼저 들어온게 먼저 나감
  - enQueue : 넣는 것 
  - deQueue : 빼는 것

```python
# c언어 스타일의 Queue 구현
front=-1
rear=-1
size = 10
Q = [0]*10
# rear, front가 계속 커지는데..?? 영구적으로 쓸 수는 없는 모델이다.
def isFull():
    global rear
    return rear==len(Q)-1

def isEmpty():
    global rear, front
    return rear==front

def enQueue(item):
    global rear
    if isFull():
        print('isFull 상태')
    else:
        rear += 1
        Q[rear]=item
        print(Q[rear])

def deQueue():
    global front
    if isEmpty():
        print('isEmpty 상태')
    else:
        front += 1
        return Q[front]

def Qpeek(): # 지워지는 것이 아니다. deQueue를 하면 무엇이 빠질지 알려주는 것이다.
    global front, rear
    if isEmpty():
        print('isEmpty 상태')
    else:
        return Q[front+1]

enQueue(1)
>>1
enQueue(2)
>>2
enQueue(3)
>>3
print(Qpeek()) >>1
print(deQueue()) >>1
print(deQueue()) >>2
print(deQueue()) >>3
```

## 2. BFS 예제

너비 탐색

```python
import sys
sys.stdin = open('연습문제3.txt')

'''예시 입력
7 8 # 점의 갯수, 간선의 갯수
1 2 1 3 2 4 2 5 4 6 5 6 6 7 3 7 # 간선의 방향(양방향성이긴함.)

예시 출력 [0, 1, 1, 2, 2, 3, 2]
'''
# 이건 집어넣기 전에 visited 체크버전
def bfs(num):
    global visited, queue, M, G

    queue.append(num)
    visited[num-1] = 1

    while len(queue)!=0:

        w = queue.pop(0)
        result.append(w)
        for k in range(1,M+1):
            if G[w][k]==1 and visited[k-1]==0 and k not in queue:
                queue.append(k)
                visited[k-1] = visited[w-1] + 1

    for x in range(len(visited)):
        visited[x]-=1

    return visited

M, N = input().split()
M = int(M) # 점의 갯수
N = int(N) # 간선의 갯수

G = [[0 for _ in range(M+1)] for _ in range(M+1)]
visited=[0] * M
queue=[]
result=[]
dots=list(map(int,input().split()))
# dots = 인접행렬 확인용
# print(dots)
for i in range(N):
    # 행에서 열로 갈 수 있는지의 여부 = 1
    G[dots[i*2]][dots[i*2+1]]=1
cnt=0
a=0
# G에 잘 들어간 것을 확인
# for j in range(len(G)):
#     print(G[j])

print(bfs(1))
```

```python
import sys
sys.stdin = open('연습문제3.txt')

'''예시 입력
7 8 # 점의 갯수, 간선의 갯수
1 2 1 3 2 4 2 5 4 6 5 6 6 7 3 7 # 간선의 방향(양방향성이긴함.)

예시 출력 : [1, 2, 3, 4, 5, 7, 6]
'''
# 이건 집어넣은 후에 체크처리
def bfs(num):
    global visited, queue, M, G

    queue.append(num)
    while len(queue)!=0:

        w = queue.pop(0)

        if not visited[w-1]:
            visited[w-1]=1
        result.append(w)

        for k in range(1,M+1):
            if G[w][k]==1 and visited[k-1]==0 and k not in queue:
                queue.append(k)

    return result

M, N = map(int,input().split())
print(type(M))
print(N)
M = int(M) # 점의 갯수
N = int(N) # 간선의 갯수

G = [[0 for _ in range(M+1)] for _ in range(M+1)]
visited=[0] * M
queue=[]
result=[]
dots=list(map(int,input().split()))
# dots = 인접행렬 확인용
# print(dots)
for i in range(N):
    # 행에서 열로 갈 수 있는지의 여부 = 1
    G[dots[i*2]][dots[i*2+1]]=1
cnt=0
a=0
# G에 잘 들어간 것을 확인
# for j in range(len(G)):
#     print(G[j])

print(bfs(1))
```

