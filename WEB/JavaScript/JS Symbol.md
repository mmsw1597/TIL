### Symbol
심벌 값은 다른 값과 중복되지 않는 유일무이한 원시값이다. 

### 생성방법
```js
const mySymbol = Symbol('mySymbol');
```
new 연산자와 함께 호출할 수 없고, 심벌 함수 매개변수로 문자열의 설명을 전달할 수 있다. 

### Symbol.for
전역 심벌 레지스트리에서 심벌의 설명과 일치하는 심벌 값을 찾아서 반환하는 메서드

### Well-known Symbol
자바스크립트가 기본 제공하는 심벌 값

### Symbol.iterator
순화 가능한 이터러블은 Symbol.iterator를 키로 갖는 메서드를 가지고 있다. 
