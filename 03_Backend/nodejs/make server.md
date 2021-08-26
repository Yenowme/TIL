## HTTP 모듈 사용

### 사용 방법
1. 서버 생성
	```jsx
	const http = require("http");

	http.createServer(function (req, res) {
		res.writeHead(200, { "Content-type": "text/plain" });
		res.write("hello, worlds");
		res.end();
	}).listen(4242);
	```

	- 가장 간단한 형태의 http서버
	- 사용을 위해 `node` 내장 모듈인 `http`를 `require`을 통해 불러와야한다.
	- `http`모듈의 `createServer()`함수를 사용해서 서버 인스턴스를 생성하고, 서버 인스턴스의 `listen()`함수는 `http`서버를 시작하게 한다.
	- createServer의 콜백 함수로 응답에 대한 처리가 이루어진다.<br>
<br>
<br>
2. request 값 받기
	```js
	 req.on("data", (chunk) => {
            reqData += chunk;
        });
        req.on("end", () => {
            if (reqData === undefined) throw "body에 값이 없습니다.";
            reqData = reqData.toString();
            console.log(reqData)
        });
	```
	- 값을 받아올 때도 리스너를 걸어줘야 한다.
	- 'data' 이벤트가 값을 계속 받아오고
	- 'end' 이벤트가 마지막 값을 받아 처리한다.
	- 버퍼로 값이 들어오기 때문에 `toString()`으로 변환이 필요하다.
<br>
<br>
### 동작 원리

- 기본적으로 비동기로 콜백을 호출하기 때문에, IO처리에 대한 Blocking을 방지할 수 있다.
- 리스너 기반으로 작동한다. 즉 request가 들어오면, response를 반환하게 된다
- 그래서 만들어진 서버에 `addListener()`를 통해서 콜백 함수를 추가할 수도 있다.
    - 요청 이벤트 `request`와 클라이언트 접속 이벤트 `connection`을 따로 등록할 수도 있다. 그러기 위해 서버가 가진 이벤트 타입을 확인해야한다.


## 참고

- [nodejs web어플리케이션 설명 블로그](https://www.nextree.co.kr/p8574/)
