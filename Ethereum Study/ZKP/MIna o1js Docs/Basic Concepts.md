
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
new Bool(x);    // 참, 거짓 값을 허용한다.
new Field(x);   // 정수를 받으며, Javascript에서 표현이 안되지만 Field가 표현할 수 있는 범위 내의 큰 숫자를 문자열로 저장한다.
new UInt64(x);  // Field를 받는다 - 64bit 내의 숫자로 제한할 때 유용하다.
new UInt32(x);  // Field를 받는다 - 32bit 내의 숫자로 제한할 때 유용하다.
PrivateKey, PublicKey, Signature;  // 계정 및 서명 작업에 유용
new Group(x, y); // 타원 곡선의 한 점으로, 2 개의 Field/numbers/strings를 허용한다.
Scalar;  // 해당 스칼라 필드 (Field와는 다름)
CircuitString.from('some string');  // 최대 128 길이의 문자열
```

Bool과 Field는 new 대신에 생성자를 호출해서 사용할 수 있다.
```
let x = Field(10);
let b = Bool(true);
```

### Conditionals
전통적인 조건문은 o1js에서는 지원되지 않는다.
```
// 이 조건문은 작동하지 않을 것이다.
if (foo) {
  x.assertEquals(y);
}
```

대신, o1js에 내장된 ```Circuit.if()``` 삼항연산자 함수를 사용한다.
```
const x = Circuit.if(new Bool(foo), a, b);  // foo ? a : b
```

### Functions
function은 타입스크립트에서와 마찬가지로 작동합니다. 예를 들어,
```
function addOneAndDouble(x: Field): Field {
  return x.add(1).mul(2);
}
```

### Common methods
자주 사용되는 몇가지 일반적인 메소드들은 다음과 같다.
```
let x = new Field(4); // x = 4
x = x.add(3);   
x = x.sub(1);
```
### 출처(참고문헌)
- https://docs.minaprotocol.com/zkapps/o1js/basic-concepts#field

### 연결문서
-