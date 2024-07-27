
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


### 출처(참고문헌)
-

### 연결문서
-