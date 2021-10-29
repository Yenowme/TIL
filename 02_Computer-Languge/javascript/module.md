# javascript의 모듈

## 내보내기

1. exports 객체 생성

	```js
		//내보낼 모듈
		exports.fuc = function(){}
	```
2. export 키워드

	- [ ] 모듈화 진행시 사용하는듯?
	```js
		//내보낼 모듈
		export fuc = function(){}
	```
	- default export : 문서에 내보낼 요소가 하나 뿐일때 명시
	```js
		//내보낼 모듈
		export default fuc = function(){}
	```
## 가져오기

1. import
	```js
	import fuc from "./module";
	```
2. require
	```js
	const fuc = require("./module");
	```
