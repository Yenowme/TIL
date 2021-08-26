# async&await

## async 함수

```js
async function f() {
  return 1;
  return Promise.resolve(1)
  //둘 다 같음
}

f().then(alert); // 1
```
- 함수 앞에 async를 붙이면 항상 프라미스를 반환한다.
- 해당 함수 안에서만 await키워드가 동작한다
## await
```js
let value = await promise;
```
- async 함수 안에서만 동작한다.
- 비동기 함수들을 동기적으로 명시해서 처리할 수 있다.

## 에러 핸들링

- try catch문을 이용할 수 있다.

### 출처
https://ko.javascript.info/async-await#ref-308
