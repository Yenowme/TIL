## 정의
---
하나의 문제는 단 한 번만 풀도록 하는 알고리즘이다. 재귀함수를 이용해서 풀이를 진행할 때, 이미 푼 문제를 다시 푸는 비효율을 줄이는 방법도 그 중 하나이다. (메모리제이션)

다이나믹 프로그래밍은 다음의 가정 하에 사용할 수 있다.
1. 큰 문제를 작은 문제로 나눌 수 있습니다.
2. 작은 문제에서 구한 정답은 그 정답에 의존하는 큰 문제에서도 적용됩니다.

어떻게 보면 재귀를 사용해서 문제를 푸는 방법과 비슷한데, 좀 더 효율적인 방법을 사용한다.


## 방법
---

1. 메모이제이션
    - 재귀를 사용해서 top-down방식으로 문제를 풀 때, 작은 문제로 쪼개는 과정에서 작은 문제들이 겹쳐 불필요한 계산을 요구하는 경우가 있음. 그럴 때 배열에 답을 저장해 불필요한 계산을 방지한다.

	    ```c
		# include <stdio.h>

		int d[100];

		int fibonacci(int x){
			if(x == 1) return 1;
			if(x == 2) return 2;
			if(d[x] != 0) return d[x];
			return d[x] = fibonacci(x - 1) + fibonacci(x - 2);
		}
		```
2. bottom up
	- 반복문을 사용해 작은 문제부터 큰 문제를 풀어가는 방법

		```jsx
		let X;
		let arr = [0,0,1,1];

		for(let i = 4; i <= X; i++)
		{
			if (i % 3 === 0)
				arr[i] = Math.min(arr[i/3] + 1, arr[i] || X);
			if (i % 2 === 0)
				arr[i] = Math.min(arr[i/2] + 1, arr[i] || X);
			arr[i] = Math.min(arr[i-1] + 1, arr[i] || X);
		}
		console.log(arr[X]);
		```
## 참고
---
참고 블로그 : https://blog.naver.com/ndb796/221233570962
