## Framer Motion
다양한 애니메이션을 쉽게 구현할 수 있도록 도와주는 라이브러리. 해당 라이브러리 사용법을 익혀보자.

한 가지 주의할 점을 짚어보자.

![image](https://user-images.githubusercontent.com/55936770/209797390-5874f77b-d1ab-4628-9299-45c2027754a6.png)

framer motion으로 애니메이션을 적용시키고 싶으면 위와같이 단순히 div를 작성하면 적용할 수 없다.

![image](https://user-images.githubusercontent.com/55936770/209797563-dc4ff495-d9cd-46f7-b4ef-7ae9b43323fd.png)

위와 같이 작성해야 함을 유의하자. motion은 framer-motion 패키지에서 import한 것이다. 근데 만약 styled-component를 사용하고 있다면 어떻게 해야 할까?

![image](https://user-images.githubusercontent.com/55936770/209798080-3324d93d-3f04-4fa5-af9c-bd35c0cbb6b0.png)

그냥 위와 같이 작성하면 된다. 이 점을 유의하고 이제 배워보자.

## 기본
들어가기전에 motion의 prop으로는 순수 css로 조작할 수 있고, spring이라는 효과가 디폴트로 적용되어 있다.

![image](https://user-images.githubusercontent.com/55936770/209798239-29194d40-fd11-40e1-acf7-22a3a942f86d.png)

motion이 적용된 컴포넌트에는 animate라는 attr을 적용할 수 있다. 위 사진은 border-radius 10px -> 100px 로 변환하는데 애니메이션을 통해 변환되는 코드이다.

![image](https://user-images.githubusercontent.com/55936770/209798488-01d71d37-0b7f-4ba8-bfd0-908f26f08183.png)

또다른 attr에는 trasnsition이 있다. 한 상태에서 다른 상태로 움직이는 방식을 정의한다. 위는 delay를 주고 3초후에 애니메이션이 발동되도록 한 것이다.

![image](https://user-images.githubusercontent.com/55936770/209798644-45ccc159-f706-4983-b419-b13a29afaa8b.png)

duration은 변환하는데 3초가 걸리도록 설정한 것이다.

![image](https://user-images.githubusercontent.com/55936770/209798916-e1078018-26e2-473f-a7c6-32ae914c52bf.png)

initial은 초기 상태를 정의한다. 크기가 0이었다가 원상태로 애니메이션을 통해 변하는 모습을 보여주게 된다.

![image](https://user-images.githubusercontent.com/55936770/209799296-cf407c8e-2c96-4c51-a699-1146811d485d.png)

위와 같이 작성하면 더이상 spring 효과가 나타나지 않는다. tween은 선형적인 애니메이션을 나타나게 해준다. 외에도 transition에는 stiffness, damping 등
다양한 속성을 제공하고, 해당 속성은 공식문서를 통해 알아보는 것이 좋다.

## Variants
![image](https://user-images.githubusercontent.com/55936770/209800962-34dad8ea-64b2-4344-ab77-962a7290dc05.png)

좀더 코드를 깔끔하게 하는 방법이다. start는 initail에 대응되고 end는 animate에 대응된다.

![image](https://user-images.githubusercontent.com/55936770/209801945-7b4686c2-658d-4dfb-83e2-ce06068bf14e.png)

부모의 variants는 자식에게 상속된다.

![image](https://user-images.githubusercontent.com/55936770/209802355-84490afa-72eb-4b9e-82e3-d12f3e434d1b.png)

자식에게 속성을 추가로 부여하고자 하면 위와 같이 작성. 자식 각각에게 다른 delay를 주고자 하면 어떻게 해야 할까?

![image](https://user-images.githubusercontent.com/55936770/209803002-18737f0d-d01d-44e9-b000-bcf3edeb2aa0.png)

delayChildren은 자식 컴포넌트에게 똑같이 0.5를 준다는 의미. staggerChildren은 자식의 첫번째부터 0.5씩 delay를 차례대로 더한다는 의미.

![image](https://user-images.githubusercontent.com/55936770/209803553-70797570-7601-4405-8a22-1fb64f5819c0.png)

y가 양수면 아래쪽이라는 뜻 따라서 해당 애니메이션은 아래에서 위로 나타나게 함. y, x는 css가 아니라 motion의 속성임.

## place-items
justify-items과 align-items를 합친 축약형

## place-self
justify-self와 align-self를 합친 축약형

## Gesture
![image](https://user-images.githubusercontent.com/55936770/209804036-69f301c9-4dc2-4a5f-9c98-c45aa6b65320.png)

whileHover는 listener의 일종으로 해당 컴포넌트에 마우스를 올리면 작동하도록 하는 애니메이션. 추가로 whileTab은 클릭하고 있을때 나타남. drag attr은
부모 컴포넌트 내에서 다른 위치로 드래그 가능하게 함. 어따 쓸진 모르겠음

![image](https://user-images.githubusercontent.com/55936770/209804483-0b0a5fcb-055f-40a1-a905-7b08334a76b8.png)

variants 활용. 추가로 해당 attr에 조건문 명시 가능. 

















