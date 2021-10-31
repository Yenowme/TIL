# DOM 다루기

- [0. 노드 선택](#0-노드-선택)
- [1. location](#1-location)
- [2. event](#2-event)
<br>

# 0. 노드 선택

### 알아둘 것

- DOM은 트리구조로 이루어져 있고. 모든 연산은 document객체에서 시작한다.
- node > element

  node는 html엘리먼트가 아닌 많은 것들을 포함하기때문에 html엘리먼트를 선택할때는 element를 선택할 것

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6f21b87a-bc0d-4ae8-9a8e-74ddbd84b7a6/_2021-07-07__3.14.51.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/6f21b87a-bc0d-4ae8-9a8e-74ddbd84b7a6/_2021-07-07__3.14.51.png)

자바스크립트 명령어를 통해 노드를 선택해서 조정할 수 있다. <br>
내가 자주 사용한건 아래 명령어들

- `querySelector`
- `querySelectorAll`
  - 배열
- `getElementsByclassName`
- `getElementById`
- `.childNodes`
  - 배열 형식으로 되어있다.
    - 접근방법
- `previousSibling` & `nextSibling`
  - 형제 노드를 찾을때 사용
  - previous : 앞
  - next: 뒤
---
### querySelector & getElementBy 차이

- querySelecor

    → NodeList 반환

    - 인덱스로 노드에 접근 가능
- getElementBY

    → HTMLcollection 반환

    - 인덱스나 키로 노드에 접근 가능

### 참고

[https://ko.javascript.info/dom-navigation](https://ko.javascript.info/dom-navigation)

# 1. location

`window`와 `Document`가 가지고 있는 객체. 객체가 연결된 장소(url)을 포함한다.

- **herf**

  현재 경로를 표시한다. 값을 새로 할당하여 다른 링크로 이동이 가능하다.

  `location.herf="/go"`

- **reload()**

  현재 url의 리소스를 다시 불러온다. 즉 새로고침 기능을 제공

  `location.reload()`


