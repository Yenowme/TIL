### 정의

JavaScript Object Notation. 즉 javascript 객체 문법으로 구조화된 데이터(객체)를 표현하기 위한 표준 포맷이다. 서버와 클라이언트가 데이터를 주고받을때 일반적으로 사용한다.

객체와 문자열 형태를 왔다갔다 할 수 있기 때문에 네트워크를 통해 주고받기 수월하다.

객체와의 큰 차이는 메서드를 담을 수 없다는 점이다. 키와 벨류값 모두 큰 따옴표를 사용해야 한다.

### 명령어

- `JSON.stringify()`
  - 인수로 전달받은 객체를 문자열로 변환하여 반환
  - js → ejs로 가져갈때 사용함
  - `parse`랑 상호보완적관계
- `JSON.parse()`
  - 인수로 받은 문자열을 객체로 변환
  - `stringify()`와 상호보완적

### 주의사항

객체 내부의 데이터에 `\n`나 `\t`와 같은 **이스케이프 문자**가 들어가면parse에 오류가 나는 경우가 있다..

그럴땐 데이터에 `.replace(/\n/gi, '\\n');`와 같이 정규표현식을 사용해서 치환해줘야한다.

---

JSON참고: [https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/JSON](https://developer.mozilla.org/ko/docs/Learn/JavaScript/Objects/JSON)

[https://0taeng.tistory.com/37](https://0taeng.tistory.com/37)
