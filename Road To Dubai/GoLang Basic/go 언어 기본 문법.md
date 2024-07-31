
### 날짜 : 2024-07-26 19:11

### 주제: 

---
### 메모: 

## 0. Numerics
integer, floating-point, complex, rune

### 1. int
##### general types
int: OS에 따라 크기가 달라짐. 
uint: 양의 정수

##### specific types
specific type은 비트 길이를 명시적으로 지정할 수 있다.
int8: -128 ~ 127
int16: -32768 ~ 32767
int32(=rune): 
int64: 

##### special types
byte: uint8의 별칭
rune: int32의 별칭
uintptr: //검색

### 2. float & complex
go는 부동소수점과 복소수를 지원한다. 

##### float types
go에서 제공하는 float type은 2가지이다.
```
float32: 32비트 부동 소수점 자리를 나타낸다.
float64: 64비트 부동 소수점 자리를 나타낸다.
```

*정밀도의 한계 때문에 float 타입은 실수의 대략적인 표현만 제공*

##### complex types
```
complex64: 2개의 float32 값 (실수, 허수)로 구성
complex128: 2개의 float64 값 (실수, 허수)로 구성
```
go에서 제공하는 complex 사용 내장함수
```
complex(r,i): 실수 부분 r, 허수 부분 l 복소수 생성
real(c): complex c의 실수부 return
imag(c): complex c의 허수부 return
```

실수(허수) 부분이 float32면 복소수는 complex64
실수(허수) 부분이 float64면 복소수는 complex128

## 1. String
Go에서 ```string```은 UTF-8로 인코딩되는 읽기 전용 바이트 시퀀스이며 불변이다.
이게 무슨 뜻이면 문자열을 읽고 쓰는 건 가능하지만 string을 수정할 수는 없다.

- UTF-8 인코딩: string은 UTF-8로 인코딩 되므로 모든 유니코드 문자를 나타낼 수 있다.
- 불변성: 문자열은 한 번 생성되면 수정할 수 없다. 모든 작업은 새로운 문자열을 생성한다.
- 길이 및 인덱싱: go에서 문자열은 바이트로 계산된다. len함수는 문자열의 바이트 수를 반환한다. 
  문자열에 인덱스로 접근하면 문자의 위치가 아닌 바이트의 위치로 접근한다. 따라서 해당 위치의 문자를 반환하는 것이 아닌 그 문자의 바이트 정보를 반환한다. 
  
- 예시
```
var s string = "안녕하세요"

fmt.Println("바이트 단위 접근:")
for i := 0; i < len(s); i++ { 
	fmt.Printf("%d ", s[i]) 
} 

fmt.Println("문자 단위 접근:") 
for _, r := range s { 
	fmt.Printf("%c ", r) 
} 

// 문자열의 바이트 길이 
byteLength := len(s) 
fmt.Printf("바이트 길이: %d\n", byteLength) 

// 문자열의 문자 길이 
runeLength := len([]rune(s)) 
fmt.Printf("문자 길이: %d\n", runeLength)
```
- 결과
```
바이트 단위 접근:
236 149 136 235 133 149 237 149 152 236 132 184 236 157 180 
문자 단위 접근:
안 녕 하 세 요 

바이트 길이: 15
문자 길이: 5
```

## 2. String Formatting
fmt 패키지는 형식을 지정해서 문자열을 출력할 수 있는 ```fmt.Printf```등의 함수를 제공한다. 

| format specifier |               description               |
| :--------------: | :-------------------------------------: |
|        %v        |         value (default format)          |
|        %T        |             해당 value의 type              |
|        %x        |          Hexadecimal encoding           |
|        %d        |            Integer (base 10)            |
|        %f        |          Floating-point number          |
|        %e        |     Scientific notation (lowercase)     |
|        %E        |     Scientific notation (uppercase)     |
|        %p        |      Pointer가 가리키는 변수의 주소 (포인터의 값)      |
|        %s        |                 String                  |
|        %c        | Unicode 코드 포인트로 표시되는 문자 (유니코드에 해당하는 문자) |

## 3. Boolean
boolean은 true, false가 있다. go에서 boolean은 특징을 가진다.
- 기본값: bool 타입 변수는 기본적으로 false이다.
- 비교 연산자: 여러 비교 연산자의 결과로 표현될 수 있다.
- 논리 연산자: 여러 논리 연산자로 논리 연산을 표현할 수 있다.

