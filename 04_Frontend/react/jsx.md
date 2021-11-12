# jsx

```jsx
class App extends Component {
    render() {
        return (
            <div className="App">
                <div>hi</div>
            </div>
        );
    }
}
```

-   html대신 js내에 html문법을 넣어줄 수 있다.
-   `class` 대신 `className`함수를 써야한다. (class 키워드와 겹치기 때문.)
-   `snake-case` 대신 `camelCase`를 사용해야한다 (빼기 키워드와 겹침.)
-   tag는 하나만 리턴 가능, 여러 자매 태그는 불가능
    -   `<> </>` 로 묶어줄 수도 있다.

## 데이터바인딩

-   원래는 `document`시리즈를 통해 태그를만들고~ 이너텍스트도 넣어주고 해야했음
-   모든 타입의 데이터가 지원된다
-   리액트는 `{}` 안에 변수명을 넣으면 데이터가 넣어진다
    ```jsx
    import { Component } from "react";

    let a = "hi"; //데이터 받기

    class App extends Component {
        render() {
            return (
                <div className="App">
                    <h1>{a}</h1> //데이터 넣어주기
                    <div>메인 글</div>
                </div>
            );
        }
    }
    ```

### 이미지 넣기

-   import로 디렉토리에 았는 이미지를 가져올 수 있다.
-   가져온 변수명에 `{}`를 활용해서 넣으면 됨
