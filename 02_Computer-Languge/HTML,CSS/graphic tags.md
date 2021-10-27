# 그래픽 tag

## 1. progress bar
```html
	<progress value = "30" max="100"></progress>
```
- 속성값
	- value : progress bar의 현재 값
	- max : progress bar의 최대값

- 특징
	```css
	progress {
	-webkit-appearance: none;
	}

	::-webkit-progress-bar {
	background-color: grey;
	}

	::-webkit-progress-value {
	background-color: orange;
	}
	```
	- 의사 선택자로 상태값의 스타일을 수정할 수 있다.
