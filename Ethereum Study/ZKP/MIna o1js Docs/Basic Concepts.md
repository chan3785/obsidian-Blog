
### 날짜 : 2024-09-14 21:27

### 주제: 

---
### 메모: 

### Field
Field는 영지식 프로그래밍에서 데이터의 기본 단위이다. 
각 field 요소는 최대 256bit 크기의 숫자를 저장할 수 있다.
Solidity의 uint256로 생각하면 된다.

예를 들어서, 전형적인 프로그래밍에서는 숫자를 이렇게 사용한다.
`const sum = 1 + 3`.

o1js에서는 이렇게 사용한다.
```const sum = new Field(1).add(new Field(3))```

다시 간단하게 만들면,
```const sum = new Field(1).add(3)```

3이 자동으로 필드 자료형으로 인식되어 더 깔끔하게 정리된다.

### Built-in data types
아래는 흔히 사용되는 자료형이다.
```
new Bool(x);    // 참, 거짓을 받는다
new Field(x);   // 정수를 
new UInt64(x);  // accepts a Field - 
```
### 출처(참고문헌)
- https://docs.minaprotocol.com/zkapps/o1js/basic-concepts#field

### 연결문서
-