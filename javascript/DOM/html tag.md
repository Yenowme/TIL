## 1.DOM객체 생성

    `document.createElement("div")`

## 2.DOM객체 설정

1. 내부 텍스트 설정

    `newDIV.innerHTML = "새로 생성된 DIV입니다.";`

2. 속성 추가

    `newDIV.setAttribute("id","myDiv");`

3. 스타일 추가

    `newDIV.style.backgroundColor="yellow"`
    `newDIV.style.setProperty("background-color","red")`

    setProperty(propertyname, value, priority)

    - propertyname : 속성 명
    - value : 속성값
    - priority : 우선순위 여부  ("important": 가장 먼저 적용)

## 3.트리의 삽입

`document.append(tag);`

1. 자식객체에 추가

    ```jsx
    부모.appendChild(DOM객체);
    부모.insertBefore(DOM객체, 기준자식);

    > querySelectorAll한 객체에는 적용 안된다 (중복 객체여서 그런가)
    ```

## 4.객체 삭제

## 참고

[https://coding-restaurant.tistory.com/212](https://coding-restaurant.tistory.com/212)
