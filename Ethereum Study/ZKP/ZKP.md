
### 날짜 : 2024-08-08 11:22

### 주제: 

---
### 메모: 
### Verifiable computing
computing(계산)이란? (C,S)
프로그램 : 순서가 있는 명령어 벡터

프로그램 실행은 어떤 과정이냐
프로그램 definition과 parameter를 실행하는 게 execution
exec는 프로그램 def에 param을 넣는 과정을 증명할 수도 있다.
나이브하게는 빈칸에 파라미터를 넣어보는 것이다.
이것을 verify 한다고 한다. 같은 결과가 나오는지

exec 하는데도 cost가 발생했을 거고
검증하는데도 cost가 발생했을 것이다.
Cexe >> Cver 를 만들려고 하는 노력의 총칭을 Verifiable Computing이라는 분야이다.

클라우드 컴퓨팅이 생기기 시작했을무렵에
고객이 가진 단말에서 헤비한 컴퓨팅을 하기는 쉽지 않다는 것을 알았다.
예를 들면 머신러닝 모델 트레이닝 등등 고객이 가진 기기에서는 쉽지 않다

train(md,data) 하는 것도 comp다

어떤 DataSet과 Model을 training 시켜달라고 외주를 줬는데 그 결과를 믿을 수 있느냐
검증하려면 직접 해보는 건데 그럼 외주를 왜 맡기냐
이걸 위해서 있는 게 V. C.

#### 다항식
인지하고 있는 대상을 다항식으로 표현해서 유통을 하거나 하면 몇가지 benefit이 있다
다항식을 안다 = coefficient를 안다
현실에 있는 것을 다항식으로 만들어서 표현하면 필요에 따라 압축을 할 수 있다.
A랑 B랑 대화를 하는 맥락에서 P(x)로 만든 대상에 대해서 얘기하고 있는데 
그 대상에 대해 계속 얘기를 하고 있는지 아닌지를 특정 점 하나를 합의해보는 것으로 확인을 할 수 있다.
특정 점에 대해 합의를 하고 그 점을 알고 있느냐로 확인을 할 수 있다는 뜻

우리는 다항식의 형태로 represetation을 해서 그 다항식을 가지고 다닐 거다.

제가 의뢰한 ml md train을 제가 의뢰한 data로 학습 시켰나요?
네 train 했습니다 -> 를 다항식으로 만들 것이다.

어떤 다항식을 마음 속으로 정했다. 그게 뭔지는 안 알려줄 거다.
그리고 맹세했다. 
B가 3을 주면 P(3)에 대한 결과를 반환해 준다.
7을 주면 P(7)에 대한 결과를 반환해 준다.
다항식에 commit을 한다. 그리고 값들이 오면 모두 대답할 수 있어야 한다.
P가 뭔지는 말을 하지 않은 채로

어떤 수 S를 먼저 합의를 해두고 P(S) 점을 계산해두고 이걸 먼저 A가 B에게 전해준다.
이게 암호학적 관점에서 commit C이다
A: S
B: C=P(S)

B가 알파라는 값을 준다. evalutae 해봐라
A는 P($\alpha$)를 계산했더니 a가 나왔다.
P(x) - a / (x-$\alpha$) 했을 때 나뉘어져야 한다.
x에다 S를 대입해도 똑같이 나뉘어진다.
S, C, 알파, a, P(s) - a / P(S - 알파)도 알고 있다.

그럼 검증은 어떻게?

저 위의 값들이 A에 의해서 evaluate 돼서 B에게 던져진 것인데
원래 다항식 P에 대해서 정말로 A가 제대로 계산을 했는지 확인을 하려면
P(s) - a / P(S - 알파)
C - a를 S(합의한 값) - 알파

어떤 다항식 P(x)가 있는데 
그 다항식으로 A와 B가 소통하는데 있어서 A가 다항식을 쥐고 공개를 하고 싶어하지 않는다
선언한 다항식에서 B는 어떤 값을 계산하는 것이 목적

