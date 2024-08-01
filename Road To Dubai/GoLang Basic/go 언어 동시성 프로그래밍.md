
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

### 1. goroutine과 channel
#### 1. 고루틴 (goroutine)
고루틴은 경량 스레드로, ```go```키워드를 사용해서 쉽게 생성할 수 있다.
### 출처(참고문헌)
-

### 연결문서
-