# tmux

## 개요

-   여러 터미널 세션을 활용할 수 있는 프로그램
-   터미널을 종료시켜도 이어서 작업할 수 있다.
-   프로그램을 백그라운드에서 계속 돌릴수도 있음.

<br/>

---

## 키워드

1. session
    - tmux를 실행하는 작업 단위. 여러 윈도우로 구성됨.
2. window
    - 터미널 화면으로 세션 내에서 탭처럼 사용 가능.
3. pane
    - 하나의 윈도우 내에서 화면 분할 가능.

## 사용법

### 세션

1. 세션 생성
    - `tmux new -s SESSION_NAME`
2. 세션과 함께 윈도우 생성
    - `tmux new -s SESSION_NAME -n WINDOW_NAME`
3. 세션 종료
    - `exit`
4. 세션 목록
    - `tmux ls`
5. 세션 이어하기
    - `tmux a`
    - `tmux attach -t SESSION_NUMBER (or SESSION_NAME)`
6. 세션 중단하기 (이어하기 가능 )
    - `tmux d`

### window

-   기본으로 `control + d`로 커맨드 입력을 시작함 -> `pre`로 지칭함

1. 새 창 열기
    - `pre + c`
2. 윈도우 목록 확인/
    - `pre + w`
3. 윈도우 이동
    - 다음: `pre + n`
    - 이전: `pre + p`
    - 지정 이동: `pre + 숫자`

### pane

1. 가로 화면 추가
    - `pre %`
2. 세로 화면 추가
    - `pre "`
3. 화면 포커스 이동
    - `pre o`
    - `pre art 화살표`

## 참고

-   참고 블로그 : https://seulcode.tistory.com/144
