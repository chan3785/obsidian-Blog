
### 날짜 : 2024-08-02 00:54

### 주제: 

---
### 메모: 
### 목차

1. 고루틴(goroutine)과 채널(channel)
    1. 고루틴(goroutine)
    2. channel
    3. 송신 전용 및 수신 전용 channel
2. channel을 이용한 동시성 제어
    1. 버퍼링된 channel
    2. channel을 이용한 작업 분배
3. select 문
4. sync 패키지 사용
    1. WaitGroup
    2. Mutex
5. 클로저(closure)와 동시성
    1. closure 없는 잘못된 고루틴
    2. closure 고루틴

## 1. goroutine과 channel
### 1. 고루틴 (goroutine)
고루틴은 경량 스레드로, ```go```키워드를 사용해서 쉽게 생성할 수 있다. 
고루틴은 매우 가볍고, 수천 개의 고루틴을 생성해도 성능에 큰 영향을 주지 않는다.
##### 고루틴의 특징
- **경량 스레드**: 고루틴은 운영 체제의 스레드보다 훨씬 가볍습니다. 고 언어 런타임이 고루틴을 관리하며, 필요에 따라 운영 체제의 스레드 풀에서 스레드를 할당합니다.
- **비동기 실행**: 고루틴은 다른 고루틴과 비동기적으로 실행됩니다. `go` 키워드를 사용하여 함수를 호출하면 새로운 고루틴이 생성되어 실행됩니다.
- **채널(Channel)**: 고루틴 간의 통신과 동기화를 위해 채널을 사용합니다.

### 2. 채널 (Channel)
채널은 고루틴 간 통신을 위한 도구이다. 채널을 사용하면 고루틴끼리 데이터를 주고 받을 수 있다.
**채널은 타입을 지정해서 선언하고 make 함수를 사용해서 생성한다.**
##### 채널 특징
- 동기화: 채널을 통해 값을 주고 받을 때, 고루틴 간 동기화가 이루어진다.
- 방향성: 채널은 양방향이거나 송신 전용, 수신 전용으로 선언할 수 있다.
###### 예제 코드
```
func main() {
	// 채널 생성
	ch := make(chan int)

	// 고루틴에서 채널에 값 보내기
	go func() {
		ch <- 42
	}()

	// 채널에서 값 받기
	val := <-ch
	fmt.Println(val) // 42
}
```

#### 송신 전용 및 수신 전용 채널
채널은 송신 전용, 또는 수신 전용으로 선언할 수 있다.
송신 전용 채널은 데이터를 보내기만 할 수 있고
수신 전용 채널은 데이터를 받기만 할 수 있다.

###### 예제 코드
```
func send(ch chan<- int, val int) {
	ch <- val
}

func receive(ch <-chan int) int {
	return <-ch
}

func main() {
	ch := make(chan int)

	go send(ch, 42)
	val := receive(ch)
	fmt.Println(val) // 42
}
```
### 3. Channel을 이용한 동시성 제어
#### 1. 버퍼링 된 channel
버퍼링 된 채널은 고루틴 간의 통신을 할 때 메시지를 저장할 수 있는 공간을 제공하는 채널이다.
일반적인 비 버퍼링 채널과 달리, 지정된 크기의 버퍼를 가지고 송신자가 수신자의 준비 여부에 상관없이 데이터를 채널에 보낼 수 있다.
##### 버퍼링된 채널의 특징
- **비동기 송신**: 송신자가 버퍼가 가득 차지 않는 한 데이터를 채널에 보낼 때 블로킹되지 않습니다.
- **비동기 수신**: 수신자가 버퍼가 비어 있지 않는 한 데이터를 채널에서 받을 때 블로킹되지 않습니다.
- **버퍼 크기 지정**: 채널을 생성할 때 버퍼의 크기를 지정할 수 있습니다.

#### 2. channel을 이용한 작업 분배
채널을 사용하여 여러 고루틴에 작업을 분배할 수 있다.
작업자 패턴은 채널을 사용하여 여러 고루틴에 작업을 분배하는 방법이다.
여러 고루틴이 작업을 분배받아 동시에 실행할 수 있도록 한다.
###### 예시 코드
```
// 작업자 함수
func worker(id int, jobs <-chan int, results chan<- int) {
	for j := range jobs {
		fmt.Printf("worker %d started job %d\n", id, j)
		time.Sleep(time.Second)
		fmt.Printf("worker %d finished job %d\n", id, j)
		results <- j * 2
	}
}

func main() {
	const numJobs = 5
	jobs := make(chan int, numJobs)
	results := make(chan int, numJobs)

	// 3개의 작업자 고루틴 생성
	for w := 1; w <= 3; w++ {
		go worker(w, jobs, results)
	}

	// 작업 채널에 작업 보내기
	for j := 1; j <= numJobs; j++ {
		jobs <- j
	}
	close(jobs)

	// 결과 받기
	for a := 1; a <= numJobs; a++ {
		fmt.Printf("result: %d\n", <-results)
	}
}
```

#### 3. select 문
select 문은 여러 채널 작업을 기다리고, 그 중 하나가 준비되면 해당 작업을 실행한다.
이는 다중 채널 동작을 제어하는 데 유용하다.
select 문에서 default 케이스를 사용하면 모든 채널이 준비되지 않은 경우에도 즉시 실행된다.
###### 예시 코드
```
func main() {
	ch := make(chan int, 1)
	ch <- 1
	select {
	case val := <-ch:
		fmt.Println("received", val)
	default:
		fmt.Println("no value received")
	}
}
```

#### 4. sync 패키지 사용
go의 sync 패키지는 동시성 프로그래밍을 위한 여러 도구를 제공한다. 여기에는 WaitGroup, Mutex, Once 등이 포함된다.
WaitGroup은 여러 고루틴의 완료를 기다릴 때 사용한다.

#### 5. Mutex
mutex는 임계 구역을 보호하여 동시 접근을 제한한다.
예) race condition 등

#### 6. 클로저와 동시성
클로저는 고루틴과 채널을 사용할 때 중요하다. 클로저는 실행 컨텍스트를 벗어난 상태에서도 동일한 실행 컨텍스트를 사용할 수 있도록 하는 기능이다.
그러므로 함수 내에서 외부 변수에 접근해 고루틴이 상태를 유지하거나, 공유상태를 안전하게 변경할 수 있게 한다.

###### 1. 클로저 없는 잘못된 고루틴
고루틴 내에서 클로저를 사용할 때, 클로저가 외부 변수의 참조를 캡처해 사용한다는 점을 주의해야 한다. 이는 의도치 않은 동작을 야기할 수 있다.


### 출처(참고문헌)
-

### 연결문서
-