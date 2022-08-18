### querySelector
1. element를 css방식으로 검색하는 메서드. 단 하나의 element만 반환한다. 중복되는 element가 여러개라면 가장 첫번째로 검색된 것을 반환한다.
2. ID를 통해서 찾고 싶다면 "#id" 를 인수로 넘기면 된다.
3. 클래스를 통해서 찾고 싶다면 ".class" 를 인수로 넘기면 된다.

### event
이벤트 종류는 굉장히 다양하며 원하는 이벤트를 찾으려면 검색을 하거나 console.dir 을 통해 찾는 것이 좋다.

### window.event
window는 js의 전역 객체로서 브라우저 자체를 생각하면 된다. resize, copy, wifi 연결 유무 등등의 이벤트를 다룰 수 있다.

### JS와 CSS
JS에 CSS를 병합하는 방법은 클래스로 css를 적용시키는 것이 좋고, 거기서 className 자체를 변경시키기 보다 classList를 이용하여 add, remove를 사용해서 CSS를 추가하는 것이 좋다.

### toggle
classList의 메서드로서 add, remove를 사용하는 것보다 더 간결하게 코드를 작성하게 해준다. 인수에 class 이름을 넣으면 그 class를 포함할땐 제거하고 없을땐 포함시킨다.

