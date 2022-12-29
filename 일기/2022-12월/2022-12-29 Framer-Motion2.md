## Motion Value
drag를 어디다 쓸지 몰랐는데, drag를 했을때 컴포넌트의 x, y 를 추적하는게 가능하다. 컴포넌트의 위치에 따라 배경색을 바꾼다던지 등, 다양한 기능을 구현할 수 있다.
motion value는 컴포넌트의 x, y를 추적하게 해주는 중요한 기능이다.

![image](https://user-images.githubusercontent.com/55936770/209947040-27d51156-f774-4f55-b89a-d3d589925553.png)

dragSnapToOrigin은 드래그 했을때 원래 위치로 되돌아오도록 하는 attr이다.

![image](https://user-images.githubusercontent.com/55936770/209947373-75f562d9-8a86-4343-9867-57a341aee01b.png)

위와 같이 useMotionValue 훅을 사용하면 x를 추적할 수 있다. 그런데 console log 를 했음에도 컴포넌트를 움직였을 때 x가 출력되지 않는다. 
이유는 motion value는 x를 변경시켜도 react 렌더링 사이클을 발동시키지 않기 때문이다. 한 마디로 x는 state가 아니다. 요약하면 motion value가 바뀌어도
컴포넌트는 리랜더링 되지 않는다. 

이는 장점으로 작용한다. 왜냐하면 컴포넌트에 API를 적용했다고 하면 컴포넌트를 움직일때 마다 API를 재호출하지 않는다. 그렇다면 x값을 어떻게 계속 출력할까?

![image](https://user-images.githubusercontent.com/55936770/209947974-dbf1ee7a-831d-4493-a53f-33c52a36fd2e.png)

답은 useEffect를 사용하면 된다. 이제 해당 컴포넌트를 움직일때마다 x의 값이 무더기로 출력되는 것을 볼 수 있다.
이를 실제로 이용하진 않을 것이다. 단지, 리랜더링이 일어난다면 어떤일이 벌어지고, 왜 리랜더링을 안되게 했는지 이해하기 위함이다. 빗금이 쳐진 이유도 이런 이유일 것이다.

![image](https://user-images.githubusercontent.com/55936770/209948313-5902d8d3-3555-4cb1-970c-4f43ca761938.png)

set 함수를 이용하면 x를 특정 위치로 변경 가능하다. 이때 애니메이션은 일어나지 않는다. 

![image](https://user-images.githubusercontent.com/55936770/209948818-8c23b8ce-cfe5-4b7d-b028-61463d1785ba.png)

이제 x값을 이용해서 컴포넌트 크기를 조절해보자. 그러기 위해선 useTransform 훅을 사용해야 하는데, 총 3개의 인자를 받는다. 첫번째는 추적하고자 하는 값, 두번째는 
이벤트가 발동되는 x의 값, 3번째는 그 x의 값에 따라 scale이 갖는 값들이다. 2, 3번째 인자는 배열이어야 한다. 그리고 순서, 크기를 맞게 작성해야 한다.

![image](https://user-images.githubusercontent.com/55936770/209949440-29a9bc3b-017e-4c68-a1c9-0a0ee09850b3.png)

위와 같이 작성하면 드래그 할때마다 컴포넌트 크기가 변경된다. useEffect는 없어도 된다.

## Scroll 감지
![image](https://user-images.githubusercontent.com/55936770/209950437-30546aa6-3b20-47c9-af21-513c1ff367a1.png)

useScroll 훅을 사용하면 scrollY, scrollYProgresss 값을 받아올 수 있다. scrollY는 픽셀 값이고 scrollYProgress는 0과 1사이 값으로 전체 페이지의 
몇 퍼센트까지 스크롤이 진행됐는지에 대한 값이다. X값도 얻어올 수 있다.

## SVG 애니메이션
![image](https://user-images.githubusercontent.com/55936770/209953742-8b0dd2e5-1ecc-45a1-9316-2e885861a5a0.png)

svg 선을 따라 그리는 애니메이션은 위와 같이 작성. 참고만 하자.

![image](https://user-images.githubusercontent.com/55936770/209954465-d01bfb6c-824d-4e78-8d19-42b5aa570db1.png)

특정 property마다 애니메이션을 다르게 적용하고 싶으면 위와 같이 작성. variants는 필수인듯 하다.

## Animate Presence
![image](https://user-images.githubusercontent.com/55936770/209956051-a5a9e804-b947-46ad-ba88-e3dd401d17ff.png)

React App에서 사라지는 componenet를 animate하도록 해주는 기능. Animate Presence의 규칙은 visible 상태여야 한다는 것. 또한 내부에는 조건문이 들어가야 함.
위와 같이 작성하면 Animate Presence는 안쪽에 사라지거나  나타나는게 있을 경우 그것을 animate하게 해준다. 반드시 variants를 적용해야 한다. 그렇지 않으면 애니메이션이
나타나지 않는다.

## 슬라이드 구현
![image](https://user-images.githubusercontent.com/55936770/209968767-d3496450-b2ba-46a5-88f5-79440ca93761.png)

box variants는 위와 같다.

![image](https://user-images.githubusercontent.com/55936770/209968803-a1c8f552-f1ac-4a6f-8b0c-7019d5b6f083.png)

슬라이드는 위와 같이 구현. 현재 위 코드는 문제점이 있다. 슬라이드를 넘길 때 컴포넌트가 살짝 아래로 튄다는 점인데 이는 absolute로 해결해야 한다. Box 컴포넌트에
position: absolute를 추가하면 정상적으로 작동. 대신 위치를 수동으로 조절해야 한다.

next버튼은 추가했고 prev버튼을 추가하려고 하였더니 애니메이션은 앞으로 가지만 숫자는 뒤로 이동하는 현상이 발생한다. 이를 해결해보자. 각 컴포넌트에는 key가 존재한다.
react는 key를 가지고 각 컴포넌트가 고유하다고 생각한다. key가 바뀌어도 react는 이전 컴포넌트는 사라졌다고 생각하고 새로운 컴포넌트가 생겼다고 생각하게 된다.

![image](https://user-images.githubusercontent.com/55936770/209970469-b1d80a07-71c7-4249-b0c8-3a4998608d51.png)

즉, key가 바뀌면 리랜더링이 일어난다. 이는 variants의 initail, animate, exit를 발동시키게 만든다. 따라서 위와 같이 작성해도 동작한다.

![image](https://user-images.githubusercontent.com/55936770/209972002-83afe9c0-658c-49a5-af96-7e88f85008a3.png)

custom은 variants에 prop을 전달하는 것이라고 보면 된다. custom에 back을 보내면 variants에서 해당 prop을 사용할 수 있다.

![image](https://user-images.githubusercontent.com/55936770/209972078-d35e3735-f2c7-4802-b3b4-c2bcda51da4c.png)

prop에 따라 값을 변경하는 모습. 그러나 여전히 버그가 있다.

![image](https://user-images.githubusercontent.com/55936770/209975280-a4585da1-16ef-4e57-90bd-2f6ef5ee2d2b.png)

중요한 점인데 back prop을 전달할때 반드시 객체로 주어야 한다. 안그러면 버그가 발생한다. 그에따라 prop interface도 따로 작성해주면 좋다.
또한, mode = "exit"는 exit 애니메이션이 끝나야 다음 initial 애니메이션이 발생하도록 하게 하는 것인데, 해당 모드를 적용하면 슬라이드가 굉장히 느려진다. 참고만 하자.

## 레이아웃
![image](https://user-images.githubusercontent.com/55936770/209976353-4a8324dd-a87f-4e3e-b64f-be988c93890a.png)

어떤 컴포넌트의 css가 바뀔 때, 해당 변화를 애니메이션화 시키고 싶으면 단순히 layout attr을 불여주면 된다.

![image](https://user-images.githubusercontent.com/55936770/209977259-16742d20-23d9-4ae8-bd5e-a22805c1203f.png)

2개의 컴포넌트에 같은 레이아웃 아이디를 부여하면 두 컴포넌트는 서로 연결되고 react는 두 개가 서로 같다고 생각하게 된다. 서로다른 부모의 컴포넌트여도 애니메이션이
연결되는 것을 볼 수 있다.

## 예제
![image](https://user-images.githubusercontent.com/55936770/209979229-7d23d483-1f5d-4a6a-b672-3105dd8be5bd.png)

4개의 박스가 있고 각 박스를 클릭하면 화면은 흐려지고 클릭한 박스는 선명하게 중앙으로 이동하는 애니메이션이다. Overlay는 검정색의 흐릿한 컴포넌트이고 클릭하면 나타나게 
하여 구현한 것이다. 

![image](https://user-images.githubusercontent.com/55936770/209980210-bce33191-ed91-4f71-b582-901c3613babb.png)

조금 더 실용적으로 만든 코드다. 참고하자.


















