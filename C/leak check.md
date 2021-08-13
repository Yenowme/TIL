## 1. valgrind

---

c 언어에서 메모리 릭 체크를 도와주는 프로그램

### 사용 방법

- -g 옵션으로 컴파일 후에 실행
- 기본 사용은 `valgrind --tool=memcheck` 을 호출하여 실행 한다.

### 플래그

|이름|설명|
|---|---|
|tool=memcheck||
|leak-check=full|메모리 에러가 날 경우 소스 파일명과 라인 위치를 출력. 디버깅 컴파일 (-g3)일 경우에만 가능
|—log-file=log.txt|체크 결과를 로그에 저장|
|

주로 사용하는 건 `valgrind --leak-check=full --log-file=log ./실행파일 명`

### 결과 해석

LEAK SUMMARY 부분을 확인, 몇 바이트의 메모리 Leak이 발생했는지 확인 가능

```makefile
==72654== LEAK SUMMARY:
==72654==    definitely lost: 4 bytes in 1 blocks
==72654==    indirectly lost: 0 bytes in 0 blocks
==72654==      possibly lost: 0 bytes in 0 blocks
==72654==    still reachable: 0 bytes in 0 blocks
```

- definitely lost 중심으로 보면 된다.

→ 그 결과를 만들어진 로그파일에 검색하면 상세 내용 확인 가능.

<br>

## 2. leak

---

1. lldb나 while(1)로 무한루프를 건다
2. 프로그램이 실행되게 켜 놓고, 다른 터미널에서 leak 프로그램을 사용한다.

    `leak ${프로그램명}`

<br>

## 3. fsanitizer=address

---

1. 컴파일시 `-g3 -fsanitize=address`를 옵션으로 넣어준다.
2. 실행한다
3. 릭이 있다면 해당 값에 대한 오류를 뱉어낸다.

<br>

## 출처
---

[valgrind 사용법](https://stormaa.tistory.com/5)
