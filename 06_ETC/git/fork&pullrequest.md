## 깃 포크 해오는 방법
1. fork
    - 포크할 깃헙 레포에서 우측 상단 fork를 누른다.

    → 내 계정 repo에 fork된 저장소가 생성됨

2. clone, remote
    - fork된 레포를 내 로컬에 클론한다
    - 원본 프로젝트 저장소를 추가한다.

        ```bash
        git remote add origin_repo(별명) https://github.com/원본레포
        ```

    - 수정작업 후 로컬에 push한다 (브랜치를 생성해도 됨)
3. 로컬 깃허브에 들어가면 compare & pull request 버튼이 뜬다
4. 풀리퀘를 생성하고, 머지해준다.

## 포크한 깃을 최신상태로 유지하는 방법

1. remote 원본 주소 추가
    ```shell
        git remote add upstrem 원본깃헙주소
    ```
2. git fetch를 통해 내용 불러오기
    ```shell
        git fetch upstream
    ```
3. 병합
    ```shell
        git checkout main
        git merge upstream/main
    ```
4. 내 레포에 푸쉬
    ```
        git push origin master
    ```
 - 왜 fetch 후에 merge하는진 모르겠다.
### 출처

[https://wayhome25.github.io/git/2017/07/08/git-first-pull-request-story/](https://wayhome25.github.io/git/2017/07/08/git-first-pull-request-story/)
