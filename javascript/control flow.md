#제어문

###for문

- **for..in..**

  열거가능한 속성에 대해서 반복

  ```jsx
  obj = {a:1, b:2, c:3};
  let o = 0;

  for (let o in obj){
  	console.log(abj.o]); // 1,2,3
  }
  ```

  객체의 키값을 인덱스에 할당

- **for..of**

  ```jsx
  arr = [1, 2, 3, 4];

  for (let i of arr) {
    console.log(i); // 1,2,3,4
  }
  ```

  배열의 내용을 인덱스에 할당

  루프 안에 console.log를 찍으면 코드가 매우 느리다. 웬만하면 문자열로 만들어서 한번에 출력해야 한다.
