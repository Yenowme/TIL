- 정해진 건 아니지만 커밋 컨벤션을 통일해두면 가독성이 올라가고, 커밋의 목적을 알기 쉽다.
- 통용되는 컨벤션 참조를 위해 [유다시티의 커밋 메세지 스타일](https://udacity.github.io/git-styleguide/) 가이드를 참조했다.

### 1. Commit Message Structure

---

```jsx
type: subject;

body;

footer;
```

기본적으로 위와 같이 구성한다.

### 2. Commit Type

---

- feat: new feature 추가
- fix: 버그 fix
- docs: 리드미와 같은 기타 문서 수정
- style: 코드 컨벤션 수정, 스페이스, 엔터 수정
- refactor: 코드 refactoring
- test: 테스트코드, 리펙토링 테스트코드 추가
- chore: 빌드 업무 수정, 패키지 매니저 수정

### 3. Subject

---

- 제목은 50자를 넘기지 않고 마침표도 붙이지 않는다.
- 과거시제를 사용하지 않고 명령어를 사용한다.

### 4. Body

---

- 선택사항이기 때문에 모든 커밋에 본문내용을 작성할 필요는 없다.
- 부연설명이나 커밋의 이유 설명시 작성한다.
- 72자를 넘기지 않고 제목과 구분되기 위해 한칸을 띄운다.

### 5. footer

---

- 선택사항이기 때문에 모든 커밋에 꼬리말을 작성할 필요는 없다.
- issue tracker id를 작성한다.
