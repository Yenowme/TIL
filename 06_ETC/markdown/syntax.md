# markdown syntax

-   html tag 사용가능

## title

### code

```md
# text ->h1

## text ->h2

### text ->h3
```

# h1 text

## h2 text

### h3 text

<br/>
<br />

## Image

### code

```md
![image name](image URL)

or

 <img src="image URL" alt="img name" width="200"/>
```

## 도표

`|`와 `-` 를 사용해서 생성 가능

```md
| First Header                | Second Header                |
| --------------------------- | ---------------------------- |
| Content from cell 1         | Content from cell 2          |
| Content in the first column | Content in the second column |
```

⬇

| First Header | Second Header |
| ------------------ 타입 정의 방법

-   클래스와 개념이 비슷하지만, 추상 클래스와 좀 더 비슷(?)

### 인터페이스 vs 커스텀 타입

-   인터페이스는 중복 선언 가능
    ```tsx
    interface ButtonInterface {
      onInit():void;
      onClick():void;
    }

    ...

    interface ButtonInterface {
      onToggle():void;
    }
    ```
-   `extends`를 사용한 상속이 가능 (`,`를 통해 여러개의 상속도 가능)

## 옵션설정

```tsx
interface ButtonInterface {
    // 속성 이름 뒤에 ? 기호가 붙으면 옵션 속성이 됩니다.
    onInit?(): void;
    onClick(): void;
}

class ButtonComponent implements ButtonInterface {
    // onInit 메서드가 설정되지 않아도 오류를 발생하지 않습니다.
    onClick() {
        console.log("버튼 클릭");
    }
}
```

-   속성 뒤에 `?` 를 붙여서 타입을 옵셔널하게 설정할 수 있음

## 읽기 전용 속성

```tsx
interface Notebook {
    readonly CPU: string;
    readonly RAM: string;
}

let mackbook: Notebook = {
    CPU: "2.9GHz 코어 i9",
    RAM: "32GB",
};

// [오류]
// 'RAM'은 읽기 전용 속성 또는 상수로 변경할 수 없습니다.
// (property) Notebook["RAM"]: string
macbook.RAM = "128GB";
```

-   `readonly` 를 붙이면 `const` 처럼 선언 이후 변경 시도를 할 수 없음

## 인덱스 시그니처 속성 선언

-   클래스 타입의 경우 인터페이스를 모두 충족한다면 새로운 속성이 추가해도 오류가 나지 않음
-   객체 리터럴의 경우에는 새로운 속성 추가시 오류가 난다. 그 해결방법으로 아래와 같이 인덱스 시그니처를 설정하면 됨.

```tsx
interface ButtonInterface {
    onInit?(): void;
    onClick(): void;

    // 인덱스 시그니처
    [prop: string]: any;
}

const button: ButtonInterface = {
    type: "button",
    disabled: false,
    onClick() {
        console.log("버튼 클릭");
    },
};
```

-   `[prop:string]: any` 를 추가하면 객체의 새 속성을 자유롭게 추가할 수 있음

## 함수 인터페이스

````tsx
interface FactorialInterface {
  (n: number): number;
}

const facto: FactorialInterface = (n) => {
  if (n === 0) { return 0; }
  if (n === 1) { return 1; }
  return n * facto(n - 1);
};
```---------- | ---------------------------- |
| Content from cell 1         | Content from cell 2          |
| Content in the first column | Content in the second column |

---

## 참고

-   [깃허브 공식 문서](https://guides.github.com/features/mastering-markdown/)
````
