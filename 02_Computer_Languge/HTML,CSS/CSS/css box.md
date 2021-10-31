- `box-sizing: border-box;`
  - padding이나 boder을 줬을 때, 박스 사이즈 너비에 padding과 boder을 무시하게 해준다.
  - 일러스트에 선 안으로 기능이랑 비슷
- `display: block` 은 옆에 다른요소가 올 수 없다 (`h1`, `p`, `div` 등)
  - 높이와 너비를 가진다.
    - 즉, `margin`, `border`, `padding`, `contents`를 가지게 된다.
    - collapsing margins
      - 두개의 마진이 같다면 하나로 취급됨.. (상하에서만 일어남)
- `display: inline` 은 옆에 다른요소가 온다. (`a`, `span`, `img` 등)
  - 높이와 너비가 없다.
  - 상하 마진이 적용되지 않는다

---

- `flex`개념

  - inline-block 으로 line 속성의 태그에 넓이와 높이를 줄 수는 있다.

    - 그러나 사이 간격을 설정할 수 없다. 마진/패딩을 먹이기 짜증남. 반응형 지원 안됨.

    → display: flex로 해결 가능!

  - 사용시

    - 자식 엘리먼트X 부모에게만 display 설정
      - 직접적인 부모만 영향을 줄 수 있음.
    - 두개의 축을 가지고 있다.

      - main axis(수평 _- 하지만 축도 변경 가능_)
        - `justify-content` 로 콘텐츠간 (가로)넓이 조정
        - `flex-direction:` 로 축 변경 - row가 기본, colum이 세로축으로
      - cross axis(수직)

        - `aling-item` 로 콘텐츠간 넓이 조정

      - wrap이란 화면이 이동할때 컨텐츠가 줄어든는 것.?
        - `flex-wrap`으로 조정
      - 100vh = 화면넓이: viewport height

- `position`
  - `:fixed`
    - 픽스되기 전 고정된 위치에 처음 위치
    - 더 위의 레이어로 이동
  - `:relative;`
    - 처음 위치한 곳을 기준으로 조금 이동하고 싶을때`top:, left:` 와 함께 사용 가능하다.
    - flex와 충돌없이 사용가능
  - `:absolute`
    - relative부모 (body)의 가장 극단으로 이동 `top:, left:` 와 함께 사용.
