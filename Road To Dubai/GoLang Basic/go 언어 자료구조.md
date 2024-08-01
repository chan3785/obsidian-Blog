
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

 #### go에서 BST를 구현한 코드는 다음과 같다.
 
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
### 출처(참고문헌)
-

### 연결문서
-