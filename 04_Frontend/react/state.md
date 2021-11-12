# state

-   웹이 app처럼 동작하게 만들 수 있다. 즉, state가 바뀌면 즉시 새로고침 없이 재 렌더링된다.
    → 자주 바뀌는, 중요한 글들을 저장하면 좋음
-   사용예제
    ```jsx
    import React, { useState } from "react";

    let [state, setState] = useState("hi");
    ```
    -   `state` 에는 data가 들어감
    -   `setState`
        -   변수를 변경하는 함수
    -   `useState`의 매개변수에는 배열, 객체 모두 들어갈 수 있다.
        -   배열 변수 수정시
        ```jsx
        function changedata() {
            var newArray = [...state]; //deep copy
            newArray[0] = "change";
            setState(newArray);
        }
        ```
        state data는 직접 조정하면 안되고, 복사해서 담아야함.
        혹은`concat()`사용가능
