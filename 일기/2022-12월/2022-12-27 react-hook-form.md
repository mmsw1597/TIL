## form 라이브러리를 사용해야 하는 이유
회원가입 form을 만든다고 생각해보자. 이름, 성, 생년월일, 아이디, 비밀번호 등등 많은 input을 작성해야 하고 그에 따라 많은 state를 관리해줘야 한다.
코드가 복잡해질 뿐더러 onChange 함수도 각각 만들어 줘야 하며, 더 나아가 form validation을 구현해야 한다면 일은 훨씬 복잡해진다.
즉, 매 input마다 유효한 값을 집어넣었는지 확인을 해야하는데 input이 많을수록 복잡해진다. 이를 해결하기 위해 form 라이브러리를 사용하는 것이다.

## Form Validation
![image](https://user-images.githubusercontent.com/55936770/209565724-7b6f9e45-a7dc-48b1-b58e-3038be407004.png)

1. onSubmit에서 form 조건을 만족하지 않을 시 error에 대한 set함수를 반환하도록 한다.
2. error를 나타내기 위해선 error state를 input마다 만들어 줘야함.
3. error 발생 시, input 옆에 error 메시지가 출력되도록 함.
4. onChange에서 입력 시 toDoError를 빈문자열로 만들어서 다시 입력할 때는 에러메시지가 지워지도록 함.

## react-hook-form
위와 같은 검증, 수 많은 input을 관리해주는 라이브러리. 지금부터 사용방법에 대해 알아보자.

## useForm
![image](https://user-images.githubusercontent.com/55936770/209566511-e8ea72ee-2a24-4fd7-ae88-2af13b3711cf.png)

useForm은 register라는 것을 제공함.

![image](https://user-images.githubusercontent.com/55936770/209566540-07da2ea9-559c-4857-b5a4-8bef00ca516b.png)

register 함수 호출 반환 값은 위와 같은 객체로 되어있음 여기서 onBlur는 input 바깥을 클릭했을때를 의미함.

![image](https://user-images.githubusercontent.com/55936770/209566779-dde34890-bed7-474a-a41d-a4c8e9b44f91.png)

위 객체를 한번에 input의 attr로 주기 위해서 스프레드 문법을 사용.

![image](https://user-images.githubusercontent.com/55936770/209566804-36bdf8fa-f67b-42dc-ab46-db30c09a6aca.png)

useForm은 watch라는 함수도 제공하는데, 이는 input의 값을 계속 주시하는 역할을 함.

![image](https://user-images.githubusercontent.com/55936770/209566830-8e691c07-236c-4fd9-925c-f3b66de41e84.png)

실제 watch의 반환값을 출력해보면 위와 같음. input에 무언가를 입력할 때마다 input의 값을 뱉어냄.

## useForm 2
![image](https://user-images.githubusercontent.com/55936770/209567136-2ac2df50-0792-48f5-a565-8c7325e7053e.png)

이제 위와 같이 input이 많은 상황을 고려해보자. register의 인자는 띄어쓰기와 대문자는 금지이다. register 덕분에 input마다 새로운 state를 만들 필요가 없어졌다.

![image](https://user-images.githubusercontent.com/55936770/209567606-b7fea366-68e2-4ce5-b1cc-1bcc9e141f9d.png)

이제 submit을 다뤄보자. useForm은 handleSubmit 함수도 제공한다. 이 함수가 Validation을 제공하게 된다.

![image](https://user-images.githubusercontent.com/55936770/209568029-42380848-caea-48be-aabd-6cc1568bdb8f.png)

handleSubmit은 2가지 인자를 받는다. 첫번째는 입력 값이 유효할때 호출되는 함수, 두번째는 입력 값이 유효하지 않을 때 호출되는 함수다. 두번째는 필수는 아니다. 첫번째는 필수다.
임시로 onValud의 data는 any로 설정하였다.

![image](https://user-images.githubusercontent.com/55936770/209568133-948c05a2-b6b3-4fe2-a564-7fab4ccab408.png)

data를 출력해보면 위와같이 출력된다. 

![image](https://user-images.githubusercontent.com/55936770/209568454-b47877ab-832c-431d-ab7d-a992fca2f70f.png)

required 속성을 추가하고 싶으면 위와 같이 작성. 왜 html attr로 required를 주지 않냐면 악의적인 브라우저 상에서 코드 변경을 금지하기 위함이다.
해당 칸을 비우고 submit할 경우 해당 칸으로 커서를 자동으로 옮겨준다.

![image](https://user-images.githubusercontent.com/55936770/209568724-0fd4d9d8-1535-40e7-b148-944878f41814.png)

최소 길이를 명시하기 위해선 위와 같이 작성하면 된다.

![image](https://user-images.githubusercontent.com/55936770/209568842-c51024f9-0229-4edd-af61-591bd9dc9834.png)

error를 직접 확인하고 싶으면 formState를 활용하면 된다. 

![image](https://user-images.githubusercontent.com/55936770/209568929-0e3a35f8-dfc9-42ee-92a1-ce3c68915a3f.png)

![image](https://user-images.githubusercontent.com/55936770/209569010-7e5d0003-a8ab-4484-9d46-4d3eb1c431f9.png)

Email은 required, minLength 10 조건이 붙었었고 빈 값으로 submit 했을때 error를 출력해보면 위와 같다. error의 타입을 보여준다. 여러가지일 경우 그 중 하나만 출력한다. 
error 객체에는 message라는 것도 보이는데 이는 오류 메시지를 의미한다. 개발자가 직접 설정가능하다.

![image](https://user-images.githubusercontent.com/55936770/209569338-89c5fb1d-1010-4303-9e62-5805621e5da1.png)

메시지는 위와 같이 전달 가능하다.

![image](https://user-images.githubusercontent.com/55936770/209569499-83fc3f77-1df6-4547-8ac5-71582bf9a62a.png)

객체로도 전달이 가능하다. 핵심은 위의 모든 것들을 내가 직접 구현할 필요없이 자동으로 라이브러리가 해준다는 점이다.

## 정규표현식 검증
![image](https://user-images.githubusercontent.com/55936770/209574282-641f4ca2-b4ca-4b8c-a33f-6b1d6ba9b85a.png)

pattern 값도 줄 수 있다. 여기에는 정규표현식을 입력할 수 있고, 해당 정규표현식에 매칭되지 않는다면 에러를 출력한다.
minLength 프로퍼티와 마찬가지로 객체를 넘겨도 되는데, 추가로 message 값도 넘길 수 있다.

## Error 메시지 화면 상에 출력
![image](https://user-images.githubusercontent.com/55936770/209574638-9fbeb7a2-9783-46fb-977b-7f2b7a084418.png)

우선 위와 같이 디스트럭처링을 활용하여 errors를 추출하자.

![image](https://user-images.githubusercontent.com/55936770/209574665-741d6a91-47fe-4936-92d9-4bc1db0ad917.png)

위와 같이 작성하면 에러가 출력된다. 주의할 점은 error가 없는 경우 errors가 undefined가 되므로 물음표는 필수다. 그리고 as를 써서 type error를 해결하자.
input이 first_name이었다면 email 대신 first_name을 기입. error type에 따라 조건문을 따로 주지 않아도 되는 것이 매력적이다.

## Form 인터페이스
![image](https://user-images.githubusercontent.com/55936770/209575078-deabed35-b8a0-4639-81ad-e3f994d0ec17.png)

위 예시로 인터페이스를 위와 같이 만들면 된다. 이때 required가 아닌 것은 물음표를 반드시 붙여주자.

![image](https://user-images.githubusercontent.com/55936770/209575183-ed6c82b0-6b63-4b8f-85c8-dbdf2e6d4f01.png)

인터페이스 적용은 위와 같다. default value도 줄 수 있는데 위와 같이 디폴트 값을 주면 input에 값이 디폴트 값으로 채워져 있다.

## 커스텀 Validation
이제 나의 의도에 맞춰 직접 검증을 구현해 보자.

![image](https://user-images.githubusercontent.com/55936770/209575994-64a08596-dbd1-4239-b7c8-c3c66af68226.png)

useForm은 setError를 제공한다. setError는 특정한 에러를 발생시키게 해준다. 

![image](https://user-images.githubusercontent.com/55936770/209576285-cb42e19f-cb9b-46ab-b4b5-8cae43c08600.png)

onValid 함수에 위와 같이 작성해주자. 이렇게 하면 minLength 등 구현되지 않은 검증에 대해서도 에러를 출력시킬 수 있다.
input에 관련된 error 외에도 백엔드 서버가 닫혔을때 에러도 출력해줄 수 있다.

![image](https://user-images.githubusercontent.com/55936770/209576409-8ffbc0fd-dec6-40e3-92ca-ed5e4b69d2f6.png)

위와같이 에러를 추가해주고

![image](https://user-images.githubusercontent.com/55936770/209576426-84d11182-3b9b-4d9f-84d1-0a19a630b953.png)

위와 같이 작성해주자. 이때 extraError는 특정 항목에 해당되는 에러가 아닌 전체 form에 적용되는 에러이다. 조건은 부가적인 error를 if문으로 명시해주면 된다. 위 사진은
생략되어 있다.

![image](https://user-images.githubusercontent.com/55936770/209576571-c1316a56-5251-4f64-99aa-86b20749ada2.png)

위와 같이 에러가 난 input에 대해 커서가 자동으로 옮기게 하고 싶다면 shoudFocus를 true로 설정하면 된다.

![image](https://user-images.githubusercontent.com/55936770/209576868-b01ddf9f-9cc0-4350-857d-43ae4a90d500.png)

또다른 방법은 validate 값을 설정하는 것인데, 함수 값을 넘겨주고 인자 값은 input에 입력된 값이며, true 또는 false를 반환한다. 

![image](https://user-images.githubusercontent.com/55936770/209576958-2886237d-fc4c-4ee7-8d1e-ca2c3e85b84d.png)

위는 응용의 예시이다. admin을 포함한다면 false를 반환하도록 설정한다. 아마 선정적인 닉네임을 걸러줄때 사용하지 않을까..?
true false 외에도 문자열을 반환할 수도 있는데 이는 에러로 간주되고 문자열은 에러 메시지가 된다.

![image](https://user-images.githubusercontent.com/55936770/209577192-e2d5128a-6b65-4586-9f8c-f4694d788b73.png)

세련되게 위와 같이 작성 가능하다. 실제 개발에서는 api를 호출할 수 도 있다. 예를들어 아이디 중복 검사가 있을 것이다.

![image](https://user-images.githubusercontent.com/55936770/209577269-a7551e47-246a-4379-9754-53016c7623f5.png)

동시에 여러 검증을 거치게 하고 싶으면 위와 같이 객체를 넘기도록 작성. 키 값은 아무거나 상관없다.















