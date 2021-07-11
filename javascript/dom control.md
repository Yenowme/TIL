#DOM 다루기

[0. 노드 선택](##노드-선택)
[1. location](##1.location)
[2.event](##2.event)

##0.노드 선택

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

## 1. location

`window`와 `Document`가 가지고 있는 객체. 객체가 연결된 장소(url)을 포함한다.

- **herf**

  현재 경로를 표시한다. 값을 새로 할당하여 다른 링크로 이동이 가능하다.

  `location.herf="/go"`

- **reload()**

  현재 url의 리소스를 다시 불러온다. 즉 새로고침 기능을 제공

  `location.reload()`

---

## 2. event

### 이벤트를 다루는 방법

- 사용자가 버튼을 클릭하거나, 폼필드에 값을 넣는 등의 행동을 했을 때, 이 모든 행동을 javascript의 event객체는 관찰하고 있다.
  우리는 이걸 이용해서 웹사이트를 동적으로 구성할 수 있다.

---

### 이벤트 리스너

1. `on` 사용

   ```javascript
   window.onload = function (e) {
     alert("I'm loaded");
   };
   ```

   위와같이 .on으로 시작하는 메소드를 사용해서 dom에 이벤트리스너를 콜백방식으로 구현할 수 있다.
   자주 쓰이는 이벤트 목록은 아래와 같다

   <details>
   <summary>이벤트 리스너</summary>
   <div markdown="1">

   - onblur : 객체가 foucs를 잃었을 때

   - onchange : 객체의 내용이 바뀌고 focus를 잃었을 때

   - onclick : 객체를 클릭했을 때

   - ondblclick : 더블클릭할 때

   - onerror : 에러가 발생했을 때

   - onfocus : 객체에 focus가 되었을 때

   - onkeydown : 키를 눌렀을 때

   - onkeypress : 키를 누르고 있을 때

   - onkeyup : 키를 눌렀다 뗐을 때

   - onload : 문서나 객체가 로딩되었을 때

   - onmouseover : 마우스가 객체 위에 올라왔을 때

   - onmouseout : 마우스가 객체 바깥으로 나갔을 때

   - onreset : Reset 버튼을 눌렀을 때

   - onresize : 객체의 크기가 바뀌었을 때

   - onscroll : 스크롤바를 조작할 때

   - onsubmit : 폼이 전송될 때

   </div>
   </details>

2. `addDventListener` 사용

- 여러 이벤트들을 콜백으로 등록하기 쉽다.

- 이벤트를 제거할 수도 있다 = `removeEventListener`

```javascript
function onClick() {
  alert("I'm clicked!");
}
function onClick2() {
  alert("또다른 이벤트");
}
document.getElementById("clickMe").addEventListener("click", onClick); // 이벤트 연결
document.getElementById("clickMe").addEventListener("click", onClick2); // 또 하나의 이벤트 연결
document.getElementById("clickMe").removeEventListener("click", onClick); // 연결할 이벤트 중 하나 제거
```

### event객체

1. `.target`

- event가 동작중인 타겟, 즉 해당 dom의 정보를 가지고 있다.
- 활용도 높다.
