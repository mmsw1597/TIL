## Relation
집합에 기반한 수학적인 개념. 즉, 중복을 허용하지 않고 순서에 의미가 없다.

## 비공식적 정의
1. relation은 table의 값으로 보인다.
2. relation은 행들의 집합을 포함한다. 공식적인 모델에서 row는 tuple이라고 불림.
3. 각 행은 실세계의 entity나 relationship에 대응됨.
4. 각 열은 해당 열이 나타내는 data의 의미를 포함하는 header가 있음
5. 공식적으로 각열의 헤더는 attribute name 이라고 불림.

## 비공식적 정의 (2)
1. 각 행은 테이블 내에서 그 행이 고유하도록 식별하는 column을 가짐.
2. 그 column을 key라고 한다.
3. 각 열을 식별하기 위해 단순한 일련번호를 key로 부여하기도 함. 이를 artificail key 혹은 surrogate key라고 부름.

## 공식적 정의 - Schema
1. Schema는 meta-data, description을 의미.
2. R(A1, A2, ... An) 으로 쓰여짐.
3. 이때 R은 relation의 이름.
4. 각 A는 attribute를 의미.
5. 각 attribute는 domain을 갖게됨. domain이란 유효한 값의 집합. ex) 소비자 id는 6자리 숫자여야 한다.

## 공식적 정의 - tuple
1. tuple은 순서있는 값의 집합.
2. 각 값은 적절한 domain으로 부터 생성됨.
3. 만약 4개의 종류의 값을 가지면 4-tuple이라고 함.
4. relation은 tuple의 집합이라고 볼 수 있음. (중복 X), 만약 중복을 가지면 table임. table과 relation은 다른 것으로 보아야 함.

## 공식적 정의 - domain
1. domain은 논리적 정의를 가짐. ex) USA 전화번호는 10개 숫자의 집합.
2. domain은 data-type 또는 정해진 형식을 가짐.
3. 같은 domain을 갖는 attribute는 여러개일 수 있음. 이때는 attribute name이 의미를 구분해주어야 함

## 공식적 정의 - State
1. relation state는 attribute의 domain의 Cartesian product의 부분집합이다.
2. Cartesian product는 가능한 모든 조합을 의미.

## Relation 특징.
1. 각 tuple은 순서가 있다고 고려되지 않는다.
2. relation schema나 tuple의 값의 경우는 순서가 중요함.
3. 일반적인 대안의 정의에서는 tuple이 meta-data와 value의 쌍으로 값을 나열하기도 함. 이때는 순서가 의미 없음.
4. Relation 내의 각 값은 atomic함. 예를들어 하나의 셀에 (1,2,3) 이런식으로 적으면 값이 3개로 되었다고 생각하지 않음 1,2,3 을 하나의 값으로 생각.
5. tuple의 각 값은 해당 attribute의 domain으로 부터 온 값이어야 함.
6. null 값은 알 수 없는 값이거나 사용 불가능한 경우에 사용.
7. t[A] / t.A는 tuple t에서 attribute A에 해당하는 값 v를 의미. 

## Constraints
1. 암묵적 제약 조건 : ex) 각 값은 list형태의 값을 갖는 것은 불가능. (atomic)
2. schema-based / 명시적 제약 조건 : ex) null 값 불가능/ unique 해야함.
3. application-based / semantic constraints : DB가 처리할 수 없는 범위의 제약은 application에서 미리 처리해주어야 함.

## relational constraints
1. 모든 유효한 relation states를 묶는 조건.
2. key constraints
3. entity integrity
4. referential integrity
5. domain constraint

## Key constraint (★)
1. superkey란 relation state의 tuple간에 같은 값을 가질 수 없게 하는 attribute의 집합
2. key란 minimal superkey라고 불림. 즉, superkey K가 있다고 할때, K에서 어떤 attribute를 제거했을 때, 더이상 superkey가 되지 않게 하는 attribute 집합
3. key는 superkey임 그러나 역은 성립하지 않음.
4. key를 포함하는 attribute의 집합은 반드시 superkey임
5. relation이 candidate key를 여러개 가지면 그중 임의로 하나를 대표해서 정하면 그것을 primary key라고 부르고 보통 밑줄을 쳐서 표현함.

