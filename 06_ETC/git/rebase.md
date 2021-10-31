#rebase 명령어

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c70e8662-f922-4342-adcf-12e648ff8cce/_2021-07-06__12.33.11.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/c70e8662-f922-4342-adcf-12e648ff8cce/_2021-07-06__12.33.11.png)

뒤엉킨 커밋과 머지의 난장판

내가 하는 feature를 진행하는 중, 다른 팀원들이 featrue를 끝내고 develop브런치를 업데이트 시킨적이 있다. 나도 해당 수정사항에 대한 반영이 필요해서, develop브랜치를 내 브랜치에 머지시키고 작업을 계속 진행했는데, 깃 그래프가 보기 싫게 되어서 멘토님이 rebase기능을 알아보라며 추천해주셨다.

### 병합기능

merge와는 다르게, 빠져나와있는 코드의 분기점(base)을 새로 업데이트(rebase)해줄 수 있다.

1. `git checkout feature`

   기존 브랜치 `feature` 로 체크아웃

   출발지를 업데이트 할 대상 브랜치로 체크아웃 한다.

2. `git rebase main`

   `main` or `develop`브랜치와 `rebase`

- 루트1

  1. 충돌 처리
  2. `git add .`

     `git rebase —continue`

     add 하고 rebase continue

- 루트2

  1. `git checkout main`
  2. `git merge feature`

     fast-foward 머지

### 사용 이유

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f34724f0-ff7d-4cb5-9f2f-27c2e2d735b4/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/f34724f0-ff7d-4cb5-9f2f-27c2e2d735b4/Untitled.png)

리베이스 전

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/91f7d891-61d1-4e3a-b3d0-786ebbeca955/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/91f7d891-61d1-4e3a-b3d0-786ebbeca955/Untitled.png)

리베이스 후

- 분기점을 업데이트 해주어 코드의 흐름을 잘 정리해줄 수 있다, 머지만 할 경우 그런것 없이 난장판이 된다.
- 여럿이서 작업시, 시간상 흐름을 확실히 진행하여 코드의 조상?을 확실히 할 수 있다.

### 참고

[https://velog.io/@godori/Git-Rebase](https://velog.io/@godori/Git-Rebase)

[https://readystory.tistory.com/151](https://readystory.tistory.com/151)
