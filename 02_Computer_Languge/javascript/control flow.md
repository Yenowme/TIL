# 제어문

## for..in..

-   열거가능한 속성에 대해서 반복
-   객체에 사용
-   객체의 키값을 인덱스에 할당

    ```jsx
    const obj = {a:1, b:2, c:3};

    for (let o in obj){
    	console.log(o]); // a,b,c
    	console.log(abj.o]); // 1,2,3
    }
    ```

## for..of

-   배열에 사용
-   배열의 내용을 인덱스에 할당

-   루프 안에 console.log를 찍으면 코드가 매우 느리다. 웬만하면 문자열로 만들어서 한번에 출력해야 한다.

```jsx
const arr = [1, 2, 3, 4];

for (let i of arr) {
    console.log(i); // 1,2,3,4
}
```

## 배열 반복 객체

-   forEach

    ```js
    const arr = [1, 2, 3, 4];

    arr.forEach((itme) => console.log(itme)); //1,2,3,4
    ```

-   map

    -   리턴값으로 다시 배열을 생성한다. (중요)

    ```js
    const arr = [1, 2, 3, 4];

    arr = arr.map((itme) => itme + 1); //2,3,4,5
    ```

-   filter

    -   리턴값의 조건식을 만족하는 멤버로 배열을 생성한다.

    ```js
    const arr = [1, 2, 3, 4];

    arr = arr.filter((itme) => itme < 3); //1,2
    ```

-   some

    -   리턴하는 조건식이 참이 있는가를 알려준다

    ```js
    const arr = [1, 2, 3, 4];

    arr = arr.some((itme) => itme === 3); //true
    ```

-   every

    -   멤버가 모두 리턴하는 조건식을 만족하는지 알려준다.

    ```js
    const arr = [1, 2, 3, 4];

    arr = arr.every((itme) => itme > 0); //true
    ```

-   find

    -   조건에 부합하는 첫 배열요소를 하나 반환한다.

    ```js
    const arr = [1, 2, 3, 4];

    arr = arr.find((itme) => itme === 3); //3
    ```

-   findIndex

    -   조건에 부합하는 첫 배열요소의 인덱스를 반환한다.

    ```js
    const arr = [1, 2, 3, 4];

    arr = arr.findIndex((itme) => itme === 3); //2
    ```

-   includes

    -   매개변수가 배열의 멤버인지 아닌지 알려준다.

    ```js
    const arr = [1, 2, 3, 4];

    arr = arr.includes(3); //true
    ```
