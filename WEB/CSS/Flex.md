### Flexbox
Inline-block의 문제점을 해결하기 위해 새로 나온 속성. 이름에서 알 수 있듯이 유연함을 자랑.

### flexbox 주의점
자식 엘리먼트에 어떤 것도 적지 말아야 함. 부모 엘리먼트에만 명시해야함. 즉, 자식에게 flex box를 적용하려면 부모에게만 display: flex를
적용하면 됨.

### main axis
flex box의 주축. 디폴트는 수평이다.

### cross axis
flex box의 교차축. 디폴트는 수직이다.

### justify-content
자식 엘리먼트를 어떻게 정렬할 것인지를 명시하는 속성. 주축에 적용됨.

### align-items
justify-content와 유사. 기본적으로 교차축에 적용됨.

### flex-direction
column, row 속성을 가질 수 있음. 기본은 row임. 주축의 방향을 의미함.

### flex-wrap
nowrap, wrap 속성을 가질 수 있음. 기본은 nowrap. 화면 사이즈를 줄였을때 부여했던 너비 값을 유지하느냐(wrap) 유지하지 않느냐(nowrap)의 차이. 기본적으로 flex-box는 요소를
라인 하나에 모두 넣기 때문.

### position : fixed
스크롤을 계속 내리거나 화면을 움직여도 특정 자리에 요소가 고정됨. 고정되는 위치는 맨 처음에 요소가 위치한 자리.
다른 요소와 겹치게 되는 경우, 그 요소와 레이어가 달라지게 됨. 위쪽 레이어로 이동함.

### position: relative
처음 위치한 곳을 기준으로 위치를 변경함. 

### position: absolute
가장 가까운 relative한 부모를 기준으로 위치를 변경함. 최종단은 body

### align-self
직접 자식에게 부여하는 속성 중 하나. align-items와 비슷하지만 특정 하나의 자식에게만 적용한다.

### order
직접 자식에게 부여되는 속성. default order는 0이다. order의 오름차순으로 요소가 정렬된다. HTML 문서의 변경없이 요소의 순서를 바꿀 수 있다. 

### align-content
교차축의 line 정렬 방법을 변경할 때 사용.

### flex-shrink
기본적으로 nowrap에서 작동하고 default 값은 1인데 만약 2를 부여한다면 화면이 줄어들 때 
요소의 너비값은 flex-shrink가 1인 요소에 비해 flex-shrink가 2인 요소가 2배로 너비가 줄어든다.

### flex-grow
flex-shrink의 반대개념. default 값은 0이고 1이 될 경우 차지할 수 있는 여분의 공간을 모두 차지하여 요소가 커진다.
부여되는 값에 따라 여분의 공간을 값에 비례하여 나눠가진다.

### flex-basis
child에 적용되는 속성. main-axis가 가로면 width, 세로면 height를 의미하게됨. flex-shrink나 flex-grow 에 의해 변형되기전 사이즈를 의미한다.  
