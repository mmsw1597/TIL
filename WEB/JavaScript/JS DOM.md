### DOM
HTML 문서의 계층적 구조와 정보를 표현하며 이를 제어할 수 있는 API를 제공하는 트리 자료구조다.

### 문서 노드
DOM트리의 최상위에 존재하는 루트 노드. document 객체를 가르킨다.

### 요소 노드
HTML 요소를 가르키는 객체.

### 어트리뷰트 노드
HTML 요소의 어트리뷰트를 가르키는 객체. 요소 노드에만 연결되어 있다.

### 텍스트 노드
HTML 요소의 텍스트를 가르키는 객체. DOM 트리의 최종단이다.

### Document.prototype.getElementById
인수로 전달한 id 어트리뷰트 값을 갖는 하나의 요소 노드를 탐색하여 반환한다.

### Document.prototype.getElementsByTagName
인수로 전달한 태그 이름을 갖는 모든 요소 노드들을 탐색하여 반환한다. 이때 여러 개의 요소 노드 객체를 갖는 DOM 컬렉션 객체인 HTMLCollection 객체를 반환한다.

### Document.prototype.getElementsByClassName
인수로 전달한 클래스 이름을 갖는 모든 요소 노드들을 탐색하여 반환한다. 마찬가지로 HTMLCollection 객체를 반환한다.

### Document.prototype.querySelector
인수로 전달한 CSS 선택자를 만족시키는 하나의 요소 노드를 탐색하여 반환한다.

### Element.prototype.matches
인수로 전달한 CSS 선택자를 통해 특정 요소 노드를 취득할 수 있는 지 확인한다.

### HTMLCollection
live 객체로 동작한다. 노드 객체의 상태 변화를 실시간으로 반영한다. 이 때문에 오류가 발생할 수 있으므로 스프레드 문법을 통해 배열로 변경시킨 후 사용하는 것이 좋다.

### NodeList
querySelectorAll 메서드의 반환 형태. 실시간으로 노드 객체의 상태 변경을 반영하지 않는다. 하지만 childNodes 프로퍼티가 반환하는 NodeList 객체는 live 객체이므로 이도 배열로
변환한 뒤 사용하는 것이 좋다.



