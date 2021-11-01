# XSS대응

-   XSS의 대응으로 `react`는 내부에서 `html`태그가 담긴 문자열을 렌더링하면, 해당 문자열을 그대로 렌더링하지 않는다.

<br>

## String형태의 html 렌더링하기

-   `dangerouslySetInnerHTML` 속성을 사용해야만 렌더링이 가능하다.

```html
<div>
    dangerouslySetInnerHTML={{__html: "
    <div></div>
    "}}>
</div>
```
