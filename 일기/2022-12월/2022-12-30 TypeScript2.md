## 타입스크립트 추론
TS에선 TS가 타입을 추론하도록 하는 암시적 타입이 있고 직접 개발자가 타입을 명시하는 명시적 타입이 있다. 간단한 변수는 TS가 타입을 추론하도록 암시적 타입을 사용하도록 하자.
왜냐하면 일일이 타입을 명시하면 코드가 복잡해지고 시간도 오래 걸리기 때문

## 필수가 아닌 값
```ts
const player : {
  name : string,
  age ?: number
}
```
위와 같이 age는 필수 값이 아닌데 만약 age를 이용한 if문을 사용하게 되면 TS는 age가 undefined일 수 있다고 에러를 표시한다. 이럴땐 && 연산자를 활용하자.

```ts
if(player.age && player.age < 10){
}
```
## Alias
```ts
type Player {
  name : string;
}

const player : Player = {
  name : "adsf",
}
```
## 함수 리턴 타입
```ts
function playerMaker(name : string) : Player{
  return {
    name : name,
  };
}

const playerMaker = (name : string) : Player => ({name});
```
보통 함수 리턴 타입은 명시하지 않아도 리턴 값을 받을 때 오류를 표시하진 않는다. 그렇지만 명시를 해준다면 리턴 값을 담은 변수는 TS로 부터 보호를 받을 수 있다.

## Read Only
```ts
type Player = {
  readonly name : string
}
```
위와 같이 작성하면 변수 값을 변경 불가능해 진다.

## Tuple
배열을 생성하게 해주고 배열의 구성 타입 순서, 최소 길이를 명시하는 방법
```ts
const player : [string, number, boolean] = ["asdf", 1, true];
```
## 특별한 타입들

### unknown 
예를들어 API로 부터 응답을 받는데 API가 어떤 객체 타입을 줄지 모른다면 이 타입을 사용하면 된다. unknown 타입을 사용하려면 먼저 typeof로 해당 변수의 타입을 조건문으로
확인하고 사용해야 TS가 허용해준다.

### void
아무것도 반환하지 않는 함수의 반환 타입을 명시할때 사용. 필수는 아님. 대신 명시하면 보호받을 수 있음.

### never
실행 되면 안되는 타입을 명시할때 사용. 에러를 발생시키는 타입에 사용됨. 자주 사용하진 않음.



