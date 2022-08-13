### Hook
함수 컴포넌트에서는 state를 사용할 수 없다. 함수 컴포넌트에서 state를 지원하게 하는 것이 Hook이다.

### Hook의 중요성
단순히 함수 컴포넌트에 변수를 선언하고 변수 값을 변경시켜도 재렌더링이 일어나지 않아, 웹 페이지에 반영이 되지 않는다. 따라서 hook을 사용해야 한다.

### useState
state를 사용하기 위한 Hook. 반드시 set함수로 변수를 업데이트 해야 한다.
```js
const [변수명, set함수명] = useState(초기값);
```

### useEffect
side effect를 수행하기 위한 hook. side effect란 렌더링이 끝난 이후에 수행되어야 하는 일. 
```js
useEffect(이펙트 함수, 의존성 배열);
```
의존성 배열의 값중 하나라도 변경될 시, 이펙트 함수가 실행된다. 

```js
useEffect(이펙트 함수, []);
```
effect 함수가 mount, unmount 시에 단 한번씩만 실행 되는 형태

```js
useEffect(이펙트 함수);
```
effect 함수가 컴포넌트가 업데이트 될때마다 호출되는 형태

### useEffect의 return
useEffect의 return 문은 컴포넌트가 unmount될 때 호출된다.

### useMemo
Memoized value를 리턴하는 hook. 

### useCallback
useMemo와 유사하지만 값이 아닌 함수를 반환한다.

### useRef
ref란 특정 컴포넌트에 접근할 수 있는 객체를 의미. 



