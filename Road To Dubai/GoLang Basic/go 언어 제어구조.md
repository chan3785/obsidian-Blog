
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

#### 1. 기본 switch 문
기본 switch 문은 하나의 변수 값을 여러 case와 비교해서 일치하는 경우에 해당 코드 블록을 실행한다.
```
func main() {
	x := 2
	switch x {
	case 1:
		fmt.Println("One")
	case 2:
		fmt.Println("Two")
	case 3:
		fmt.Println("Three")
	default:
		fmt.Println("Other")
	}
}
```
- `switch x`: x의 값을 평가한다.
- `case 1`, `case 2`, `case 3`: x의 값이 각각 1, 2, 3과 일치할 때 실행할 코드 블록을 정의한다.
- `default`: 어떤 case 절에도 해당하지 않을 때 실행할 코드 블록을 정의한다.

#### 2. 여러 값을 검사하는 switch 문
여러 값을 검사하는 switch 문에서는 각 case에 여러가지 값을 포함할 수 있다.
이렇게 하면 동일한 수행을 여러 값에 대해서 해야 할 때 유용하다.
```
func main() {
	x := 4
	switch x {
	case 1, 3, 5:
		fmt.Println("Odd")
	case 2, 4, 6:
		fmt.Println("Even")
	default:
		fmt.Println("Other")
	}
}
```

- `case 1, 3, 5`: x의 값이 1, 3, 5 중 하나일 때 "Odd"를 출력한다.
- `case 2, 4, 6`: x의 값이 2, 4, 6 중 하나일 때 "Even"을 출력한다.
- `default`: x의 값이 나열된 값에 해당하지 않을 때 "Other"를 출력한다.

#### 3. 조건식을 사용하는 switch 문
조건식을 사용하는 switch 문에서는 각 case에 조건식을 사용할 수 있다.
이 방식은 특정 값 뿐만 아니라 복잡한 조건을 처리할 때 유용하다.

```
func main() {
	x := 10
	switch {
	case x < 5:
		fmt.Println("x is less than 5")
	case x < 10:
		fmt.Println("x is less than 10 but greater than or equal to 5")
	default:
		fmt.Println("x is 10 or more")
	}
}
```

- `switch`: switch 키워드 뒤에 아무것도 명시하지 않아도 된다. 각 case 절에서 직접 조건을 평가한다.
- `case x < 5`: x가 5보다 작으면 "x is less than 5"를 출력한다.
- `case x < 10`: x가 10보다 작고 5 이상이면 "x is less than 10 but greater than or equal to 5"를 출력한다.
- `default`: x가 10 이상이면 "x is 10 or more"를 출력한다.

#### 4. fallthrough
fallthrough는 go의 switch문에서 사용되는 특별한 키워드로, 현재 case가 실행되면 다음 case를 강제로 실행하게 한다. 
즉, fallthrough를 사용하면 조건을 검사하지 않고 다음 case를 실행한다.
```
func main() {
	x := 1
	switch x {
	case 1:
		fmt.Println("One")
		fallthrough
	case 2:
		fmt.Println("Two")
		fallthrough
	case 3:
		fmt.Println("Three")
	default:
		fmt.Println("Other")
	}
	// One 
	// Two
	// Three
}
```
- `case 1`: x가 1인 경우 "One"을 출력한 후 fallthrough 키워드에 의해 다음 case 절(즉, case 2)을 실행한다.
- `case 2`: 조건을 검사하지 않고 "Two"를 출력한 후 다시 fallthrough 키워드에 의해 다음 case 절(즉, case 3)을 실행한다.
- `case 3`: 조건을 검사하지 않고 "Three"를 출력한다.
- `default`: fallthrough에 의해 다음 case 절이 없을 때 실행된다. 위 코드에서는 실행되지 않는다.

fallthrough는 오직 다음 절로만 강제로 실행을 넘길 수 있다.
따라서 현재 case의 끝에서만 사용할 수 있으며, 다중으로 사용은 허용되지 않는다.

fallthrough를 사용할 경우, 다음 case의 조건은 검사되지 않으므로 논리적 오류를 방지하기 위해 신중하게 사용해야 한다.
### 출처(참고문헌)
-

### 연결문서
-