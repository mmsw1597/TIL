## Data model이란?
1. 데이터베이스 구조
2. 구조들을 조정할 수 있는 연산.
3. 데이터베이스에 적용되는 특정 제약조건<br/>

이 3가지 개념을 통합하여 data model이라고 부른다.

## Data model operation
크게 데이터를 가져오거나 업데이트하는 연산으로 구분한다. operation은 기본 연산(insert, delete, update)가 있고, 이 기본연산을 토대로 사용자 정의 연산을 만들 수 있다.

## Data model categories
1. Conceptual Data Models 
2. Physical Data Models
3. Implementation Data Models

## Conceptual Data Models
high-level에 속하며 거의 대부분의 유저가 인지할 수 있는 데이터의 컨셉을 말한다. 

## Physical Data Models
low-level에 속하며 데이터를 어떠한 방식으로 저장하는지 기술한다.

## Implementation Data Models
개발자가 DBMS에 표현한 것. 예를 들어 RDB를 사용했는지, noSQL을 사용했는지.

## Database Schema
데이터베이스에 대한 설명. 데이터베이스 구조나 데이터 타입, 데이터 제약조건을 말함. 전체적인 틀을 의미. meta-data에 해당함.

## Database State
실제 저장된 데이터를 의미. instance라고도 불림. 데이터베이스의 스냅샷이라고 보면 됨.

## Schema vs State
schema는 한번 정해지면 바꾸는 빈도가 매우 낮다. 하지만 state는 거의 매순간 바뀔 수 도 있다.

## Three-Schema Architecture (★)
1. internal schema at the internal level
2. conceptual schema at the conceptual level
3. external schema at the external level <br />

이는 DBMS의 성질, 프로그램과 데이터의 분리, 원본 데이터에 대한 다양한 뷰 제공의 특징을 서포트하기위해 설계됨.

## Internal Schema
물리적 데이터 저장 구조에 해당. 복잡한 저장구조와 데이터를 분리. 따라서 high-level에서 데이터가 어떤식으로 저장되는지 신경쓸 필요 없음.
ex) 데이터를 파티션을 나눠서 따로 분류하여 저장

## Conceptual Schema
원본 데이터를 의미. 데이터베이스 구조나 제약조건에 해당함

## External Schema
같은 원본 데이터(Conceptual Schema)를 유저에 따라서 다양한 view를 제공할 수 있게 함. ex) 학생들의 성적에 대한 데이터베이스가 있을때 학생에겐 자신의 성적만, 교수에겐 모든
학생의 성적을 보이도록 가능하게 함.

## Three-Schema Architecture의 특징
1. 각 level에서 수정이 되어도 다른 level에 영향을 주지 않음
2. 하위 레벨에서 수정을 해도 상위 레벨에서는 mapping만 수정하면 된다.
3. 각 레벨 사이의 mapping이 필요함. program은 보통 external schema만 참조하고, DBMS는 내부적으로 conceptual, internal를 mapping을 통해 차례로 거침. 데이터 추출은 반대순서

## Data Independence
1. Logical
2. Physical

## Logical Data Independence
conceptual schema를 바꾸어도 external schema에 영향을 주지 않음을 의미하는 독립성.

## Physical Data Independence
internal schema를 바꾸어도 conceptual schema에 영향을 주지 않음을 의미하는 독립성.

## DDL
1. 데이터베이스의 틀을 만들때 사용하는 언어. 데이터 정의 언어를 의미. conceptual schema를 명시할때 사용.
2. 보통 많은 DBMS는 DDL 하나로 internal, external을 구현할 수 있음.
3. 몇몇 DBMS는 internal, external를 구현할 때 다른언어 (SDL, VDL)을 쓰기도 함.

## DML
데이터 삽입/ 삭제/ 조정을 할때 쓰이는 언어. high level 언어이며 non-procedural Language임. 처리 순서를 명시하지 않으며 set-oriented라고 불리는데 집합 단위로 처리한다는 
의미. 다른 프로그래밍 언어에 결합이 가능하다. 






