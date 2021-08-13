### 역사

---

Representational State Transfer 용어의 약자. HTTP 설계를 제대로 활용하도록 설계한 아키텍처.

- 기술이나 내용이 아닌 형식이다.
- 메소드와 url을 조합해 직관적인 데이터 요청을 보내는 방법.

### 구성

---

- 자원(RESOURCE) - URL
- 행위(Verb) - HTTP METHOD
- 표현(Representations)

### 특징

---

1. Uniform Interface

    url로 지정한 리소스에 대한 조작을 통일되고 한정적인 인터페이스로 수행하는 아키텍처 스타일 (뭔말?)

2. Stateless

    작업을 위한 어떠한 상태정보를 따로 저장하고 관리하지 않는다. 그저 들어오는 요청만을 처리하면 된다.

3. Cacheable

    HTTP웹표준을 그대로 사용하기 때문에, 웹에서 사용하는 기존 인프라를 그대로 활용이 가능하다.

4. Self-descriptiveness

    REST-API 메세지만 보고도 이를 쉽게 이해 할 수 있는 자체 표현 구조로 되어있다.

5. Client - Server 구조

    서버는 API를 제공하고, 클라이언트는 사용자 인증이나 컨텍스트등을 직접 관리하는 구조로 각각의 역할이 확실히 구분된다 .

6. 계층형 구조

    다중 계층으로 구성될 수 있으며, 보안, 로드 밸런싱, 암호화 계층을 추가해 구조상의 유연성을 둘 수 있고, PROXY, 게이트웨이 같은 네트워크 기반의 중간매체를 사용할 수 있다.

---

### HTTP

- GET

    데이터를 조회, 요청하는데 사용

- POST

    새로운 정보를 추가하는데 사용

- PUT

    데이터를 변경, 업데이트 (통째로 갈아끼울때)

    - PATCH

        일부 데이터를 수정

- DELETE
    - 데이터를 삭제할 때

---

### 규칙

→ 대안으로 GraphQL이 있다.

- 데이터를 컬럼단위로 요청할 수 있다

---

[https://www.youtube.com/watch?v=iOueE9AXDQQ](https://www.youtube.com/watch?v=iOueE9AXDQQ)
