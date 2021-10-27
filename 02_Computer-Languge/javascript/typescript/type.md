```tsx
/*변수 타입 지정*/
let name: string = "string";

/*함수 타입 지정*/
function fun(x: number): number {
    return x;
}
```

-   타입을 변수에도 저장할 수 있다. (대문자로 시작하는 컨벤션)
-   변수, 함수, 매개변수, 리턴값에 타입 지정이 가능

## 타입 정의

-   사용자가 직접 타입을 정의하는 경우

```tsx
// 사용자 정의 타입 operation 정의
// 타입 별칭(Type Alias)
type operation = {
    data: number[];
    output: (num: number) => number[];
};

// 사용자 정의 타입 operation 적용 예시
let sum: operation = {
    data: [10, 30, 60],
    output(num) {
        return this.data.map((n) => n + num);
    },
};

let multiply: operation = {
    data: [110, 230, 870, 231],
    output(num) {
        return this.data.map((n) => n * num);
    },
};
```

## 타입 어설션

-   사용되는 변수가 특정 타입임을 단언. 캐스팅과 비슷하지만 컴파일 과정에서만 사용됨.
-   앵글 브라켓 `<>` 사용 → JSX에서는 사용 불가

    ```tsx
    let assertion: any = "타입 어설션은 '타입을 단언'합니다.";

    // 방법 1: assertion 변수의 타입을 string으로 단언 처리
    let assertion_count: number = (<string>assertion).length;
    ```

-   `as` 문법 사용

    ```tsx
    let assertion: any = "타입 어설션은 '타입을 단언'합니다.";

    // 방법 2: assertion 변수의 타입을 string으로 단언 처리
    let assertion_count: number = (assertion as string).length;
    ```

## 타입 종류

| 이름                     | 설명                                         |
| ------------------------ | -------------------------------------------- |
| null,?                   | 널 지정                                      |
| string                   | 문자열                                       |
| int                      | 숫자                                         |
| boolean                  | 참,거짓                                      |
| undefine                 | undefine                                     |
| Binint                   | big int                                      |
| array, `T[]`, `Array<T>` | 배열                                         |
| `{}`, `{T:string}`       | 배열                                         |
| any                      | 모든 타입                                    |
| never                    | 항상 오류를 출력하거나, 리턴값을 가지지 않음 |
| union                    | 여러타입 동시 지정 가능 연산자               |
