### stdin 입력값 받는법 = (`scanf`)

```jsx
const readline = require("readline");

const rl = readline.createInterface({
  input: process.stdin,
  output: process.stdout,
});

rl.on("line", (line) => {
  console.log("hello !", line);
  rl.close();
});

rl.on("close", () => {
  process.exit();
});
```

1. `readline모듈` 불러오기

   : 한 줄씩 readable스트림 (ex: process.stdin) 에서 데이터를 읽기위한 인터페이스 제공

2. `rl.createInterface`로 input, output값 설정해주기

   : readline을 사용하기 위해 인터페이스 세팅

3. `rl.on`으로 `line`이벤트 핸들러 걸기
   - `rl.question`으로도 사용 가능
4. 이벤트 핸들러를 끝낼땐 `rl.close()` 이벤트 진행해야한다.

   그렇지 않으면 이벤트가 끝나지 않음

5. `close` 이벤트 핸들러로 데이터 받은 결과 진행하기

---

### 여러 줄 입력방법

```javascript
const rl = require("readline").createInterface({ input: process.stdin });

let arr = [];
let i = 0;

rl.on("line", (line) => {
  //이벤트리스너여서 계속 반복된다.
  console.log(i);
  i++;
  if (i === 3) {
    rl.close();
  }
}).on("close", () => {
  console.log(arr);
  process.exit;
});
```

- `rl`에 `"line"`이라는 이벤트 리스너를 걸어서 진행하는것이기 때문에 여러줄을 입력받더라도 따로 반복문을 설정 할 필요없이, 리스너 안에 close조건을 걸어주면 된다.

### 그 외 메소드

- .`question`
  - `rl.question('', (answer) ⇒ {})`

### 참고

[https://velog.io/@yujo/node.js표준-입력-받기](https://velog.io/@yujo/node.js%ED%91%9C%EC%A4%80-%EC%9E%85%EB%A0%A5-%EB%B0%9B%EA%B8%B0)
