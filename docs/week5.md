# Index with B-tree

### Index란?

![image](https://user-images.githubusercontent.com/55472510/188303514-4b2d9324-fd22-4799-9f8d-1df2c594709f.png)

- 추가적인 쓰기 작업과 저장 공간을 활용하여 데이터베이스 테이블의 검색 속도를 향상 시키기 위한 자료구조

(1) 장점 - `테이블을 조회하는 속도와 그에 따른 성능을 향상시킴` - 전반적인 시스템의 부하를 줄일 수 있다
(2) 단점 - 인덱스를 관리하기 위해 DB의 약 10%에 해당하는 저장공간이 필요함 - 인덱스를 관리하기 위한 추가직업이 필요함 - `인덱스를 잘못 사용하는 경우 오히려 성능이 저하되는 경우도 발생`

<hr/>

### Index가 무조건 옳은가?

DBMS 의 `인덱스는 항상 정렬된 상태를 유지하기 때문에 원하는 값을 탐색하는데는 빠르지만 새로운 값을 추가하거나 삭제, 수정하는 경우에는 쿼리문 실행 속도가 느려진다`. 결론적으로 DBMS 에서 인덱스는 데이터의 저장 성능을 희생하고 그 대신 데이터의 읽기 속도를 높이는 기능이다.
SELECT 쿼리 문장의 WHERE 조건절에 사용되는 칼럼이라고 전부 인덱스로 생성하면 데이터 저장 성능이 떨어지고 인덱스의 크기가 비대해져서 오히려 역효과만 불러올 수 있다.

- **_Index를 사용하면 좋은 경우_**
  (1) 규모가 작지 않은 테이블
  (2) insert, update, delete가 자주 발생하지 않는 컬럼
  (3) join이나 where또는 order by에 자주 사용되는 컬럼
  (4) 데이터의 중복도가 낮은 컬럼

<hr/>

### Index의 자료구조

`(1) B+-Tree 인덱스 알고리즘`

- 일반적으로 사용되는 인덱스 알고리즘의 경우 B+-Tree 알고리즘이다
- B+-Tree 인덱스는 `칼럼의 값을 이용해 인덱싱`하는 알고리즘이다

- B+ tree: 자식 노드가 2개 이상인 b-tree를 개선시킨 자료구조 [참고](https://velog.io/@emplam27/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EA%B7%B8%EB%A6%BC%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-B-Plus-Tree)

`(2) Hash 인덱스 알고리즘`

- `칼럼의 값으로 해시 값을 계산해서 인덱싱하는 알고리즘으로 매우 빠른 검색을 지원`
- 특정문자로 시작하는 값으로 검색을 하는 전방 일치와 같이 값의 일부만으로 검색하고자 할 때는 해시 인덱스를 사용할 수 없음

[해시테이블 참고](https://mangkyu.tistory.com/102)

**_ 왜 Index를 생성하는데 b-tree를 사용하는가? _**
Hash table은 데이터를 조회할 때 시간 복잡도가 O(1)이다
b-tree를 사용하는거에 반해 더 효율적이지 않을까?

답변은 `SELECT질의의 경우 조건에 부등호(<>)연산도 사용할 때가 있다.hash table을 사용하면 등호(=)연산은 가능하지만 부등호 연산이 불가능하다.`

<hr/>

### Primary Index VS Secondary Index

<hr/>

#### 출처

인덱스: https://mangkyu.tistory.com/96
hash와 b-tree: https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Database
b+tree: https://velog.io/@emplam27/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-%EA%B7%B8%EB%A6%BC%EC%9C%BC%EB%A1%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EB%8A%94-B-Plus-Tree
hash table : https://mangkyu.tistory.com/102
