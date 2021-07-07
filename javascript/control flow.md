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
