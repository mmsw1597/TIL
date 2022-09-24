## RDB
1. relational database
2. 자료의 관계를 주요하게 다룸.
3. SQL 질의어를 사용하기 위해 데이터 구조화가 필요함.

## NoSQL
1. 구조화된 질의어를 사용하지 않는 데이터베이스
2. 자료간의 관계에만 초점을 두지 않음.
3. 자료 개체 고유의 의미에도 관심을 둔다.
4. 데이터를 구조화하지 않고 유연하게 저장함.
5. 다양한 종류가 있지만 대표적으로 자료를 Document로 저장하는 Document DB가 일반적

## NoSQL 장점
1. 관계형의 경우 데이터를 구조화하는 것이 필수. 따라서 스키마에 정의된 데이터가 아니면 저장할 수 없는 제약이 있음
2. NoSQL의 경우 사전작업 없이 데이터베이스를 사용할 수 있음

## MongoDB 구조
Database는 여러 개의 Collection으로 구성되어 있고, 각 Collection은 여러 개의 Document로 구성된다.

## Database
1. 하나 이상의 Collection을 가질 수 있는 저장소.
2. SQL에서의 Database와 유사.

## Collection
1. 하나 이상의 Document가 저장되는 공간.
2. SQL에서의 table과 유사함.
3. collection이 document의 구조를 정의하지 않음

## Document
1. MongoDB에 저장되는 자료
2. SQL에서 row와 유사함. 단 구조제약없이 유연하게 저장 가능.
3. JSON과 유사한 BSON을 사용하여 다양한 자료형을 지원.

## Document - ObjectID
1. 각 document의 유일한 키 값, SQL에서의 primary key와 유사한 ObjectID가 존재함.
2. ObjectID는 하나씩 증가하는 값이 아닌 document를 생성할 때 자동으로 생성되는 값. (timestamp + random value  + auto increment)

## MongoDB 사용법
1. 직접 설치하는 방법이 있음. 이는 번거럽고 어렵지만 얼마든지 데이터를 사용할 수 있음.
2. Cloud 서비스를 사용하면 쉽고 빠르게 시작가능. 단, 사용량에 따라 요금이 부가됨.

## Mongoose ODM
1. Object Data Modeling
2. MongoDB의 Collection에 집중하여 관리하도록 도와주는 패키지
3. Collection을 모델화하여 관련 기능을 쉽게 사용하도록 도와줌.
4. MongoDB의 기본 Node.js 드라이버는 연결상태를 관리하기 어려움. Mongoose를 사용하면 간단하게 데이터베이스와의 연결상태를 관리해줌.

## Mongoose ODM 장점
1. 스키마 관리에 용의함
2. 기본적으로 NoSQL은 스키마를 정의하지 않지만 데이터 형식을 미리 정의해야 코드 작성과 관리에 유용함.
3. Monggose는 Code-level에서 스키마를 정의하고 관리할 수 있게 해줌.
