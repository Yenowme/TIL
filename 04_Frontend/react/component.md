# component

div대신 태그를 단어로 바꿔서 사용할 수 있다.

## 함수형 컴포넌트

-   hook과 함께 요즘 대체적으로 사용됨

```jsx
function Modal({form, children}){
return(<><div>{form}<div><>)
}

return <Modal from = "hi"></Modal> //div대신 사용
```

-   주의점
    -   이름 시작은 대문자로
    -   변수 범위를 잘 알아야 한다.
-   반복적으로 나타나는 컴포넌트를 만들면 관리가 편해진다.
-   props(매개변수)를 통해 데이터를 주고받을 수 있다.

## 클래스형 컴포넌트

```jsx
import React, { Component } from "react";

class Hello extends Component {
    render() {
        const { color, name, isSpecial } = this.props;
        return (
            <div style={{ color }}>
                {isSpecial && <b>*</b>}
                안녕하세요 {name}
            </div>
        );
    }
}

Hello.defaultProps = {
    name: "이름없음",
};

export default Hello;
```

-   .defaultProps 로 디폴트 인자 설정 가능
-   `render()`메서드 필수
-   커스텀 메서드
    -   class안에 멤버로 넣어주면 됨
    -   handle...로 네이밍 짓는게 관습
    -   그러나 이벤트 핸들러로 적용되면 this가 적용이 안된다.
        ```jsx
        constructor(props) {
            super(props);
            this.handleIncrease = this.handleIncrease.bind(this);
            this.handleDecrease = this.handleDecrease.bind(this);
          }
        ```
        이렇게 구현해야함 (생성자 바인딩)
        -   [ ] super(props)?
        -   `this.핸들링함수 = this.핸들링함수.bind(this)`를 해주면 this가 적용된다.
    -
