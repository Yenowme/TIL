# hoisting

## 개요

-   hoisting = "끌어올리다"
-   인터프리터가 변수와 함수의 메모리 공간을 **선언 전**에 미리 할당하는것
    -   `var` 의 경우 `undefined`로 초기화됨
    -   `let` `const` 의 경우 초기화되지 않음 - 선언문이 나오기 전에는 TDZ(temperately Dead Zone)처리가 됨. 사용불가
        → let 과 var의 중요한 차이점

## 예시

-   JavaScript는 함수의 코드를 실행하기 전에 함수 선언에 대한 메모리부터 할당함
-   함수를 호출하는 코드를 함수 선언보다 앞서 배치할 수 있다.

    ```jsx
    catName("클로이");

    function catName(name) {
        console.log("제 고양이의 이름은 " + name + "입니다");
    }

    /*
    결과: "제 고양이의 이름은 클로이입니다"
    */
    ```
