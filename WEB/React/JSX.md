### JSX
자바스크립트를 확장한 문법 JS + HTML/XML 이라고 보면 된다.

### JSX 중괄호
JSX의 중괄호 내에는 JS 표현식을 넣을 수 있다.

### JSX도 표현식이다.
JSX를 일반적인 표현식처럼 다루어도 문제 없음.

### JSX는 엘리먼트를 반환한다.
화면에 보이는 것을 나타내는 객체를 React 엘리먼트라고 한다.

### Babel
JSX 형태로 적은 코드를 브라우저가 이해할 수 있는 형태로 변환해줌. React.createElement를 사용한 꼴로 변환.

### 주의점
for 이나 class같은 js 예약어와 html 어트리뷰트 이름이 겹치는 경우가 있다. 따라서 jsx에서 이들을 사용할 때는 
for 대신 htmlFor, class대신 className을 사용해야 한다.
