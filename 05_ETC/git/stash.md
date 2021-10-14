# git stash

-   작업사항들을 스택에 임시로 저장할 수 있음
-   커밋하기 전 브랜치를 이동할 때, 머지할 때 사용

<br/>

-   stash 대상
    -   Modified이면서 Tracked 상태인 파일
    -   Staging Area에 있는 파일(Staged 상태의 파일)
        -   git add 명령을 실행한 경우

## 명령어

-   `git stash` : 대상들을 스택에 저장
-   `git stash list`: 저장된 목록을 보여준다.
-   `git stash drop stash@{2}`: 특정 stash를 삭제할 수 있다(list로 확인 가능)
