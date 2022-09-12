## DBMS Interfaces
1. Stand-alone query language interfaces : SQL 쿼리문을 DBMS를 통해 직접 타이핑하는 인터페이스
2. Programmer interfaces : 다른 프로그래밍 언어에 포함된 (embedding DML) 형태를 지원하는 인터페이스
3. user-friendly interfaces : 유저에게 친화적인 인터페이스, 그래피컬한 것이 특징.

## DBMS Programming Languade Interfaces
1. Embedded Approach : 말 그대로 SQL문이 c언어 등에 포함된 형태로 접근
2. Procedure Call Approach : DBMS에 접근하는 함수 즉, API를 제공. JDBC나 ODBC. 이식성이 좋기때문에 가장 많이 사용됨.
3. DB Programming Language Approach : 특정 DBMS 고유의 언어를 제공. 특정 DBMS에 종속적.

## DBMS Utilities
1. Loading Data : DB에 있는 파일형태의 데이터를 로딩
2. Backing up
3. Reorganizing
4. Performance Monitoring
5. Other function. (sorting, compression, etc)

## Other Tools
애플리케이션 개발 환경, CASE(computer-aided software engineering 개발할때 도움을 주는 프로그램) 은 DB design component를 가짐. 

## Three Tier Client-Server DBMS Architecture
3계층으로 구성됨. Client - App/Web Server - DB server로 구성된다. 이중 중간계층은 app의 비즈니스 로직을 저장한다.

## Intermediate Layer
1. 비즈니스 로직 저장.
2. DB 서버의 데이터에 접근하거나 데이터를 업데이트
3. 클라이언트가 직접 DB 서버로 접근하는 것을 막기때문에 보안성이 증가한다.

## DBMS 분류
1. data model에 따른 분류 : 관계형 / 네트워크 / 계층형 -> 객체지향형/ 관계형 + 객체지향형
2. Single user / multi user
3. 중앙집중형 / 분산형 (빅데이터)

## DBMS 비용
1. 일부는 오픈소스 시스템이기 때문에 무료. 오픈소스도 라이센스에 따라 비용을 지불할 수 도 있다.
2. 대부분 개인이 사용하는 목적이라면 무료로 제공되는 것이 많다.
3. 상업적 용도라면 큰 비용이 발생. 이때 추가적인 모듈을 제공함.
