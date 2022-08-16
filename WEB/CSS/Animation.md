### Transition
어떤 상태(state)에서 다른 상태로 가는 변화를 애니메이션화 하는 것.

### 사용방법
```css
a {
transition: "변화시키고 싶은 속성" "변화할때까지 걸리는 시간" "변하는 방법", ...
}
a:hover{
  color: tomato;
  background-color: wheat;
}
```
첫번째 자리에 all을 넣으면 state 변화시 변하는 속성 모두를 포함한다. 변화시키고자 하는 속성이 state 문에 없으면 안된다. 본래 상태로 돌아갈 때에도 애니메이션을 통해 돌아간다.
구분은 콤마로 한다.

### cubic-bezier
변하는 방법을 직접 커스텀할 수 있음. 대부분은 ease-in, ease-out, ease-in-out을 사용.

### transform
어떤 요소의 형태를 변화시키는 방법.

### 종류
1. rotateY(deg) : Y 축 기준 회전.
2. rotateX(deg) : X 축 기준 회전.
3. rotateZ(deg) : Z 축 기준 회전. (시계 방향 회전)
4. scaleX/Y/Z(m) : 축을 기준으로 m배 만큼 확대.
5. translateX/Y/Z(npx) : 축을 기준으로 npx 만큼 이동.
6. 나머지는 외우기보단 직접 mdn에서 검색해서 찾아 쓰자.

### 주의점
특정 요소를 transform 시킬때 형제 요소는 전혀 영향을 받지 않는다. 즉, 다른 요소의 box를 변형시키지 않고 요소를 이동시킨다.

### 애니메이션
```css
@keyframes "애니메이션 이름"{
  from{
  }  
  to{
  }
}

@keyframes "애니메이션 이름"{
  0%{
  }
  50%{
  }
  100%{
  }
}

element{
animation: "애니메이션 이름" "변하는 시간" "변하는 방법";
}
```
어떠한 상태 변화가 일어나지 않아도 페이지가 로드되면 자동 재생되는 애니메이션.

### Media query
css를 이용하여 스크린의 사이즈를 알 수 있는 방법 즉, 사용자가 모바일에서 사이트를 보거나, 가로모드로 보거나, 아주 큰 화면에서 보는 것을 알아채는 방법
```css
@media screen and (max-width: 400px) and (orientation : landscape){
  //속성 변경
}
```
이 스크린이 400px보다 작고 가로모드면 중괄호 내의 효과 적용. 세로모드는 portrait.
