
### 날짜 : 2024-08-01 13:43

### 주제: 

---
### 메모: 
### 목차

1. (Built-in) 배열(Array)과 슬라이스(Slice)
    1. Array
    2. Slice
    3. Array와 Slice의 차이점
2. 큐(Queue)와 스택(Stack)
3. (Built-in) 맵(Map)
4. 트리(Tree)
    1. 이진 검색 트리(BST, Binary Search Tree)
    2. AVL Tree
5. Cosmos-SDK의 IAVL 트리
    1. IAVL 트리란 무엇인가?

### 1. 배열(Array)과 슬라이스(Slice)
Array와 Slice는 가장 기본적인 자료구조로, go에서 직접 지원해준다. (built - in)
#### 1. Array
배열은 고정된 크기의 동일한 타입 요소들의 집합이다. 배열의 크기는 선언시 정해지며 변경할 수 없다.

#### 2. Slice 
슬라이스는 동적 배열로, 배열과 달리 크기를 유연하게 조절할 수 있다.
slice는 배열을 부분 참조할 수 있다.

#### 3. Array와 Slice의 차이점
- Array는 정적으로 할당하고 Slice는 동적으로 할당한다. Slice는 선언에 미리 크기를 선언하지 않아도 된다.
- Slice는 배열의 부분 집합을 참조할 수 있다.
- Slice는 Array보다 더 많은 기능을 제공하며 Array보다 더 자주 사용딘
### 출처(참고문헌)
-

### 연결문서
-