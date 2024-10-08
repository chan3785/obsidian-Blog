
### 날짜 : 2024-08-01 12:04

### 주제: 

---
### 메모: 
### 목차
1. Interface란 무엇인가?
2. Interface와 polymorphism(다형성)
3. Empty Interface

### 0. Interface란 무엇인가?
인터페이스는 메서드의 집합을 정의한다. 인터페이스를 구현하려면 해당 타입의 모든 메서드를 정의해야 한다. 인터페이스의 특징은 다음과 같다.

- 암시적 구현: ```implements```키워드를 사용하지 않고도 해당 메서드를 구현함으로써 자동으로 인터페이스를 구현한다.
- 다형성: 여러 타입이 동일한 인터페이스를 구현함으로써 인터페이스를 통해 다른 타입을 일관되게 처리할 수 있게 해준다. 인터페이스는 함수가 필요한 메서드를 구현하기만 하면 다른 타입을 받아들이고 반환할 수 있게 해준다.

### 1. Interface와 Polymorphism
다형성은 여러 데이터 타입들을 동일한 방식으로 다룰 수 있게 하는 기능을 의미한다. 다형성은 코드를 더 유연하고 재사용 가능하게 만들어준다.

### 2. Empty Interface
빈 인터페이스는 어떤 타입도 담을 수 있는 컨테이너이다. 빈 인터페이스는 메서드를 정의하지 않기 때문에 모든 타입이 이 인터페이스를 구현한 것으로 간주된다.
이를 사용하면 어떤 타입도 변수에 할당할 수 있기 때문에 일반적으로 제네릭, 임의의 데이터 저장, 다양한 타입을 처리할 때 유용하다.

- **다양한 타입의 값 저장**: 빈 인터페이스를 사용하여 다양한 타입의 값을 저장할 수 있다.
- **다양한 타입의 값 처리**: 빈 인터페이스를 사용하여 다양한 타입의 값을 처리할 수 있다.
- **제네릭한 함수 구현**: 특정 타입에 구애받지 않고 제네릭한 함수를 구현할 수 있다.

빈 인터페이스는 사용하는 곳에서의 해당 타입을 알 수는 없기 때문에 값을 사용할 때 ```type assertion```이나 ```type switch```를 통해 원래의 타입을 확인하고 사용해야 한다.

- 예제
```
// 정의된 타입 구조체
type Person struct {
	Name string
	Age  int
}

type Animal struct {
	Species string
	Age     int
}

// 입력된 값을 구조체와 비교하는 함수
func compareStructs(i interface{}) {
	switch v := i.(type) {
	case Person:
		fmt.Printf("Value is a Person: %+v\n", v)
	case Animal:
		fmt.Printf("Value is an Animal: %+v\n", v)
	default:
		fmt.Printf("Unknown type: %T\n", v)
	}
}

func main() {
	// 다양한 타입의 값을 담을 수 있는 빈 인터페이스 슬라이스
	var i interface{}

	// Person 구조체와 비교
	i = Person{Name: "Alice", Age: 30}
	compareStructs(i) // Value is a Person: {Name: Alice Age: 30}

	// Animal 구조체와 비교
	i = Animal{Species: "Dog", Age: 5}
	compareStructs(i) // Value is an Animal: {Species: Dog Age: 5}

	// 기타 타입과 비교
	i = "Hello"
	compareStructs(i) // Unknown type: string
}
```

### 출처(참고문헌)
-

### 연결문서
-