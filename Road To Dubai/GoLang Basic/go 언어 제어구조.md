
### 날짜 : 2024-07-31 22:30

### 주제: 

---
### 메모: 
### 목차
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

### 1. 조건문: if, else if, else
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
		fmt.Println("x is less than 7 but greater than 3")
	} else {
		fmt.Println("x is greater than or equal to 7")
	}
}
```

#### 4. 조건문 내 변수 선언
if 문 내에서 변수 선언도 가능하다.
단, 이 변수는 if문 scope 내에서만 유효하다.
```
func main() {
	if x := 10; x > 5 {
        // x 존재 
		fmt.Println("x is greater than 5")
	}
    // x 존재하지 않음
}
```

### 반복문: for, break, continue
go에서는 유일한 반복문으로 for문을 사용한다.
다양한 방식으로 반복문을 사용할 수 있다.
#### 1. 기본 for 문
초기화, 조건, 후처리를 포함한 기본적인 형태이다.
```
func main() {
	for i := 0; i < 5; i++ {
		fmt.Println(i)
	}
}
```

#### 2. 조건문만 있는 for 문
초기화와 후처리를 포함하지 않고 조건식만 있는 형태도 가능하다.
```
func main() {
	i := 0
	for i < 5 {
		fmt.Println(i)
		i++
	}
}
```

#### 3. 무한 루프
반복문에 조건을 명시하지 않으면 무한히 반복되는 무한 루프를 만들 수 있다.
```
func problematicFunction() {
	for {
		// Infinite loop
		fmt.Println("This function never halts.")
	}
}
```

#### 4. range를 사용한 for 문
배열, 슬라이스, 맵, 채널 등을 순회할 때 사용한다. 다음은 `nums` 슬라이스의 각 요소에 대해 인덱스 i와 값 num을 반복하는 예시 코드이다.
약간 C#에 foreach문과 비슷한 것 같다.
```
func main() {
	nums := []int{2, 3, 4}
	for i, num := range nums {
		fmt.Printf("Index: %d, Value: %d\n", i, num)
	}

	m := map[string]string{"a": "apple", "b": "banana"}
	for k, v := range m {
		fmt.Printf("Key: %s, Value: %s\n", k, v)
	}
}
```

#### 5. break, continue
break는 반복문을 종료하고 continue는 다음 반복으로 건너뛴다.
```
func main() {
	for i := 0; i < 10; i++ {
		if i == 5 {
			break
		}
		if i%2 == 0 {
			continue
		}
		fmt.Println(i)
	}
}
```


### switch 문
go에서 switch문은 하나 이상의 조건을 순서대로 판단해서 일치하는 case의 블록을 실행하는 구조이다. 
각 case 절에 해당하지 않으면 default 절을 실행한다.

#### 기본 switch 문

### 출처(참고문헌)
-

### 연결문서
-