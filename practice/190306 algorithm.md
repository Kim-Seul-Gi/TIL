# 190306 algorithm

## 1. 트리

### 1-1. 그래프와의 차이점

- 그래프 를 푸는 방법- DFS, BFS (싸이클이 존재할 수 있음)

- 트리는 위에서 아래로 쭈우욱 = 계층구조 라는 특징


### 1-2. Binary Tree(이진트리)

BT - binary Tree = 3가지 방법 존재 > 주로 그래프 형식으로 생각해서 문제를 풀면 된다

- preorder

- inorder

- postorder


### 1-3. 트리 관련 용어

- 서브트리 : 부모자식 사이의 간선이 없어지는 경우 자식 쪽 을 말한다. 점 하나만 남아도 트리(이진트리도 가능)라고 한다

- 차수 : 자식이 몇세대까지 존재하는지

- 높이 : 루트부터 노드까지의 간선수

- 너비 : 사촌들의 수


### 1-4. 문제를 풀 때 주의할 점

- 삭제연산 관련돼서 고려해야 할 점
  - 해당하는 노드가 단말인가, 가지인가, 루트인가?
  - 삭제 후에 트리가 어떻게 생길 것인가.

- 최소 힙과 최대 힙 관련
  - 넣는 것 : 일단 넣은 다음에 올바른 자리로 이동시키는 형식이다. 423 참조 (기본 조건은 둘다 완전 이진트리 라는 점을 참조.)
  - 빼는 것 : 노드가 빠지는 경우에는 완전이진을 유지하기 위한 것을 먼저 노드자리로 이동시킨다.