### 기본
1. HEAD -> master 는 컴퓨터에 커밋된 것.
2. origin/master 는 github 저장소에 올라간 커밋.

### push
git push origin main (not master)

### pull
git pull origin main

### stage에 추가
git add file명

### 커밋
git commit -m "message"

### 과거로 돌아가기
git log 입력. HEAD가 있는 위치가 현재 내 파일의 시점. commit 마다 고유 id를 가지고 이 id를 복사후 git checkout id 입력하면 과거로 돌아갈 수 있음.

### 현재로 돌아오기
git checkout main 입력. 이는 main 브랜치로 돌아오는 뜻이기도 함.

### 커밋 삭제
HEAD에서 지금 버전을 삭제하고 싶으면 git reset --hard HEAD^ 를 입력. HEAD뒤에 오는 ^는 현재 버전에서 얼마나 멀리 갈지를 나타냄. 이는 하드리셋이며 파일을 삭제하고 완전히
과거로 돌아감.

### 원격저장소 github와 일치시키기.
git push origin main --force 입력. 코드 충돌 무시.

### mixed reset
git reset HEAD^ 는 복합 리셋이라함. 이는 내가 선택한 커밋에서 변경사항을 unstage 영역 즉, 작업 영역으로 옮김. 커밋은 돌아가지만 변경된 파일은 그대로임.

### soft reset
복합 리셋과 유사하지만 unstage가 아닌 stage 영역에 추가한다.

### 브랜치 생성
git checkout -b new-branch-name

### 브랜치를 깃허브에 올리기
git push origin branch-name

### git status
파일 상태 확인 명령어

### 가장 최근의 커밋 수정
git commit --amend -m "message" / git commit --amend --no-edit (전자는 메시지를 수정. 후자는 메시지 수정 X)

