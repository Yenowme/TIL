## 얕은 복사(Shallow Copy)

- 참조(주소)값의 복사를 나타낸다!

```jsx
const obj = { vaule: 1 }
const newObj = obj;

newObj.vaule = 2;

console.log(obj.vaule); // 2
console.log(obj === newObj); // true
```

- `obj` 객체를 `newObj` 객체에 할당하였으며, 이를 **참조 할당**이라 부른다
- 데이터가 그대로 생성되는것이 아닌, 해당 데이터의 참조 값(메모리주소)를 전달하여 한 데이터를 공유하는 것이다.

## 깊은 복사(Deep Copy)

- 데이터 값 자체의 복사를 나타낸다!
- 자바스크립트의 원시 타입은 깊은 복사가 되지만, **참조 타입은 일반 할당 연산자로 얕은 복사가** 된다

### 객체 깊은 복사 방법

1. `Object.assign()` 메소드 활용
    
    ```jsx
    const obj = { a: 1 };
    const newObj = Object.assign({}, obj);
    ```
    
2. 전개 연산자 `...` 활용
    
    ```jsx
    const newObj = { ...obj };
    ```
    

→ 두 방법 모두 2뎁스 이상의 복사는 얕은 복사로 전환됨

1. JSON 객체 메소드 
    
    ```jsx
    const newObj = JSON.parse(JSON.stringify(obj));
    ```
    
    - JSON.stringyfi 와 JSON.parse를 활용해서 복사
    - 2뎁스 이상의 복사가 가능하지만, 문자열 기반이기 때문에 내부 함수는 복사되지 않음
2. 커스텀 재귀 함수
    
    ```jsx
    function deepCopy(obj) {
      if (obj === null || typeof obj !== "object") {
        return obj;
      }
    
      let copy = {};
      for (let key in obj) {
        copy[key] = deepCopy(obj[key]);
      }
      return copy;
    }
    ```
    
    - 문제를 원칙적으로 해결해 주는 재귀함수
    - 이미 구현된 모듈도 있다.
3. lodes 모듈의 cloneDeep 사용

```jsx
const lodash = require("lodash");

const newObj = lodash.cloneDeep(obj);
```

→ 함수까지 깊은 복사가 가능

## 참고

[[JavaScript] 얕은 복사(Shallow Copy)와 깊은 복사(Deep Copy)](https://velog.io/@recordboy/JavaScript-%EC%96%95%EC%9D%80-%EB%B3%B5%EC%82%ACShallow-Copy%EC%99%80-%EA%B9%8A%EC%9D%80-%EB%B3%B5%EC%82%ACDeep-Copy#objectassign)
