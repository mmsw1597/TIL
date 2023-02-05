# Babel
자바스크립트 컴파일러

간혹 node JS나 브라우저가 이해하지 못하는 최신 JS 문법을 사용할 수 있다. 이때 node JS, 브라우저가 이해할 수 있도록 코드를 변환해 주는 것이 바로 Babel이다.

# devDependencies
Babel은 개발자에게 필요한 패키지이다. 따라서 devDependencies로 분류된다. (프로젝트에게 필요한 패키지는 dependencies로 분류)

이때 Babel을 설치할때 `--save-dev`를 붙이는데 devDependencies로 뷴류되도록 하게 하는 명령어다.

`--save`는 npm install을 할때 dependencies 항목에 추가한다는 뜻인데, 최근 npm5 버전이후는 굳이 `--save`옵션을 붙이지 않아도
자동으로 dependencies 항목에 추가된다.

# nodemon
우리가 만든 파일이 수정되는지 감시하는 패키지

파일이 수정되면 nodemon이 알아서 재시작해준다.

코드를 수정할때마다 프로젝트를 수동으로 재시작할 필요가 없어짐
