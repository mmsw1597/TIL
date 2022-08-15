``` css
button : active {
  background-color : tomato;
}
```
### active
어떤 요소를 누르고 있을 때 효과 적용

### hover
어떤 요소에 마우스를 대고 있을 때 효과 적용

### focus
키보드로 요소를 선택하고 있을 때 효과 적용

### visited
링크에만 적용되는 state인데, 방문한 적이 있는 사이트에 효과 적용.

### focus-within
focus된 자식을 가진 부모 엘리먼트에 효과 적용.

### state 연계
```css
form : hover input: focus{
  background-color: brown;
}
```
form이 hover 상태고 input이 focus 상태면, 배경색 갈색 적용.


