### interface
object를 설명하는 TS문법. 함수를 정의할때 ts의 경우 매개변수에 타입을 명시해야 하는데, 만약 타입이 객체라면 interface를 이용하여 객체안의 프로퍼티가 무슨 타입인지 명시해야한다.

```s
interface PlayerShape{
  name: string;
  age: number;
}

const sayHello = (playerObj : PlayerShape) =>
  `Hello ${playerObj.name} you are ${playerObj.age} years old.`;
```
`playerObj : PlayerShape` 이부분에 주목. `playerObj`가 어떤 객체인지, 요소가 무슨 타입인지 설명해주는 interface가 `PlayerShape` 라는 뜻.

### Required/Optional
```ts
interface CircleProps{
  bgColor: string;
  borderColor? : string;
}
```
위의 경우 `?`가 없는 prop은 필수적이라는 뜻이고 `?`가 붙은 prop은 선택적이라는 것이다.

### 주의점
styled-component와 component간의 요소의 필수 유무가 불일치가 일어나면 에러가 발생한다.
```ts
interface CircleProps{
  bgColor: string;
  borderColor? : string;
}

interface ContainerProps{
  bgColor: string;
  borderColor : string;
}

function Circle({bgColor, borderColor} : CirCleProps){
  return <Container bgColor = {bgColor} borderColor = {borderColor} />;
}
```
이 경우 null 병합 연산자 `??`를 써서 borderColor에 초기값을 줌으로써 해결가능하다. `borderColor ?? bgColor`

### TS와 State
TS에서 `useState`를 사용할 경우 TS는 초기값을 보고 state의 타입을 추론한다. 만약 초기값으로 number 타입을 줬다면 그 state의 타입은 number로 제한된다.
이를 원하지 않는다면 다음과 같이 작성하면 된다.
```ts
const [value, setValue] = useState<number|string|boolean>(0);
```

