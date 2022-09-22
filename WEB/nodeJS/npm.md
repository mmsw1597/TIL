## NPM
1. node package manager의 준말
2. Node.js 프로젝트를 관리하는 필수적 도구.
3. 온라인 상태라면 어디서든 연결 가능.
4. cmd나 터미널에서 사용가능

## npm 온라인 저장소
1. 수많은 오픈소스 라이브러리와 도구들이 업로드되는 장소
2. 필요한 라이브러리나 도구를 손쉽게 검색 가능.

## 커맨드라인 도구
1. 프로젝트 관리를 위한 다양한 명령어 제공
2. 저장소에서 라이브러리, 도구 설치, 프로젝트 설정, 의존성 관리 등을 가능하게 해줌.

## 프로젝트 생성
`$npm init` : 프로젝트 디렉터리 안에서 해당 명령어 사용시 package.json이라는 파일을 만들어주고 해당 디렉토리는 node.js 프로젝트가 된다.

## package.json
프로젝트 관련 정보들이 저장되는 파일. 파일을 직접 수정하거나 npm 명령어를 사용하여 프로젝트 정보 수정 가능.
![image](https://user-images.githubusercontent.com/55936770/191726776-a3dfba79-249e-42a4-9d0b-2381a5291833.png)

## 의존성 관리
1. 프로젝트 내에서 사용하는 라이브러리 관리 방법
2. 프로젝트는 라이브러리에 의존하기 때문에 이러한 라이브러리를 dependency라고 함.

## 라이브러리
1. 특정 기능을 수행하는 코드의 묶음
2. 복잡한 기능을 직접 수행 X. 다른 사람이 구현한 것을 사용하는 방법.
3. Node.js에서는 패키지라고도 부름

## npm install
1. 해당 명령어로 프로젝트 의존성을 관리 가능
2. 의존성 추가/내려받기/개발용 추가/전역 패키지 추가 등 여러 용도로 사용 가능
3. 추가된 패키지는 package.json의 dependencies 안에 추가됨. 그리고 node modules 디렉터리에 저장됨.

## dependencies와 devDependencies
1. npm은 개발용 의존성을 분리하여 관리 가능.
2. 개발용은 배포 전까지만 사용하는 의존성
3. --save-dev 옵션을 붙이면 개발용 의존성 추가 가능.
4. package.json의 devDependencies에 추가됨

## package-lock.json
1. 프로젝트 의존성 추가시 해당 파일이 생성됨.
2. 프로젝트에 의존성을 추가하면 자동으로 최신버전으로 추가가 됨.
3. 의존성 버전이 갑자기 변경되지 않도록 설치된 버전을 고정하는 역할

## 버전 표기법
`npm install [package-name]@[version]` 으로 지정 가능.

## 의존성 내려받기
1. 기본적으로 node_modules 디렉토리는 코드관리나 배포시에 업로드 X
2. 의존성이 많아지면 용량이 너무 커지고 운영체제별로 실행되는 코드가 다른 경우가 존재하기 때문
3. `npm install`을 통해 package.json에 정의된 dep, devDep를 node_modules 디렉토리에 내려받을 수 있음.
4. `npm install --production` 명령어로 개발용 의존성은 제외할 수 있음.

## 로컬 패키지
package.json에 선언되어 있고 node_modules에 저장된 패키지

## 전역 패키지
1. npm install -g 를 통해 내려받아 전역 패키지 저장소에 저장된 패키지
2. 전역 패키지도 프로젝트에서 사용가능하나 프로젝트 의존성은 package.json에 명시적으로 선언되는 것이 좋은 방향이다.

## 의존성 삭제
`npm remove [package-name]`을 통해 의존성 패키지 삭제 가능.

## 스크립트 실행
1. 스크립트란 간단한 동작을 수행하는 코드
2. package.json의 scripts에 선언된 스크립트를 npm run [script-name]으로 실행 가능.



