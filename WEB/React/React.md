### React
React js가 element를 생성하고 event listener를 더하는 기능을 추가해줌

### ReactDOM
React Element를 가지고 HTML로 바뀌게 하는 역할을 함

### root div
ReactDOM이 React element를 가져다 놓을 곳

### render
react element를 root div에 삽입하라는 뜻. 즉, 웹 페이지에 렌더링함.

### createElement
1. 첫번째 인수는 태그이름
2. 두번째 인수는 property가 포함된 객체 (id, class, style, eventlistener 등)
3. 세번째 인수는 contents

### React의 렌더링
재렌더링이 일어날 컴포넌트를 확인하고, react는 이전 상태와 다른 부분만 파악하여 그 부분만 리렌더링하게 된다.
