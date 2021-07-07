#DOM 다루기

###노드 선택

### 알아둘 것

- DOM은 트리구조로 이루어져 있고. 모든 연산은 document객체에서 시작한다.
- node > element

  node는 html엘리먼트가 아닌 많은 것들을 포함하기때문에 html엘리먼트를 선택할때는 element를 선택할 것

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6f21b87a-bc0d-4ae8-9a8e-74ddbd84b7a6/_2021-07-07__3.14.51.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6f21b87a-bc0d-4ae8-9a8e-74ddbd84b7a6/_2021-07-07__3.14.51.png)

자바스크립트 명령어를 통해 노드를 선택해서 조정할 수 있다
내가 자주 사용한건 아래 명령어들

- `querySelector`
- `querySelectorAll`
  - 배열
- `getElementsByclassName`
- `getElementById`
- `.childNodes`
  - 배열
    - 접근방법
- `previousSibling` & `nextSibling`
  - 형제 노드를 찾을때 사용
  - previous : 앞
  - next: 뒤

### 참고

[https://ko.javascript.info/dom-navigation](https://ko.javascript.info/dom-navigation)
