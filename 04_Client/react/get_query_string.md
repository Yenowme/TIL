# url query string 가져오기

## 설치

```bash
yarn add query-string
```

## 사용

```jsx
import queryString from "query-string"그

const questionId = queryString.parse(location.search);
```

-   queryString 객체의 parse로 location.search에 있는 쿼리스트링 객체로 변환

## 참고 블로그

[참고 블로그](https://justmakeyourself.tistory.com/entry/querystring-path-of-react-router)
