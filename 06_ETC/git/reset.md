# git reset

`git reset -—hard HEAD`

## reset 옵션

-   soft : index 보존(add한 상태, staged 상태), 워킹 디렉터리의 파일 보존. 즉 모두 보존.
    → 커밋에 뭐 추가해야하거나 할때 사용
-   mixed : index 취소(add하기 전 상태, unstaged 상태), 워킹 디렉터리의 파일 보존 (기본 옵션)
    → add한것도 취소
-   hard : index 취소(add하기 전 상태, unstaged 상태), 워킹 디렉터리의 파일 삭제. 즉 모두 취소.
    → 최신 커밋 상태로 돌아감

## 커밋된 메세지 변경

`git commit —amend -m "COMMIT MESSAGE"`

### 참고

-   [참고 블로그](https://gmlwjd9405.github.io/2018/05/25/git-add-cancle.html)
