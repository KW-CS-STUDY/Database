# RDBMS vs NoSql

<hr/>

### RDBMS란?

`관계형 데이터 베이스를 생성하고 수정하고 관리할 수 있는 소프트웨어`

- Relational Database: 관계형 데이터 모델에 기초를 둔 데이터베이스
- 관계형 데이터 모델: 데이터를 구성하는데 필요한 방법 중 하나로 모든 데이터를 2차원 테이블 형태로 표현함

#### 특징

1. 모든 데이터를 2차원 테이블로 표현
2. Row(record,tuple)과 column(filed, item)으로 이루어진 기본 데이터 저장 단위
3. 만들거나 이용하기도 비교적 쉽고, 확장이 용이함
4. ER모델에서 엔티티를 기반으로 테이블이 만들어짐
5. DBMS가 효율적이고 정확하게 운용되기 위해서는 `ACID` 트랜잭션을 갖추고 있어야 함

#### 종류

1. ORACLE
2. PostgreSQL
3. MySQL
4. MS-SQL
5. SQLite

[참고] (https://wch18735.github.io/database/RDBMS/)

<hr/>

### NoSql이란?

`비관계형 데이터베이스를 지칭한다. 즉 관계형 데이터 모델을 지양하며 대량의 분산된 데이터를 저장하고 조회하는데 특화되었으며 스키머 없이 사용 가능하거나 느슨한 스키마를 제공하는 저장소`

#### 특징

1. 데이터간의 관계를 정의하지 않는다(Join연산이 불가함)
2. RDBMS에 비해 대용량의 데이터를 저장할 수 있음
3. 분산형 구조로 서버에 데이터를 분산 저장해서 특정 서버에 장애가 발생했을 때도 데이터 유실 혹은 서비스 중지가 발생하지 않는다
4. 고정되지 않는 테이블 스키마를 갖는다

#### 종류

1. Key-Value Database: 기본적으로 key-value 하나의 묶음으로 저장되는 구조로 단순한 구조이기에 속도가 빠르며 분산 저장 시 용이함
   ex) Redis, Oracle NoSQL Database
2. Wide-Column Database: 행마다 키와 해당 값을 저장할 때 마다 각각 다른 값의 다른 수의 스킬마를 가질 수 있음
   ex) Hbase, GoogleBigTable, Vertica
3. Document Database: 테이블의 스키마가 유동적으로 레코드 마다 각각 다른 스키마를 가질 수 있음 ex) MongoDB, CouchDB, Azure Cosmos DB

[참고](https://code-lab1.tistory.com/53)

<hr/>

### 출처

RDBMS: https://jwprogramming.tistory.com/52
RDBMS 종류: https://wch18735.github.io/database/RDBMS/
NoSQL: https://code-lab1.tistory.com/53