$g^{q(s) x (s - \alpha)} = g^p(s) - a$이면 높은 확률로 증명이 됐다라고 하는 프로토콜이다

## ZKP
목표: 프로그램이 있고 그걸 실행했을 때 프로그램 빈칸에 파라미터를 넣을 수 있는지 적법한 절차로 계산을 했는지 증명
1. 실행 비용보다 검증 비용이 기하급수적으로 낮아야 한다.
2. 외주 대행자를 보호해줘야 한다. intermediate values -> encrypt

여러가지 연산을 포함하는 코드를 
a x b x c라는 프로그램으로 reduce했다고 하자.

m1 = a x b
m2 = m1 x c
를 pgm을 실행하는 과정이다라고 해보자

3 , 2, 4를 통해 아웃풋 m2 24가 모든 파라미터를 넣어서 적법한 절차로 연산했는지 증명해보고 싶다.
이게 영지식이다.

계산을 한다고 하는 거는 회로에 들어가는 와이어에 적법한 밸류를 흐르게 하는 것이랑도 비슷하다

저 연산을 타겟 벡터 t 내적 v 곱하기 타겟벡터 t 내적 w는 t 내적 k다
$t\cdot v X t \cdot w = t \cdot k$

타겟 벡터는 선태의 대상이 되는 밸류 모음
t = ```[a,b,c,m1,m2]```

3,2,4,6,24라는 걸 실행을 한 사람은 알 수 있다
그러면 v는 어떻게 되는가
한개 한개 각각의 값이 게이트 와이어에 대응이 되고 있다.
G1 : t내적v x t내적w = t내적k
v:L ```[1,0,0,0,0]```
w:R ```[0,1,0,0,0]```
k:O ```[0,0,1,0,0]```

v의 첫번째 자리를 보면 g1에서 1, g2에서 0
v의 2번째 자리를 보면 g1에서 0, g2에서도 0
v1(x)를 구하고 싶다 정하고 싶다
라그랑주 보강법을 사용하면 점 2개를 지나는 유니크한 다항식을 만들 수 있다
그렇게 v1부터 v5까지 생성이 될텐데
이 다항식들의 특징은 
게이트를 선택한 순간 와이어를 볼 수 있다. 다른 값은 다 죽어서
타겟벡터를 적법하게 완성하는 사람만이 Px를 알 수 있게 될 것이다.

아웃풋으로 받은 q(s)에 h(s)를 곱해서 p(s)값이 나오면 증명이 된다.
수많은 파라미터를 넣어서 연산을 한 것을 한번 내지 두 번의 연산으로 증명할 수 있게 된다.

### Zero-Knowledge Proof (verifiable computing)
블록체인과의 접점이 어떻게 될 것인가
1. privacy
2. scalability
이것 조차도 족쇄 상상하기 나름의 문제를 풀 수도 있을 것이다.

타원곡선에서 스스로 더하는 연산을 스칼라 곱으로 하기로 했다.
g를 스스로 더하는 연산을 seed phrase만큼 스칼라 곱을 하면 나오는 점 P의 x 좌표가 퍼블릭키가 된다

머클 증명
특정 원소가 집합의 원소인지 아닌지 효율적으로
최악의 경우 O(n)으로 집합의 원소를 모두 가지고 다닌다

멤버십 증명
seed phrase를 가진 사람이 증명을 할 수 있다. rt를 만들 수 있으면 이 사람은 거기에 주소를 가진 사람이구나

zk-regex

circom은 빠르게 circuit을 빠르게 설계하고 컴퓨터 설계 경험이 적으면 아주 굿
좀 더 복잡하게나 설계를 더 해야 할 때 arkworks라는 툴 추천
온체인 데이터 같은 큰 데이터를 처리하는 circuit을 define 해야 할 때 
halo2 추천


### 출처(참고문헌)
-

### 연결문서
-