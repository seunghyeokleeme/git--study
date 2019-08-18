# git--study

## 1. git이란?

- git은 파일의 변경사항을 추적하는 시스템

누가,언제, 뭐를 작성한지

이것을 local pc에 저장하고 클라우드에 push도 할수 있다.
서버에 올려서 변경사항을 백업할수 있다.---깃 허브

- versinon Control

1. repository ---folder
2. Commit----- change write(깃이 추적하여 변경사항의 보관함)
3. Branches------- defalut :master ---last work(user using..) /// new item add?? no master?? ---- new branch use!!!

- link: https://help.github.com/en/articles/github-glossary
  // GitHub glossary(용어집)--- 중요중요

##목적

이 수업은 아래와 같은 상황에 있는 분들을 위한 수업입니다. 아래에서 문서란 일반적인 텍스트 문서에서부터 이미지, 소스코드를 망라한 모든 파일이라고 생각하시면 됩니다.

수 많은 문서를 관리해야 하는 분
이 문서들이 자주 변경되는 분
문서의 변경 이력을 체계적으로 관리해야 하는 분
문서의 조작을 막아야 하는 분
문서를 안전하게 백업해야 하는 분
문서를 다른 사람과 공유해서 공동으로 작업하는 분

//local respository remote repository
push: 원격 저장소에 밀어놓는 것 (인터넷으로 밀어놓은 것)

---

1. Version Control
2. backup
3. Collaborate

<h1> backup </h1>

- my1 (push) -------> github.com (서비스)
- my2 <-------------(pull)
  -------------------------- =same
- my2 ------------>(push)
- my1<------------pull

<h1>Collaborate</h1>

- my ---------> push
- other <---------- pull
  ---------> push

### 1.Git Bash 실행

==> 콘솔/터미널에 ‘git’ enter!!

- pwd : print working directory
- cd / :root directory
- cd ~ :home directory
- cd :change directory
- --help : simple manual
- man command : manual
- ls –l : list in log format
- touch: make empty file
- .filename :hidden files
- ls –a : show all files
- mkdir : make directory
- ./ :current directory
- mv : move(rename)
- rm –r : remove directory
- ../ : parent directory
- cd /: absolute directory vs cd ../ : relative directory
- 자동화는 명령&&명령&&명령

### 2.버전관리의 시작

- 어떤 특정한 디렉터리를 버전 관리 하고 싶으니까 거기를 관리해 라고 시킬거다.

- => pwd 입력
- ---홈디렉토리가 나온다
- => cd Desktop/git/ 입력
- ---이건 디렉토리 미리 만듬
- => pwd 입력
- ---지금 디렉토리 주소나옴
- => ls –al 입력
- ---상태확인
  ........
  https://youtu.be/avP7QLMNSXo

- .
- ..
- ------------> git init . 입력해야한다.
- .git

### 3.버전 생성

Working tree (수정된파일) -> Staging Area (버전을 만드는곳) -> Repository(깃=버전을 보관함)

- .
- ..
- .git
- -----> nano hello1.txt 입력 (문서 생성)
- --------> 1 입력 (내용) 나가는건 ctrl + X
- <!> cat 파일명.확장자 입력하면 파일 내용이 출력

git status 입력 -----> 유저한테 상태를 보여줌 ..아직 버전이 없고
추적안하는 파일명을 보여줌

git add 파일 입력 --> 버전이 될 상태 만듬

깃에게 버전 만들어!!
---->(명령어)
git commit –m “Message 1” 입력 ----> 버전이 생성됨(저장소로 감)

/// working tree clean -----> 버전이 되지 않은 수정사항이 없다 의미..

git log -----> 버전 확인하고 싶을 때 history 보고싶을때

### 4.여러개의 파일을 하나의 버전으로 만들기

changes not stagged... untracked files; 차이

1. 깃은 버전 관리를 한번 했기 때문에 관리되고 있고
2. 버전관리를 안해봤기 때문에 깃이 추적을 없는셈 친다.

제일 중요중요!!!!!
https://handam.tistory.com/127

### 5. 버전간의 차이점비교

git log –p ---------> 버전이름 알수 있고 추가정보랑 이전 버전확인상태 알수 있음

git diff -------------> Working tree에서 수정된사항 기록 보여준다.

### 6. checkout과 시간여행

git checkout (commit의 아이디)
ex) git checkout 8f7def17efe83ed11048959a759c59bfb5faf359

git checkout master ---------> 가장 최신 버전으로 돌아옴

### 7. 보충 수업

git add . --------> 모든 디렉토리안에 있는 파일을 다 버전을 될준비를 한다.

git add src ----------> 모든 src 디렉토리를 ~ 한다

git commit –am “내용” -------> add와 commit을 동시에한다.

but!! 한번이라도 add가 된 파일이어야 작동함...

### 8. 버전 삭제 git reset

3번째 commit한 버전을 지우고 2번이 최신버전이 되어야하면

git reset —hard 2번id 입력!! ---------> 이버전으로 reset하겠다 의미!!!!!!

!!!!!!!! 공유되기 전 버전만 reset 만 하는게 좋다 오류가 날수도 있기때문.......

### 9. 버전 되돌리기 - git revert

버전을 삭제하지 않으면서, 되돌리는 방법으로서 revert를 소개합니다

이때는 commit it를 최신버전으로 쓴다. 즉 삭제하지않지만 사라지는 id를 ..

무조건 역순으로 revert 해야한다.

1234
ex) 3번이 커밋 -------- 4번 revert
1번이 커밋------------- 4번 revert 3 revert 2번 revert 진행!!!
