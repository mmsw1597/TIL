### Truthy 와 Falsy
자바스크립트는 불리언 타입이 아닌 값을 Truthy와 Falsy로 구분한다. Falsy의 종류는 아래와 같다
* false
* undefined
* null
* 0, -0
* NaN
* ''<br>
이외에는 모두 Truthy이다. Truthy는 모두 true로 평가되고 Falsy는 모두 false로 평가된다.

### 암묵적 타입 변환
개발자의 의도와 상관없이 자바스크립트 엔진에 의해 암묵적으로 타입이 자동으로 변환되는 것을 암묵적 타입변환이라고 한다.
``` java
var x = 10;
var str = x + ''; // 숫자를 문자열로 자동 형변환

1 +'2' // "12"
```
위와 같이 + ''를 통해 피연산자를 문자열로 타입 변환해준다.
```java
+'' // 0
+'0' // 0
+'1' // 1
+'string // NaN
'0' * 1 // 0, *산술 연산자는 숫자 타입이 아닌 타입을 숫자로 바꿔준다.
```
단항 연산자 +를 통해 피연산자를 숫자로 타입 변환해준다. 이외에 불리언 타입은 0, '', false, undefined, null, NaN 해당 값들이 조건식에 있다면 이들은 
모두 불리언으로 자동 타입변환 된다.

### 명시적 타입 변환
기본적으로 생성자 함수를 new 연산자 없이 호출하는 방법이 있다.
```java
String(1); // '1'
String(NaN); //'NaN'

Number('0') // 0
Number(true) // 1

Boolean('x') // true
Boolean(undefined) //false
```
이외에 메서드를 활용하는 방법이 있다.
```java
(1).toString(); //'1'
(Infinity).toString(); //'Infinity'

parseInt('0'); // 0 (문자열만 가능)
parseInt('-1'); // -1

//!!를 쓰면 부울린 타입으로 형변환
!!'x'; //true 
!!''; //false
```

### 단축 평가
예제로 먼저 살펴보자
```java
'Cat' && 'Dog' // 'Cat'은 true이고 &&연산자는 좌항에서 우항으로 표현식을 평가하며 &&연산자는 두 항 모두 true임을 확인한다. 따라서 'Cat'을 평가하고 'Dog'를 평가하고 'Dog'리턴
'Cat' || 'Dog' // ||는 둘중 하나만 true이면 되고 첫 항에서 true이므로 우항은 평가할 필요가 없다. 따라서 'Cat'을 반환
```
이런식으로 자바스크립트에서 && 와 ||은 피연산자를 타입변환하지 않고 그대로 반환한다. 또한 표현식을 평가하는 도중 평가 결과가 확정되면 나머지 평가 과정을 생략한다. 이를 단축 평가라고 한다.
이를 어떻게 유용하게 사용할까? 아래에 예시를 적어보았다.

```java
/* 변수가 null 또는 undefined 인지 확인하고 프로퍼티를 참조할 때 */
var elem = null;
var value = elem && elem.value //null 반환, elem은 null이므로 false이고 &&연산이므로 좌항에서 평가가 끝난다.

/* 함수 매개변수에 기본값을 설정할 때 */
function getStringLength(str){
  str = str || ''; //str이 undefined라면 빈 문자열을 반환한다.
  return str.length;
}

//ES6의 매개변수 기본값 설정
function getStringLength(str = ''){
  return str.length;
}
```

### 옵셔널 체이닝 연산자
ES11에서 도입된 옵셔널 체이닝 연산자 ?.는 좌항의 피연산자가 null 또는 undefined인 경우 undefined를 반환, 그렇지 않으면 우항의 프로퍼티 참조를 이어간다.
```java
var elem = null;

var value = elem?.value;
console.log(value); //undefined
```
기존에는 &&연산자로 이 기능을 구현했지만 &&는 0이나 ''도 false로 간주하여 좌항을 그대로 반환한다. 이는 ''나 0은 기본값으로 유의미할 수 있기 때문에 문제가 된다.
하지만 옵셔널 체이닝 연산자는 오로지 null, undefined가 아니면 우항을 참조한다.

### null 병합 연산자
ES11에서 도입된 null 병합 연산자 ??는 좌항의 연산자가 null 또는 undefined면 우항을 반환하고 그렇지 않으면 좌항을 반환한다. 변수에 기본값을 설정할 때 유용하다.
``` java
var foo = null ?? 'dafault';
console.log(foo); //'default'
```
기존에는 ||연산자로 이를 구현했지만 이또한 0이나 ''를 false로 간주하기 때문에 0이나 ''를 기본값으로 유효하게 사용한다면 문제가 된다. 하지만 병합 연산자 ??는 
오로지 null이나 undefined인 경우에만 false로 간주한다.











