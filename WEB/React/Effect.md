### 렌더링
state가 변경되면 컴포넌트 내에 있는 모든 코드가 재실행되어 리렌더링이 일어나게 된다. 여기서 굳이 다시 실행되지 않아도 되는 코드도
재실행되는 것이 성능 저하를 일으킬 수 있다. 이를 해결하는 것이 useEffect이다.

### useEffect
```js
useEffect(f, []);
```
f 함수는 맨 처음 렌더링 될때 한번만 실행되고 이후 리렌더링이 일어나도 다시 호출되지 않게된다.

```js
useEffect(f, [...dep]);
```
f 함수는 dep가 변화할때 리렌더링이 일어나게 된다.

### useEffect 반환
useEffect가 반환하는 함수는 요소가 destroyed 될때 실행되는 함수를 의미한다.
