### git 기본적인 사용법

##### Clone
```
git clone [저장소 링크]
```
특정 브랜치만 클론하고 싶을 때
```
git clone -b [브랜치 이름] [저장소 링크]
```
##### Pull
git pull [저장소 링크]






### 2024년 04월 18일 15시 06분 14초
obsidian에서 git push 오류가 났었다.
이후 계속해서 커밋은 이루어졌지만 push는 되지 않았다.
![[Pasted image 20240418183204.png]]
이런 오류를 띄우며 push가 되지 않았다.

#### 원인:
원인은 git plugin에서 모든 정보를 commit하고 push를 하는가보다.

Excalidraw에서 ai를 사용하려고 내 open ai api key를 받아와서 넣었다.
근데 그것도 커밋을 하고 푸시를 해서 
secret 내용은 푸시를 할 수 없다고 경고가 떴다.

### 해결:
그래서 다시 excalidraw 설정에서 api key를 지우고 
==`git log`== 를 이용해 commit 기록과 commit id를 확인한 다음에
==`git reset --hard [commit id]`== 를 통해 commit을 롤백 시켰더니 
그 후로 문제 없이 해결됐다.

