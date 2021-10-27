- pseudo selector (pseudo classes)- 태그의 특정 상태 구분

  - `:hover` 포인터를 올렸을 때만
  - `.class:nth-child(n+1)`

    = 모든 class의 n번째에 1번째것 선택

    even은 짝수, odd는 홀수

    - `form:hoverd input:focus {}` 처럼 부모의 조건이 달성되면 조건이 달성된 자식을 선택하게 할수도 있다.

- Pseudo-elements (요소의 특정 부분 스타일링) - 태그의 속성으로 구분

  - `::placeholder` 와 같이 attribute의 속성 스타일을 변경할수도 있다.
  - `::selection` 은 선택된 대상을 변경 가능 > 웹사이트 개성 업

- custom properties (스타일화)

  - 자주 사용하는 값들을 전역 변수로 정리

  ```css
  :root {
    —-main-color: vale;
  }

  class {
    color: var(--main-color);
  }
  ```

  - .class{ color: var(-var-name)}

    - 사용 예시

  - 익스플로어에서는 사용 불가..

- 연결자(combinator) - 선택자 결합으로 다양한 선택

  - `.a .b`

    = a 를 부모로 가진 b를 선택

  - `parents > direct_children`

    = parents를 바로 위 부모로 가지고있는 direct children을 선택

  - `.a + .b`

    = a 다음에 오는 형제 'b'를 선택

  - `.a ~ .b`

    = a의 형제인 b를 선택

  - `input[attribute="value"]{}` 태그의 속성값으로 해당태그를 선택도 가능

    - `~=` 은 우항의 부분을 포함하는 것들 전부 선택
    - $ 은 우항으로 끝나는 모든것 선택 (ex img)
    - `: focust-within` 은 자식이 focused가 되면 선택됨

  - 여러개의 선택자를 콤마로 함께 선택할 수 있다.
