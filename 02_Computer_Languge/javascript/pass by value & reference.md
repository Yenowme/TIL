c 언어에서는 value로 전달할 지 reference로 전달할 지를 포인터를 통해 내가 직접 제어할 수 있었다. 그러나 자바스크립트에서도 그게 가능한가? 이런 경우 자바스크립트는 어떤식으로 값을 옮길까?

c에서 구현하던 swap을 통해 실험 해 보았다.

```javascript
function swap_(a, b) {
	let temp;

	temp = a;
	a = b;
	b = temp;
	console.log(a, b); // 2 1
	return ;
}

let a = 1;
let b = 2;

swap_(1,2);

console.log(a,b); // 1 2
```

함수 내부에서는 값이 바뀌었지만, 외부에서는 함수를 사용했음에도 값이 바뀌지 않았다. 값을 pass by value했다는 뜻. 값 자체만 전달하고, 해당 주소값은 전달하지 못했다.

그러나 배열, 오브젝트, 함수와 같은 경우는 자바스크립트가 알아서 reference로 넘기게 된다. 따라서

```jsx
function swap_(obj) {
	let temp;

	temp = obj.a;
	obj.a = obj.b;
	obj.b = temp;
	console.log(obj.a, obj.b);
	return ;
}

let obj = {
	a : 1,
	b : 2
};

swap_(obj);

console.log(obj.a,obj.b);
```
### 결론
위와같이 값을 객체에 넣어서 객체 자체를 전달하면 된다.

---

[참조 블로그](https://medium.com/nodesimplified/javascript-pass-by-value-and-pass-by-reference-in-javascript-fcf10305aa9c)
