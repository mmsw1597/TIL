### Styled-Component
react에서 css를 좀 더 편하게 입히는 방법. css 모듈을 import 하거나 html 태그에 style 어트리뷰트를 쓸 필요가 없음.

### 사용방법
```js
const Father = styled.div`
  display: flex;
`;
const BoxOne = styled.div`
  background-color: teal;
  width: 100px;
  height: 100px;
`;
const BoxTwo = styled.div`
  background-color: tomato;
  width: 100px;
  height: 100px;
`;

function App() {
  return (
    <Father>
      <BoxOne />
      <BoxTwo />
    </Father>
  );
}
```
위 코드는 현재 중복된 부분이 많은 상태.

### 컴포넌트 변경.
``` js
const Father = styled.div`
  display: flex;
`;
const Box = styled.div`
  background-color: ${props => props.bgColor};
  width: 100px;
  height: 100px;
`;

function App() {
  return (
    <Father>
      <Box bgColor = "teal"/>
      <Box bgColor = "tomato"/>
    </Father>
  );
}
```

### 컴포넌트 확장
```js
const Father = styled.div`
  display: flex;
`;
const Box = styled.div`
  background-color: ${props => props.bgColor};
  width: 100px;
  height: 100px;
`;

const Circle = styled(Box)`
  border-radius: 50px;
`;

function App() {
  return (
    <Father>
      <Box bgColor = "teal"/>
      <Circle bgColor = "tomato"/>
    </Father>
  );
}
```

### as
```js
function App() {
  return (
    <Father>
      <Btn>Log in</Btn>
      <Btn as ="a" href="#">Log in</Btn>
    </Father>
  );
```
어떤 컴포넌트의 style은 그대로 쓰되 태그만 바꾸고 싶은 경우 as를 쓰면 된다.

### selector
```js
const Box = styled.div`
  height: 100px;
  width: 100px;
  background-color: tomato;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: ${animation} 1s linear infinite;
  span{
    font-size : 18px;
    &:hover{
      font-size: 50px;
    }
  }
`;


function App() {
  return (
    <Wrapper>
      <Box>
        <span>ㅋㅋ</span>
      </Box>
    </Wrapper>
  );
}
```
Box 컴포넌트 내에서 span을 선택하려면 단순히 css처럼 span을 선택하면 된다. 그리고 span 중괄호 내의 &는 span을 의미한다. 이 방식의 경우 태그 이름에 의존하고 있기 때문에
span 태그이름이 변경되면 적용되지 않는다.

```js
const Box = styled.div`
  height: 200px;
  width: 200px;
  background-color: tomato;
  display: flex;
  justify-content: center;
  align-items: center;
  animation: ${animation} 1s linear infinite;
  ${Emoji}{
    &:hover{
      font-size: 98px;
    }
  }
`;

const Emoji = styled.span`
    font-size: 36px;
`;

function App() {
  return (
    <Wrapper>
      <Box>
        <Emoji as ="p">ㅋㅋ</Emoji>
      </Box>
    </Wrapper>
  );
}
```
위는 Emoji 컴포넌트를 만들고 as를 이용하 p태그로 바꾸었음에도 제대로 동작하는 것을 확인하는 코드다. Emoji는 Box내에서 hover 이벤트가 발생하면 속성이 적용된다.
