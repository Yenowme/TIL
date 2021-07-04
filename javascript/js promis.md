Promise는 자바스크립트 비동기 처리에 사용되는 객체이다.

콜백 지옥의 해결방법 중 하나.

1. promise객체를 선언하면 비동기 처리 로직이 실행되어 대기상태가 된다. 내부 함수로는 resolve와 reject함수가 인자로 들어온다.
2. `resolve`(전달데이터) 가 `promise` 콜백 함수에서 실행되면 그 함수는 `.then`으로 결과값이 넘어간다. 그 then메소드가 실행되면 인자값을 받아 진행된다.
   - [ ] resolve(데이터) 의 데이터가 then(내부함수(데이터))에 들어가는 데이터가 되는것일까?
3. `catch`가 `reject`를 진행시킨다.

`.then`을 체인방식으로 연결하여 결과값을 전달할 수 있다.

[자바스크립트 비동기 처리와 콜백 함수](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/)

[자바스크립트 Promise 쉽게 이해하기](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)
l
