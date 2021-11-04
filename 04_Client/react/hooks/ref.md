## useRef

-   특정 돔에 직접 접근해서 조작 가능 (like `getElementById`)
    -   javascript에서 특정 Dom을 선택하는 역할 ex) getElementById, querySelector
-   외부 라이브러리 사용할때 유용하다. 그 외에는 state로 관리하는게 좋다.
-   선언한 객체를 컴포넌트의 `ref` attribute에 넣고, 객체의 `current`를 호출하면 해당 객체에 접근이 가능해진다.

```jsx
import {useRef} from 'react

const App = () => {

}
```
