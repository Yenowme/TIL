# reset css

html태그들에는 기본적으로 들어가있는 스타일들이 있다. <br>
그 중 마진이나 패딩으로 인해 스타일을 입힐 때 불편한 부분들이 생기기도 한다. <br>
그걸 없애기 위해 reset.css로 스타일을 초기화 한다.

1. 외부 파일 가져오기
- nnormalize.css에서 파일을 가져와 적용시킨다.
- 모든 스타일을 리셋하기보단, 기본 스타일은 남겨두고 브라우저별 다른점만 초기화시켜준다.
- CDN 기법을 통해 링크로 적용시킬 수 있음 : https://cdnjs.com/libraries/normalize
```html
  <head>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/normalize/8.0.1/normalize.min.css" />
  </head>
```

2. 파일 생성
- 외부에서 파일을 생성해 import해서 적용시킨다
- `@import "reset.css"`
```css
html,body,div,span,applet,object,iframe,h1,h2,h3,h4,h5,h6,p,blockquote,pre,a,abbr,acronym,address,big,cite,code,del,dfn,em,img,ins,kbd,q,s,samp,
small,strike,strong,sub,sup,tt,var,b,u,i,center,dl,dt,dd,ol,ul,li,fieldset,form,label,legend,table,caption,tbody,tfoot,thead,tr,th,td,article,
aside,canvas,details,embed,figure,figcaption,footer,header,hgroup,menu,
nav,output,ruby,section,summary,time,mark,audio,video {
  margin: 0;
  padding: 0;
  border: 0;
  font-size: 100%;
  font: inherit;
  vertical-align: baseline;
}
/* HTML5 display-role reset for older browsers */
article,aside,details,figcaption,figure,footer,header,hgroup,menu,
nav,section {
  display: block;
}
body {
  line-height: 1;
}
ol,
ul {
  list-style: none;
}
blockquote,
q {
  quotes: none;
}
blockquote:before,
blockquote:after,
q:before,
q:after {
  content: "";
  content: none;
}
table {
  border-collapse: collapse;
  border-spacing: 0;
}
input:focus {
  outline: none;
}
a {
  color: inherit;
  text-decoration: none;
}
```

## 출처
https://velog.io/@jewon119/01.CSS-%EA%B8%B0%EC%B4%88-Reset-CSS
