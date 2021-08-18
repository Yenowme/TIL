# 웹 스토리지

- 데이터를 db없이 웹 스토리지에 저장할 수 있다.
- 로컬스토리지
	- 세션이 끝나도 데이터가 지워지지 않는다.
	- 여러 탭이나 창을 띄워도 데이터가 하나의 공간에 저장된다.
- 세션스토리지
	- 웹페이지의 세션이 끝날 때 데이터가 지워짐.
	- 데이터가 탭과 창마다 따로 저장되고, 창이 꺼지면 사라진다.
- 브라우저별로 모두 별개로 지원된다.

## 사용법

1. 기본 API

	- 키와 값으로 이루어진 데이터를 저장한다
	- 문자형 데이터 타입만 지원한다. -> JSON사용하면 편하다.
	- window객체 내에 저장되어있다.
	<br>
	<br>
	- 키에 데이터 저장 : setItem
		```js
		localStorage.setItem("key", value);
		```
	- 데이터 불러오기 : getItem
		```js
		localStorage.setItem("key");
		```
	- 키에 데이터 삭제 : removeItem
		```js
		localStorage.removeItem("key");
		```
	- 모든 데이터 삭제
		```js
		localStorage.clear();
		```
	- 저장된 데이터 개수
		```js
		localStorage.length;
		```

