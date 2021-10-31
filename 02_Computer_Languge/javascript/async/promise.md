# promise

Promise는 자바스크립트 비동기 처리에 사용되는 객체이다.

콜백 지옥의 해결방법 중 하나.

### 사용방법

1. promise객체를 선언하면 비동기 처리 로직이 실행되어 대기상태가 된다. 내부 함수로는 resolve와 reject함수가 인자로 들어온다.

    ```jsx
    promise = new Promise(function(resolve, reject){
    	resolve(1);
    	reject(2);
    })

    promise.then(function(data){
    	console.log(data); //1
    })

    promise.catch(function(error){
    	console.error(error)
    })
    ```

2. `resolve`(전달데이터) 가 `promise` 콜백 함수에서 실행되면 그 함수는 .`then`으로 결과값이 넘어간다. 그 `then`메소드가 실행되면 인자값을 받아 진행된다.
3. `catch`가 `reject`를 진행시킨다.
4. `.then`을 체인방식으로 연결하여 결과값을 전달할 수 있다.

### 프로미스의 3가지 상태

1. pending(대기)

    : 비동기 처리 로직이 아직 완료되지 않은 상태

    ```jsx
    new Promise((resolve, reject) => {
    	//...
    });
    ```

2. fulfilled(이행)

    : 비동기 처리가 완료되어 프로미스가 결과값을 resolve에 반환한 상태

    ```jsx
    promise = new Promise((resolve, reject) => {
    	resolve(data); //fulfilled
    });

    promise.then(fun);
    ```

    - 이제 `then()` 을 사용할 수 있다.
    - `then`의 리턴값은 다시 `then`콜백함수의 매개변수로 들어간다.
3. rejected(실패)

    : 비동기 처리가 실패하거나 오류가 발생해서 reject()가 호출된 상태

    ```jsx
    new Promise((resolve, reject) => {
    	reject(error); //fulfilled
    });

    promise.catch(fun);
    ```

    - then의 두번째 인자로 error를 처리할 수도 있다. 하지만 가급적 catch를 사용할것.

### Promise.all
-  배열로 매개변수를 주면, 모두 실행이 끝나고 나서 결과값을 배열로 리턴한다.

    ```js
    const a1 = Promise.resolve(1);
    const a2 = Promise.resolve(2);
    const a3 = Promise.resolve(3);

    Promise.all([a1, a2, a3]).then((pass)=>{
        console.log(pass); //[1,2,3]
    })
    ```

---

## 출처

[자바스크립트 비동기 처리와 콜백 함수](https://joshua1988.github.io/web-development/javascript/javascript-asynchronous-operation/)

[자바스크립트 Promise 쉽게 이해하기](https://joshua1988.github.io/web-development/javascript/promise-for-beginners/)

- ajax
- async & await

---
