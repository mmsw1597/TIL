### Git
파일을 트래킹하는 방식, version control system. 파일이 변경되었다면 무엇이, 언제, 누가, 어디서 바꾸었는지를 추적해준다.
이전 버전으로 돌아갈 수 도 있다.

### Github
git 파일이나 git 변경사항을 업로드하는 곳. 즉, 파일을 업로드 하는 곳.

### Github Desktop
git은 원래 콘솔에서 작동하나, 진입장벽이 높아서 좀 더 쉽게 사용할 수 있도록 만든 것이 github desktop. 
graphic user interface를 만든 것이다.

### Repository
파일들이 저장된 곳, 그리고 git이 주시하고 있는 곳이다. 

### Commit
커밋은 작업에 대한 기록이다. 어떤 변경사항이 있을 때, 그것을 히스토리에 기록하고 싶을 때 사용한다.

### Git workflow (Git Area)
1. Working Directory : 현재 작업하고 있는 폴더
2. Staging Area : 변경사항이 있는 파일들을 선택해 커밋할 수 있도록 지정하는 곳.
3. Git Directory : 파일들이 커밋된 곳. 변경사항에 대한 스냅샷을 갖고 있는 곳.

### Branch
마스터의 마지막 commit에서부터 다른 타임라인을 뜻함. 변경사항을 마스터로 전달하여 merge할 수 있음.

### Conflict
예를 들어 main 브랜치와 다른 하나의 브랜치 A가 있다고 하자. main과 A에서 서로 같은 라인을 수정하고, main에서 이를 merge하려고 할때
충돌이 일어난다. 이때, merge하기 전 경고를 주고, 그럼에도 merge를 누르면 다음과 같이 코드가 변경된다.
```txt
<<<<<<< HEAD
crazy conflict
=======
welcome friends
>>>>>>> happy

and then he lives.
```
<<< ~ === 는 main branch의 상태이고, === ~ >>>는 happy branch의 수정 상태이다. 여기서 수정하고 싶은 부분만 남기고 나머지는 모두 지우면
conflict가 사라지고 정상적으로 merge가 가능하다.

### fork
다른 사람의 repository를 복사하여 자신의 repository에 저장하는 것.

### clone a repository
Github에 있는 repository를 자신의 desktop으로 복사하는 것.

### push
작업 완료후 push를 통해 코드를 원격 저장소로 보내는 것.

### pull request
원본 레포지토리에서 pull request를 생성하면 다른 사람들이 원본을 수정한 코드를 올릴 수 있다. 원본의 주인은 merge여부를 결정할 수 있다.

### fork한 후에 원본이 변경되면?
1. fork하면 기본적으로 upstream 브랜치가 생성됨.
2. upstream 브랜치를 통해 베이스 저장소의 변경사항을 요청받을 수 있음.
3. fork한 후 fetch를 하게되면 upstream 브랜치가 변경됨.
4. upstream 브랜치를 자신의 master 브랜치로 병합하면 최신 상태로 업데이트 됨.

### issues
해야할 일들이나 사람들이 발견한 문제나 버그를 기록하는 곳. 작성자나 원본의 주인이라면 그 이슈를 닫을 수 있다.

### milestone
다음 버전으로 가기 위해 해결해야 하는 이슈를 모은 것.
