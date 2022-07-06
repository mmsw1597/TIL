### 내부 슬롯과 내부 메서드
내부슬롯과 내부 메서드는 자바스크립트 엔진의 구현 알고리즘을 설명하기 위해 사용하는 의사 프로퍼티와 의사 메서드이다. 이들으 직접적으로 호출하거나 접근할 수 있는 방법을 제공
하진 않는다. 단 일부 내부 슬롯과 내부 메서드에 한하여 간접적으로 접근할 수 있는 수단을 제공하기는 한다.

### 프로퍼티 어트리뷰트
자바스크립트 엔진은 프로퍼티를 생성할 때 프로퍼티의 상태를 나타내는 프로퍼티 어트리뷰트를 기본값으로 자동 정의한다. 종류는 값(Value), 갱신 가능 여부(Writable), 열거 가능 여부
(Enumerable), 재정의 가능 여부(Configurable)을 말한다. 이들은 모두 내부슬롯이며 직접 접근이 불가능하고 Object.getOwnPropertyDescriptor 메서드를 사용하여 간접적으로 확인 가능하다.
이때 이 메서드는 매개변수로 객체의 참조와 프로퍼티 키를 전달받고 프로퍼티 디스크립터 객체를 반환한다.

### 데이터 프로퍼티
키와 값으로 구성된 일반적인 프로퍼티이다. value, writeable, configurable, enumerable의 어트리뷰트를 갖고 있다.
* [[Value]] 어트리뷰트<br>
프로퍼티 키를 통해 접근하면 반환되는 값이다. <br>
* [[Writable]] 어트리뷰트<br>
불리언 값을 가지며 프로퍼티의 값의 변경 가능 여부를 나타낸다. false인 경우 읽기 전용 프로퍼티가 된다.
* [[Enumberable]] 어트리뷰트<br>
프로퍼티의 열거 가능 여부를 나타내며 불리언 값을 가진다. false인 경우 for...in문이나 object.key메서드 등으로 열거 불가능 하다.
* [[Configurable]] 어트리뷰트 <br>
프로퍼티의 재정의 가능 여부를 나타내며 불리언 값을 가진다. false인 경우 프로퍼티 삭제, 프로퍼티 어트리뷰트 값의 변경이 금지된다. 단 writable이 true면 value와 writable값을
변경하는 것은 가능하다.<br>

### 접근자 프로퍼티
자체적으로 값을 갖진 않으나 다른 프로퍼티의 값을 읽거나 저장할 때 사용하는 접근자 함수로 구성된 프로퍼티다.
* [[Get]] 어트리뷰트<br>
접근자 프로퍼티 키로 프로퍼티 값에 접근시 [[Get]]의 값 getter함수가 호출되고 그 결과가 반환된다.
* [[Set]] 어트리뷰트<br>
접근자 프로퍼티를 통해 데이터 프로퍼티 값을 저장할 때 호출되는 접근자 함수다. 접근자 프로퍼티 키로 프로퍼티 값을 저장시 [[Set]]의 값 setter함수가 호출되고 그 결과가 반환된다.
* [[Enumberable]] 어트리뷰트
* [[Configurable]] 어트리뷰트

```java
const person = {
  firstName: 'Lee',
  lastName: 'ddd',
  
  get fullName(){
    return `${this.firstName} ${this.lastName}`;
  },
  set fullName(name){
    [this.firstName, this.lastName] = name.split(' ');
  }
};

person.fullname = 'park gunwoo'; //setter
console.log(person.fullName); //park gunwoo //getter
```

### 프로퍼티 정의
Object.defineProperty 메서드를 사용하면 프로퍼트의 어트리뷰트를 정의할 수 있다.
```java
const person = {};

Object.defineProperty(person, 'firstName', {
  value: 'park',
  writable: true,
  enumberable: true,
  configurable: true
});
```
누란된 어트리뷰트는 디폴트 값으로 undefined, false가 된다. 참고로 Object.defineProperties메서드를 사용하면 여러 개의 프로퍼티를 한번에 정의 가능하다.

### 객체 변경 감지
객체는 변경 가능한 값이나 객체의 변경 방지 메서드를 통해 이를 방지할 수 있다. 방지의 강도는 3개, 확장금지 (preventExtensions), 밀봉 (seal), 동결 (freeze)가 있다.

### 객체 확장 금지
Object.preventExtensions 메서드를 통해 객체의 확장을 금지한다. 프로퍼티 추가가 금지도며 삭제, 읽기, 쓰기, 어트리뷰트 재정의는 가능하다.
```java
const person = {name: 'Lee'};

console.log(Object.isExtensible(person)); // true
Object.preventExtensions(person);

person.age = 20; //무시됨
```

### 객체 밀봉
Object.seal 메서드를 통해 객체를 밀봉한다. 프로퍼티 추가와 삭제, 어트리뷰트 재정의가 불가능하지만 읽기와 쓰기는 가능하다.
```java
const person = {name: 'Lee'};

Object.seal(person);

person.age = 20; //무시
delete.person.name; //무시
person.name = 'Kim' //가능
Object.defineProperty(person, 'name', { configurable:true}); //Error
```

### 객체 동결
Obejct.freeze 메서드를 통해 객체를 동결하다. 오로지 읽기만 가능하다.
```java
const person = {name: 'Lee'};

Object.freeze(person);

person.age = 20; //무시
delete.person.name; //무시
person.name = 'Kim' //무시
Object.defineProperty(person, 'name', { configurable:true}); //Error
```
주의할 점은 freeze 함수는 중첩 객체까지는 동결 불가능하다. 중첩 객체까지 동결시키려면 재귀적으로 frezze메서드를 호출해야한다.

  


