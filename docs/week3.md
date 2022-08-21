# Transaction

#### 인터뷰 질문

1. transaction 이란?
2. 트랜잭션 격리 수준에 대해서 설명해주세요

<hr/>

### Transaction 이란?

- 데이터 베이스의 상태를 변환시키는 `하나의 논리적 기능을 수행하기 위한 작업의 단위` 또는 `한꺼번에 모두 수행되어야 할 일련의 연산`들을 의미
- 트랜잭션은 작업의 완전성을 보장해주는 것이다 사용자의 입장에서는 작업의 논리적 단위로 이해를 할 수 있고 시스템의 입장에서는 데이터들을 접근 또는 변경하는 프로그램의 단위가 됨

### 특성

1. `원자성(Atomicity)`
   - 트랜잭션의 연산은 데이터베이스에 **모두 반영되든지 아니면 전혀 반영되지 않아야한다**
   - 트랜잭션 내의 모든 명령은 반드시 완벽히 수행되어야 하며, 모두가 완벽히 수행되지 않고 **어느 하나라도 오류가 발생하면 트랜잭션 전부가 취소**되어야 한다
2. `일관성(Consistency)`
   - 트랜잭션이 그 실행을 **성공적으로 완료하면 언제나 일관성 있는 데이터베이스 상태로 변환한다**
   - 시스템이 가지고 있는 고정요소는 트랜잭션 수행전과 트랜잭션 수행 완료 후의 상태가 같아야한다
3. `고립성(Isolation)`

   - **둘 이상의 트랜잭션이 동시에 병행 실행되는 경우 어느 하나의 트랜잭션 실행중에 다른 트랜잭션의 연산이 끼어들 수 없다**
   - **수행중인 트랜잭션은 완전히 완료될 때까지 다른 트랜잭션에서 수행 결과를 참조할 수 없다**

4. `지속성(Durability)`
   - **성공적으로 완료된 트랜잭션의 결과는 시스템이 고장나더라도 영구적으로 반영되어야 한다**
   <hr/>

### Transaction Isolation Level(트랜잭션 격리 수준)

serializable로 갈수록 고립성이 높아지며, 성능이 떨어진다

1. `READ UNCOMMITTED(커밋되지 않은 읽기)`

   - 어떤 트랜잭션의 변경내용이 **commit이나 rollback과 상관없이 다른 트랜잭션에 보여진다**

2. `READ COMMITTED(커밋된 읽기)`

   - 어떤 트랜잭션의 변경 내용이 **commit 되어야만 다른 트랜잭션에서 조회 가능하다**

3. `REPEATABLE READ(반복 가능한 읽기)`
   - **트랜잭션이 시작되기 전에 커밋된 내용에 대해서만 조회할 수 있는 격리 수준**
4. `SERIALIZABLE(직렬화 가능)`
   - **동시처리 능력이 다른 격리 수준보다 떨어지고 성능저하가 발생한다**

- **문제점**
  ![image](https://user-images.githubusercontent.com/55472510/185797515-b19a26f3-815a-4de2-92e9-2bcf3a012bb6.png)

1. `Dirty Read`

   - 변경 후, 아직 커밋되지 않은 값을 읽고 Rollback후의 값을 다시 읽어 최종 결과 값이 상이한 현상

2. `Non-Repeatable Read`

   - 한 트랜잭션 내에서 같은 쿼리를 두번 수행할 때, 그 사이에 다른 트랜잭션이 값을 수정 또는 삭제함으로써 두 쿼리가 상이하게 나타나는 비 일관성

3. `Phantom Read`

   - 하나의 트랜잭션에서 같은 쿼리를 두 번 실행했을 경우, 첫 번째 쿼리에서 없던 유령(Phantom) 레코드가 두 번째 쿼리에서 나타나는 현상이다.

   - **INSERT에 대해서만 발생하는 문제** (SELECT, DELETE에 대해서는 발생하지 않는다)
     👉 이를 방지하기 위해서는 쓰기 잠금 (write lock)을 걸어야 한다

각 경우별 예시 [참고](https://joont92.github.io/db/%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B2%A9%EB%A6%AC-%EC%88%98%EC%A4%80-isolation-level/)

<hr/>
### 트랜잭션 연산 및 상태

![image](https://user-images.githubusercontent.com/55472510/185797721-5969276e-a850-41b2-999b-6af27c451b25.png)

- Active
  **트랜잭션의 활동 상태** 즉, 트랜잭션이 실행중이며 동작중인 상태
- Failed
  **트랜잭션의 실패 상태** 더 이상 정상적으로 진행할 수 없는 상태
- Partially Committed
  **트랜잭션의 커밋 명령이 도착한 상태**
- Committed
  **트랜잭션의 완료 상태**
- Aborted  
  **트랜잭션의 취소 상태**트랜잭션이 취소되고 실행 이전 데이터로 돌아간 상태

- `Partially Committed` vs `Committed`
  Commit 요청이 들어오면 상태는 Partial Commited 상태가 된다. 이후 Commit을 문제없이 수행할 수 있으면 Committed 상태로 전이되고, 만약 오류가 발생하면 Failed 상태가 된다. 즉, Partial Commited는 Commit 요청이 들어왔을때를 말하며, Commited는 Commit을 정상적으로 완료한 상태를 말한다.

<hr/>
 
### 참조
Transaction : https://coding-factory.tistory.com/226
트랜잭션 격리수준: [1] https://zzang9ha.tistory.com/381
[2] https://joont92.github.io/db/%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B2%A9%EB%A6%AC-%EC%88%98%EC%A4%80-isolation-level/
[3] https://velog.io/@guswns3371/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B2%A9%EB%A6%AC%EC%88%98%EC%A4%80

트랜잭션의 연산 및 상태: https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Database
