# textarea 높이 가변길이로 변경

```jsx
onChange={(value) => {
          const newHeight: string = event?.target.scrollHeight + "px";
          console.log(newHeight);
          textArea.style.height = newHeight; //따로 가져온 객체
          setValue(value);
        }}

```

-   `onChange` 함수에 `setValue`를 받는 라이브러리때문에, value를 전달해서 함수처럼 사용했더니 잘 진행되었음
-   `event` 객체를 써봤더니 사용되었다. 아마 저 라이브러리에서 받은 함수가 실제 `event-lisner`에서 사용되기 때문인듯.
-   근데 `event.target.style.height = event.target.scrollHeight+"px"` 는 Invalid left-hand side in assignment expression. 에러가 생김.. 이유 불명
    -   -> `getElemntByClassName()` 으로 돔 객체 다시 선택해서 수정하니 괜찮아짐.
