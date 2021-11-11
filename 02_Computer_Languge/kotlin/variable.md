# 변수

## 기본 선언

-   `val` : read only 변수. 선언 후 변수값을 바꿀 수 없음
-   `var`: 선언 후 변수값을 바꿀수 있다.
-   `const val` ≠ `val`
    -   `const val` 은 컴파일시 결정, val 은 런타임때 결정

### lateinit

```kotlin
lateinit var x : String
x = "Initialized"
println(x)
```

-   처음에 var 형태의 x가 나중에 사용될 것이며, String 타입이라는 것만 정해 준다.

-   그리고 이후에 사용할 때에 값을 지정해 주면 x에 값이 들어간다.cl

### by lazy

by lazy는 이렇게 사용된다.

```kotlin
val x : String by lazy { "Initialized!" }
println(x)
```

-   처음에 val 형태의 x가 나중에 사용될 것이며, '사용 시에' 어떤 값이 들어가는지를 정해 준다.

-   이후에 따로 지정할 필요는 없고, 두 번째 줄과 같이 x를 사용하는 첫 순간에 x에 값이 들어간다.

-   하지만 만약 x가 다른 계산식의 영향을 받거나, 다른 변수의 초기화 이후에만 값을 알 수 있다면 이 방식을 사용할 수 있다.
