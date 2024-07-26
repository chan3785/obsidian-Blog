
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
- float32: 32비트 부동 소수점 자리를 나타낸다.
- float64: 64비트 부동 소수점 자리를 나타낸다.
*정밀도의 한계 때문에 float 타입은 실수의 대략적인 표현만 제공*

##### complex types

```
complex32: 
-complex64: 
```
### 출처(참고문헌)
-

### 연결문서
-