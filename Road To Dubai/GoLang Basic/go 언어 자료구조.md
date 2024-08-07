
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
- Slice는 배열의 부분 집합을 참조할 수 있다. 따라서 배열의 일부를 참조해 만들어진 슬라이스의 값을 변경하면 원본 배열의 값도 변경된다.
- Slice는 Array보다 더 많은 기능을 제공하며 Array보다 더 자주 사용된다.

### 2. Queue와 Stack
Queue는 FIFO (First-In-First-Out), Stack은 LIFO (Least-In-First-Out)을 따르는 구조를 의미한다.

### 3. Map
맵은 Key-Value 쌍을 저장하는 데이터 구조이다. 파이썬의 Dictionary와 유사하다. 
맵의 특징
- Key는 Unique해야 한다.
- Key와 Value의 타입은 같아야 한다.
- 크기는 동적으로 할당된다.
- Key를 통해 Map에 저장된 값에 빠르게 접근할 수 있다. O(1)

### 4. Tree
트리는 hierachical 데이터 구조로, 노드로 구성되며 각 노드는 자식 노드를 가질 수 있다.
Array, Slice와 같이 선형적이지 않고 자식-부모로 비선형적인 구조를 가진다.

#### 1. 이진검색트리 Binary Search Tree
이진 검색 트리는 각 노드가 최대 2개의 자식을 가지며, 
왼쪽 자식 노드는 부모 노드보다 작고,
오른쪽 자식 노드는 부모 노드보다 크다.
- 계층적 구조: 데이터의 계층적인 표현을 가능하게 한다.
- 효율적인 구조: BST는 평균적으로 O(log n)의 검색 시간복잡도를 가진다.
##### go에서 BST를 구현한 코드
 ```
type Node struct {
	value int
	left  *Node
	right *Node
}

// 새로운 노드를 추가하는 함수
func (n *Node) Insert(value int) {
	if value < n.value {
		if n.left == nil {
			n.left = &Node{value: value}
		} else {
			n.left.Insert(value)
		}
	} else {
		if n.right == nil {
			n.right = &Node{value: value}
		} else {
			n.right.Insert(value)
		}
	}
}

// 트리에서 값을 찾는 함수
func (n *Node) Search(value int) bool {
	if n == nil {
		return false
	}
	if value < n.value {
		return n.left.Search(value)
	} else if value > n.value {
		return n.right.Search(value)
	}
	return true
}

func main() {
	root := &Node{value: 10}
	root.Insert(5)
	root.Insert(15)
	root.Insert(3)
	root.Insert(7)

	fmt.Println(root.Search(7))  // true
    fmt.Println(root.Search(3))  // true
	fmt.Println(root.Search(12)) // false
}
```

#### 2. AVL Tree
AVL Tree는 BBST의 일종으로, 각 노드의 왼쪽과 오른쪽 서브 트리의 높이 차이가 1 이하가 되도록 한다. 그래서 높이를 항상 O(log n)으로 유지되도록 회전 연산을 수행해서 균형을 유지하는 게 AVL 트리이다.
기본 이진 탐색 트리에서 편향 트리와 같은 불균형 구조의 단점을 극복하기 위해 고안되었다.
AVL 트리와 같은 균형 트리는 삽입, 삭제 연산 후에도 균형을 유지해 성능을 보장한다.
##### 주요 특징
- **균형 인수**: 각 노드의 균형 인수는 왼쪽 서브트리의 높이와 오른쪽 서브트리의 높이의 차이입니다. AVL 트리는 이 균형 인수가 -1, 0, 1 중 하나를 유지하도록 합니다.
- **회전 연산**: 균형 인수가 -1, 0, 1을 벗어나는 경우, 트리의 균형을 맞추기 위해 회전 연산을 수행합니다. 회전 연산에는 네 가지가 있습니다: 단순 좌회전, 단순 우회전, 좌우 이중회전, 우좌 이중회전.

균형인수 (Balance Factor)
임의의 노드 k에 대해 
```Balance Factor (k) = height(subLeft(k)) - height(subRight(k))```
- BF = 1: 왼쪽 서브트리가  오른쪽 서브트리보다 1단계 높다
- BF = 0: 왼쪽 서브트리와 오른쪽 서브트리의 높이가 같다
- BF = -1: 왼쪽 서브트리가 오른쪽 서브트리보다 1단계 낮다
![[Pasted image 20240802005222.png]]
삽입, 삭제가 일어난 노드의 부모 노드를 차례로 BF를 검사한다.
#### 균형이 깨졌을 때
BF가 1, 0, -1을 벗어나는 노드 기준으로 어떤 Case인지 파악한다.
균형을 바로 잡았을 때, 균형을 맞춘 뒤에 검사를 멈추지 않고 남은 노드에 대해서 검사를 계속한다.

##### Left Left (LL) Case
##### Right Right (RR) Case

##### Right Left (RL) Case

##### Left Right (LR) Case

### 5. Cosmos-SDK의 IAVL 트리
#### 1. IAVL 트리란 무엇인가?
IAVL 트리는 BST, AVL 트리, Merkle 트리의 특성을 결합한 데이터 구조이다. 주로 블록체인의 상태를 저장하고 검증하는 데 사용한다.
##### IAVL 트리의 특징
- 이진 검색 트리: 각 노드는 최대 2개의 자식을 가지며, BST의 구조를 따른다.
- AVL 트리: 각 노드의 왼쪽 서브트리와 오른쪽 서브트리의 높이 차가 1 이하가 되도록 한다.
- Merkle 트리: 각 노드가 해시값을 가지며, 이를 통해 모든 하위 노드의 데이터 무결성을 검증할 수 있다. 

#### 2. IAVL 트리의 장점
- 효율적인 조작: 검색, 삽입, 삭제 등의 연산이 최악의 경우에도 O(log n)을 넘지 않는다.
- 암호학적 검증: Merkle 특성을 이용해 데이터의 무결성을 검증할 수 있다.
- 버전 관리: IAVL 트리는 상태의 버전을 관리하여, 특정 시점으로 되돌아 갈 수 있는 기능을 제공한다. 이는 블록체인의 상태 롤백과 검증에 유용하다.

IAVL 트리는 다음과 같은 주요 연산을 제공한다.
- 삽입 (Insertion): 새로운 키-값 쌍을 트리에 추가한다.
- 삭제 (Deletion): 트리에서 특정 키를 삭제한다.
- 검색 (Search): 특정 키의 값을 조회한다.
- 검증 (Verification) : Merkle 트리의 해시값으로 무결성을 검증한다.

### 출처(참고문헌)
-

### 연결문서
-