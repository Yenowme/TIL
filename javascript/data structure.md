### Queue 구현

- FIFO
- 데이터를 집어넣는 선형자료형

```jsx
class Queue {
  constructor() {
    this._arr = [];
  }
  enqueue(item) {
    this._arr.push(item);
  }
  dequeue() {
    return this._arr.shift();
  }
}

const queue = new Queue();
queue.enqueue(1);
queue.enqueue(2);
queue.enqueue(3);
queue.dequeue(); // 1
```

`.push()` : 배열의 끝에 값 추가

`.shift()` : 배열의 첫번쨰 요소 뺴서 반환
