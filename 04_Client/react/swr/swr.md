# swr

## 1. 개요

-   `SWR`은 캐시로부터 데이터를 반환한 후, fetch 요청(재검증)을 하고, 최종적으로 최신화된 데이터를 가져오는 전략
-   `useSWR` 함수는 첫번째 인자로 통신 주소, 투번째 인자로 통신 함수를 받아 그 결과를 첫번째 객체로, 에러를 두번째 객체로 전달함.

## 2. 설치

```bash
yarn add swr
or
npm i swr
```

## 3. useSWR

1. 콜백 인자로 사용할 `fetcher` 함수를 제작한다

    ```jsx
    const fetcher = (url) => axios.get(url).then((res) => res.data);
    ```

2. `useSWR` 을 임포트 하고 함수 컴포넌트에서 사용하면 된다.

    ```jsx
    import useSWR from "swr";
    const fetcher = (url) => axios.get(url).then((res) => res.data);

    function Profile() {
        const { data, error } = useSWR("/api/user", fetcher);

        if (error) return <div>failed to load</div>;
        if (!data) return <div>loading...</div>;
        return <div>hello {data.name}!</div>;
    }
    ```

3. 커스텀 훅을 만들어서 사용해도 된다.

    ```jsx
    function useUser(id) {
        const { data, error } = useSWR(`/api/user/${id}`, fetcher);

        return {
            user: data,
            isLoading: !error && !data,
            isError: error,
        };
    }
    ```

    - 커스텀 훅을 제작해서 state를 props에 전달할 필요 없이 필요한 곳에서 모두 사용할 수 있다.
    - 여러번 재사용해도 요청은 한번으로 통일된다.

## 4. mutate

-   `useSWRConfig()` hook으로부터 mutate 함수를 얻을 수 있으며, `mutate(key)`를 호출하여 동일한 키를 사용하는 다른`SWR hook`에게 갱신 메시지를 전역으로 브로드캐스팅할 수 있다.
-   즉, api 재요청을 `mutate`함수 하나로 진행할 수 있음
-   로컬 데이터에 기반해서 포스트 요청을 보낼 떄, 서버에서 받아오지 않고 로컬을 먼저 업데이트 시킬 수 있음
    -   [ ] 좀 더 알아봐야함
    -   [https://swr.vercel.app/ko/docs/mutation](https://swr.vercel.app/ko/docs/mutation)

## 참고

-   [공식 사이트](https://swr.vercel.app/ko)
-   [공식 문서](https://swr.vercel.app/ko/docs/getting-started)
-   [typescirip-swr 참고 레포](https://github.com/diego3g/react-example-useswr/blob/master/src/services/useRequest.ts)
