### Pseudo Selector
많은 태그 중 특정 태그를 고르는 기법. last-child, firsrt-child 등으로 선택가능. class나 id를 사용하는 것보다 더 좋은 방법.

### nth-child()
인수 자리 안에 몇번째 자식을 고를건지 정하면 특정 태그를 고를 수 있음. 또는 even, odd도 사용가능. 2n, 3n, 2n+1, 3n+1도 가능.

### direct children
어떤 요소의 바로 밑 자식 태그를 지정하려면 '>'를 사용하면 된다. ex) div > span

### direct sibling
어떤 요소의 바로 첫번째 형제 태그르 지정하려면 '+'를 사용하면 된다. 바로 다음에 와야 선택된다.

### '~' combinator
어떤 요소의 형제이기는 하나 바로 뒤에 오는 태그는 아닌 요소를 지정하려면 '~'를 사용하면 된다.

### 어트리뷰트로 선택하기
예를들어 input 태그에 required 어트리뷰트가 있다면 input:required로 그 태그를 선택할 수 있다.

### 어트리뷰트 값으로 선택하기
예를들어 input 태그에 type = "password"인 어트리뷰트가 있다면 input[type="password"]로 선택할 수 있다.

### 어트리뷰트 값 포함으로 선택하기
예를들어 input 태그에 placeholder ="...name" 같이 name을 포함하는 값이 있다면 input[placeholder~="name"]으로 태그들을 선택가능

### ::placeholder
placeholder의 스타일을 변경시킬려면 콜론을 두 개 붙여서 스타일을 적용하면 된다.

### ::selection
어떤 텍스트를 드래그 했을 때 스타일을 변경시키려면 ::selection을 사용하면 된다.

### ::first-letter
첫번째 글자를 강조하는 문법.








