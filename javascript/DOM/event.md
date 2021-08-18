# 2. event

### 이벤트를 다루는 방법

- 사용자가 버튼을 클릭하거나, 폼필드에 값을 넣는 등의 행동을 했을 때, 이 모든 행동을 javascript의 event객체는 관찰하고 있다.
  우리는 이걸 이용해서 웹사이트를 동적으로 구성할 수 있다.

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

   - onkeypress : 키를 누르고 있을 때 -> 권장하지 않음

   - onkeyup : 키를 눌렀다 뗐을 때

   - onload : 문서나 객체가 로딩되었을 음

   - onmouseover : 마우스가 객체 위에 올라왔을 때

   - onmouseout : 마우스가 객체 바깥으로 나갔을 때

   - onreset : Reset 버튼을 눌렀을 때

   - onresize : 객체의 크기가 바뀌었을 때

   - onscroll : 스크롤바를 조작할 때

   - onsubmit : 폼이 전송될 때

   </div>
   </details>

2. `addDventListener` 사용

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
	- 여러 이벤트들을 콜백으로 등록하기 쉽다.

	- 이벤트를 제거할 수도 있다 : `removeEventListener`

### event 버블링

- 이벤트가 연속하여 발생하는 버블현상. 여러개의 요소가 겹쳐있을 때, event는 해당 위치에서 위로 가면서 이벤트를 발생시킨다.
- `event.stopPropagation()`을 통해 버블링을 멈출 수 있다.

### event객체

1. `.target`

- event가 동작중인 타겟, 즉 해당 dom의 정보를 가지고 있다.
- 활용도 높다.
