
### 날짜 : 2024-05-13 20:17

### 주제: 

---
### 메모: 
### 공통 요소
1. ==Logo== $\rightarrow$ 시작 페이지로 이동
2. ==connect wallet button== 
	  지갑 연결 false $\rightarrow$ wallet connect (구현 완료)
	  지갑 연결 true $\rightarrow$ PP Logo + 보유 포인트 (단위: pp)
3. ==sign up button== 
	  계정 확인 false $\rightarrow$ sign up 페이지로 이동 
	  계정 확인 true $\rightarrow$ wallet logo + 지갑주소 6자리 + 프로필 이미지
   => 상단 바 메뉴
   
### 시작 페이지
1. Find your mission $\rightarrow$ mission menu 페이지로 이동
2. 하단바 (여타 adf 서비스와 같음) 
	컴포넌트로 제공 가능한가요 ?
	
- Find your mission 버튼을 눌렀을 때 계정 확인을 해서 없으면 navigate 되는 페이지랑 sign up 버튼 누르고 navigate 되는 페이지랑 같은가?

###  Sign Up 페이지
1. Go to Artiside button $\rightarrow$ Artiside Sign up 페이지로 이동
2. Sign Up with Wallet connect $\rightarrow$ wallet connect (월렛 커넥트 버튼 복제)

- artiside에서 connect 하고 넘어온 다음 다시 여기서 connect 하는 건지,
- artiside에서 connect 하면 넘어와도 유지되게 만드는 건지,
- artiside에서 wallet connect 하지 않고 sign in 한 뒤에 여기 와서 connect 하는 건지 (소셜 로그인)
- 기존의 계정을 가지고 있던 유저는 어떻게 처리하는 건지
  (非 sei wallet 유저들, 현재 wallet connect에 sei wallet module 없는 듯 함)

### Mission Menu 페이지
1. Referral Code $\rightarrow$ (미정) 팝업에 유저정보로 만든 or 유저에게 저장된 Referral code 보여주고 클립보드 복사 버튼도 옆에 (모달)
2. . Referral Link $\rightarrow$ (미정)

- Referral link 버튼을 누르면 링크만 보여줄 것인가?
- link 버튼을 눌렀을 때, 복사 가능한 링크랑 sns 공유 버튼을 보여줄 것인가?
- 
#### 2. Mission Tab 
1. 미션 상태 tab
	1. All (미완 / 전체)
	2. Ongoing (내가 진행 중 / 전체 진행 중) $\rightarrow$ 기간으로 ongoing / done 여부 판단
	3. Done (유저가 클리어 한 것 /  기간이 끝난 것)
	4. Next (예정) 시간 기준
2. 미션 카테고리 tab
	1. Referral 
		   
	2. Social
	3. Artiside
	4. Seeding
	5. Launchpad
	6. The Flux
	7. KYC
3. 



### 출처(참고문헌)
-

### 연결문서
-