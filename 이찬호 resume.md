**Chanho Lee**

**Contact Information**  
Email: dirtyface1234@naver.com  
Phone: +82 10-3029-3696
Github: https://github.com/chan3785
Twitter: https://x.com/chan3785

---
## **Projects**
##### SuperTell 
**역할:** Front-End Developer  
**개요:** A prediction market platform built on the NEO blockchain.  
**기술 스택:** Next.js, TypeScript, Solidity, Telegram Bot API  

**수행한 업무:**
1. 로그인: wagmi를 사용해 지갑 로그인 구현. context api와 provider로 로그인 상태를 전역적으로 관리, 브라우저 local storage에 토큰 저장으로 로그인 유지
2. 게임 생성/조회/삭제: writeContract(), readContract를 통해 게임을 생성하고 게임 리스트, 게임 상세 조회 
3. 반응형 웹 디자인: React context API를 사용해 사용자 기기의 스크린 크기를 전역 상태로 상태값에 따른 반응형 웹 디자인 구현.
4. 텔레그램 웹 앱 배포: telegram bot api로 telegram bot 생성 -> TWA 배포

**결과:**
1. 영어 커뮤니케이션 협업 능력 향상
2. 전역 상태관리 경험
3. 해외 개발자 협업 경험

**개선점:**
1. 모바일 UI가 개선이 되었으면 좋겠음.
2. 단순한 가격 예측 모델이 아닌 dapp과 관련된 (ex. 활성 사용자 수, TVL 등)에 대한 정보를 불러오는 api를 활용하면 더 재밌었을 것 같음.
3. 커스텀 훅으로 반복되는 코드 개선
**링크:** [Website](https://supertell.vercel.app) | [GitHub](https://github.com/chan3785/supertell.git)

---
##### Ripple market 
**역할:** Front-End Developer  
**개요:** web3 second hand market
**기술 스택:** Next.js, TypeScript, web3Auth

**수행한 업무:**
1. 로그인/회원가입: web3Auth SDK를 사용. 소셜 로그인 google auth를 통해 지갑 로그인 구현. getAccount()로 로그인 상태 예외처리 로직 강화.
2. 게시글 생성/조회/수정/삭제: pocket base를 통해 CRUD 로직 연결

- 결과
1. XRPL 2024 해커톤 3rd Place 수상 ($2000)
2. web3Auth, 소셜 로그인 사용

- 후기
non-evm 체인에 연결할 때는 web3auth 모듈을 사용할 수 있는 것을 배웠습니다.
문서를 찾아보니 리플 뿐만 아니라 solana 등 다른 레이어 1 체인에도 연결할 수 있고 소셜 로그인 기능을 제공하므로 사용자 경험이 좋을 것 같습니다.

**링크:** [Website](https://ripplemarket-chan3785s-projects.vercel.app/) | [GitHub](https://github.com/hackathemy/ripplemarket)
