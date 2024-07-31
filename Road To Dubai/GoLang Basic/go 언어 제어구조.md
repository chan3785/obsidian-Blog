
### 날짜 : 2024-07-31 22:30

### 주제: 

---
### 메모: 
## 목차
1. 조건문: if, else if, else
    1. 기본 if 문
    2. if-else 문
    3. if-else if-else 문
    4. 조건문 내 변수 선언

2. 반복문: for, break, continue
    1. 기본 for 문
    2. 조건식만 있는 for 문
    3. 무한 루프: 정지 판별 문제
    4. range를 사용한 for 문
    5. break와 continue
3. switch 문
    1. 기본 switch 문
    2. 여러 값을 검사하는 switch 문
    3. 조건식을 사용하는 switch 문
    4. fallthrough

## 1. 조건문: if, else if, else
#### 1. 기본 if 문
```
func main() {
	x := 10
	if x > 5 {
		fmt.Println("x is greater than 5")
	}
}
```
괄호가 없이 사용하는 게 이색적이다
#### 2. if - else 문
```
func main() {
	x := 3
	if x > 5 {
		fmt.Println("x is greater than 5")
	} else {
		fmt.Println("x is not greater than 5")
	}
}
```

#### 3. if-else if-else 문
```
func main() {
	x := 8
	if x < 3 {
		fmt.Println("x is less than 3")
	} else if x < 7 {
		fmt.Println("x is less than 7 but greater than or equal to 3")
	} else {
		fmt.Println("x is greater than or equal to 7")
	}
}
```
### 출처(참고문헌)
-

### 연결문서
-