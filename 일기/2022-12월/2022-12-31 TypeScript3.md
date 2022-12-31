## Call Signature
```ts
type Add = (a:number, b:number) => number;

const add : Add = (a,b) => a+b;
```
함수의 인자타입, 반환 타입을 커스텀 타입으로 정의하는 것.

## 오버로딩
함수가 받는 인자 타입을 여러가지로 주는 것. call signature가 여러개인 경우라고 생각하면 된다.
```ts
type Add = {
(a:number, b:number) => number;
(a:number, b:string) => number;
}

const add : Add = (a,b) => a+b;
```

## 다형성 (polymorphism)
```ts
type SuperPrint = {
  <T>(arr : T[]) => T
}

const superPrint : SuperPrint = (a) => a[0]

const a = superPrint([1,2,3,4])
const b = superPrint([true, false, true])
const d = superprint([1,true,"aasd"])
```
위와 같이 작성된 것을 제네릭이라고 한다. SuperPrint 타입을 사용할때 굳이 타입을 명시하지 않아도 된다. TS가 알아서 유추하기 때문이다. 

그냥 any를 쓰면 안될까? 생각도 드는데 TS로 부터 보호를 받으려면 any는 지양하는게 좋다. 예를들어 d.toUpperCase() 함수를 쓰는 경우 any로 했다면 에러가 뜨지 않는다.

```ts
const superPrint<T>(a: T[]){
  return a[0];
}
```
위와 같은 형태가 좀 더 많이 쓰인다.

```ts
type Player<E> = {
  name : string
  extraInfo : E

const who : Player<{favFood : string}> = {
  name : "asdf",
  extarInfo  : {
    favFood : "asdf",
  }
```

위는 또 다른 예시이다. React에서 useState<T> 이런 식으로 썼던 것도 제네릭에 해당한다.
  
  