### 4. 변수 선언 및 초기화 하기
go에선 여러가지 방법으로 변수를 정의하고 초기화 할 수 있다.
```
var s string = "initial"
```
또는 := 연산자와 함께 shorthand 표기법으로 선언할 수도 있다.
```
변수명 := 값
```
':=' 연산자는 함수 내에서만 사용 가능하다.
이렇게 선언하면 변수 타입을 명시적으로 지정하지 않고도 변수를 선언할 수 있다.
고 언어 컴파일러가 값의 타입을 자동으로 추론해서 변수에 할당한다.
#### 초기화 없이 여러 변수 선언
```
var (
    a, b int
    s string
    c complex64
)
```
// 이는 각 변수를 개별적으로 선언하는 것과 같다. 
// 초기화하지 않으면 변수는 타입에 따라 0이라는 값을 갖는다.
```
var a, b int
var s string
var c complex64
```

#### 상수 정의하기
고 언어에서 상수를 선언할 때, 데이터 타입을 명시적으로 지정하지 않아도 된다. 이는 고 언어의 상수는 "타입이 없는 상수(untyped constant)"로 간주될 수 있기 때문이다. 이러한 상수는 사용되는 문맥에 따라 적절한 타입으로 자동으로 변환된다. 그러나 필요에 따라 명시적으로 타입을 지정할 수도 있다.

```
const hello = "Hello, World!"
```

## 5. Function
- 함수를 사용하면 캡슐화를 통해 코드의 재사용성을 높일 수 있다.
- 함수는 0개 이상의 매개변수와 0개 이상의 반환값을 받을 수 있다.
함수를 정의하고 사용하는 법은 다음과 같다.
```
func functionName(parameterName parameterType) returnType {
    // function body
    return value
}
```

## 6. Struct
구조체는 하나의 이름으로 '변수'를 그룹화하는 복합 데이터이다. 이런 변수를 필드라고 한다.
구조체는 클래스와 유사하지만 상속을 지원하지 않는다.

```
type StructName struct {
    field1 fieldType1
    field2 fieldType2
    // more fields...
}
```
Go는 다른 객체지향언어처럼 클래스를 지원하지 않는다. 다이아몬드 상속과 같은 문제가 있기 때문이다. 그래서 구조체를 만들었다.

- **상속 없음**: 상속 지원 X, 대신 컴포지션을 사용하여 코드 재사용
- **캡슐화**: 접근 지시자 X, 대문자로 필드 이름 표기로 public을 나타냄
- **메서드**: 구조체 내에 메서드 정의 X. 외부에서 구조체 타입과 연관
## 7. Method
메서드는 function과 유사하지만 특정 타입(일반적으로 구조체)과 연관되어 있다. 

메서드는 타입의 동작을 정의한다. 그게 구조체든 뭐든
그리고 구조체의 필드에 접근하고 동작을 정의할 수 있다.
그래서 흔히 구조체와 함께 사용된다.

```
type TypeName struct {
    // fields
}

func (receiver TypeName) methodName(parameters) returnType {
    // method body
}
```
#### 객체지향의 Class와 Go의 method 비교
- Receiver: 클래스에서 메서드가 객체와 연관되는 것과 비슷하게 receiver라는 특정 타입에 속하도록 만들어주는 특별한 인자를 사용한다.
- this: go에는 암시적 this 키워드가 없다. 대신 명시적으로 receiver 이름을 사용한다.
- Pointer Receiver: 클래스에서 객체의 상태에 접근하는 것과 유사하게 포인터를 인자로 넘겨받아서 값을 직접 수정할 수 있다.

## 8. Pointer
포인터는 다른 변수의 메모리 주소를 저장하는 변수이다.
포인터를 사용해 실제 변수의 위치에 접근하고 값을 변경할 수 있다.

- 주소 연산자 & : 변수의 주소를 가져온다
- 역참조 연산자 $*$ : 포인터가 가리키는 주소의 값을 가져온다
- 값의 변경 : 포인터를 통해 값을 변경하면, 해당 주소에 저장된 값이 실제로 변경된다
```
var ptr *int
ptr = &variable
```
```*int```: 포인터의 타입. int 형 변수를 가리킨다는 뜻.
```&variable```: 변수의 메모리 주소를 반환한다.

## 9. Closure
클로저는 함수가 자신이 정의된 환경을 캡처하고 기억하여, 함수 밖에서 호출 되더라도 내에서 정의된 함수로, 외부 함수의 변수에 접근할 수 있는 기능이 있다.


### 출처(참고문헌)
-

### 연결문서
-