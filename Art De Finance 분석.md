
### 날짜 : 2024-05-09 18:19

### 주제: #adf 

---
### 메모: 
### ARTDEFINANCE 
1. 상단 우측 3개 버튼 $\rightarrow$ 각각 사이트로 이동 (프론트) 
2. 화면 중앙 비디오 삽입
3. 스크롤에 따라 동적으로 변하는 화면 
4. 로드맵 년도 버튼에 따라 변하는 내용
5. 커뮤니티 (디스코드, 트위터, 미디움, 닥스, 텔레그램 등등)
6. 미디움 글 나열
7. FAQ 자주 묻는 질문 
8. 파트너스
9. 밑에 기업 소개? 컨택? 

### ARTISIDE 
1. 스폰서 사이트 링크 모음
	(Art de finance, The flux, Adf partners)
2. Tab 버튼 4개 
	(Creation (default), Feed, Seeding, Launchpad)
3. 검색창 
	(Creators, artworks, inspiration 세 개의 항목에 대해서 다)
4. 로그인 - 지갑
	계정 없을 시 - 회원가입 페이지(모달)
	유저네임 입력 ![[Pasted image 20240509183021.png]]
	![[Pasted image 20240509183051.png]]
	완료되면 메인화면으로
	지갑주소로 유저 구분 $\rightarrow$ 새 지갑으로 연결하니까 새로 회원가입
	구글 로그인은 지원 안되는 듯
	무조건 지갑으로 로그인
	sign in => 모달
	sign up => 페이지
5. 로그인 되어 있을 때
	지갑주소(뒷부분 생략) + 프로필 이미지
	![[Pasted image 20240509231214.png]]
	
6. Create 버튼 클릭시
	 한 주 동안 투토리얼 2페이지 (모달) $\rightarrow$ hide for a week, start
	 ![[Pasted image 20240509185452.png]]
	 사진 파일 업로드, 타이틀, 디스크립션 $\rightarrow$ upload
	 다른 어떤 조건도 없이 업로드 가능
	 업로드 시 작품페이지로 이동
	 파일유형: jfjf, pjpeg, jpeg, pjp, jpg, png, heif, gif, svgz, svg
	

#### ARTISIDE Creation Page
1. Inspiration 작품페이지 
	이미지, 타이틀, 박수 수(클릭가능), 뷰 수, 작성자 + 팔로우 버튼, 작성자가 적은 작품 description, 몇분전 (백엔드)
	업로드	작품에 대한 박수(취소가능), 작품 저장(취가), 작품 공유 (link copy만)
	댓글: 유저, 내용, 몇분전 시간, 대댓글(@유저네임 언급), 하트(취소가능), 
	삭제(본인이면), 신고(본인 아니면)
2. Artworks 작품페이지
	이미지, 타이틀, 박수 수(클릭가능), 뷰 수, 아티스트(작성자) + 인증마크 + 팔로우 버튼, About Artworks(디스크립션)
	박수, 저장, 공유
	댓글: 유저, 내용, 몇분전 시간, 대댓글(@유저네임 언급), 하트(취소가능), 
	삭제(본인이면), 신고(본인 아니면)
	마켓플레이스로 이동(또는 판매하지 않는 상품입니다)
	레드라벨 버튼(커밍쑨)
	Details (metadata(URI 형식), IPFS 링크 (들어가면 이미지))  $\rightarrow$ onchain data
	![[Pasted image 20240509224750.png]]
	카테고리
	해시태그 붙여서 $\rightarrow$ 클릭 X, 검색 대상 X
	그냥 작품 설명 용도인 듯 (프론트)
	![[Pasted image 20240509225304.png]]
	Artist의 또 다른 작품 나열 
	more 누르면 Artist 페이지로
3. 메인페이지
	ARTIST가 업로드 한 건 Artwork 탭으로
	非ARTIST가 업로드 한 건 Inspiration 탭으로
	뉴스 2개 
	작품 분류 기준 - Newest, Popular, Oldest
	Inspiration 탭은 Newest 기준 밖에 없는 듯
4. 유저페이지 (非 아티스트)
	유저 프로필 이미지, 배너 이미지, 유저네임, 팔로워 팔로잉(클릭 가능), 게시글, 지갑주소(카피 버튼) (백엔드)
	유저 프로필 클릭 가능, 배너 이미지 클릭 가능 $\rightarrow$ 이미지 업로드 (본인)
	팔로우 버튼(본인 이외) 업그레이드 투 파트너 버튼(본인) 
	- Inspiration tab
		inspiration들 보여주기
		- inspiration 컨테이너 = 마우스 올리면 살짝 붕 뜨면서 
			- 이미지
			- Title, 
			- 공유, 
			- ==북마크, 박수== 상태 확인가능, 
			- 프로필이미지, 
			- 유저네임, 
			- 박수 수, 뷰 수 (read only)
		  ![[Pasted image 20240510002525.png]]
		 $\rightarrow$ 이 상태에서 프로필 영역에 마우스를 올리면 간소화된 프로필
		 ![[Pasted image 20240510002904.png]]
			 - 프로필 이미지, 유저 이름
			 - insp 수, 팔로워 수
			 - insp 항목 나열
			 - 팔로우 버튼
		 ![[Pasted image 20240510003113.png]]
			 - 본인일 땐, 팔로우 버튼 X
		 - artwork 컨테이너 = 
			 - 이미지
			 - artist 프로필 (owner)
			 - 공유, 
			 - ==북마크, 박수== 상태 확인가능, 
			 - 타이틀 (공간이 더 있음)
			 - artist 프로필 (+ @핸들)
			- 박수 수, 뷰 수 (read only)
		 ![[Pasted image 20240510002458.png]]
		  ![[Pasted image 20240510003421.png]]
			- 프로필 이미지, 아티스트 이름, 별
			- art 수, insp 수, 팔로워 수
			- 작품들 나열
			- 팔로우 버튼 + seeding 버튼
				$\rightarrow$ seeding 버튼 누르면 그대로 아티스트 프로필 페이지로 이동
	- Favorites tab $\rightarrow$ 북마크
		Artwork (갯수), Inspiration (갯수)
		- 있다면, inspiration 항목과 동일
		- 없다면, 
		  ![[Pasted image 20240509233949.png]]
		  creation 페이지 artwork tab으로 이동
		  - 본인이 아니면 
		    Owned tab 없음 나머진 동일
	- Owned tab
	  클릭시 The flux 유저페이지 owned 탭으로 이동
5. 런치패드 페이지
	- Staking tab
		- Total staked (ADF), ADF reward for the round, End Date(미국기준), ADF Price(coin market 사이트에서 정보 받아와야 하는 듯)
		- My staking status => 백엔드? 컨트랙트? 둘 다?
			![[Pasted image 20240510164110.png]]
			버튼 클릭시 $\rightarrow$ 마이 페이지 reward 탭으로 이동
		- 
	- Voting tab
		
	- My launchpad
	- how to use launchpad 버튼 $\rightarrow$ https://artiside.artdefinance.io/launchpad/about 로 이동


### 사용후기

### 출처(참고문헌)
-

### 연결문서
-