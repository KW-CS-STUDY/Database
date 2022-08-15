# SQL & JOIN

_SQL문의 경우 MySQL기준으로 설명함_

#### 인터뷰 질문

1. Join에 대해서 설명해주세요
2. SELECT SQL문 실행순서에 대해서 설명해주세요
<hr/>

### SQL

1. `INSERT`

데이터를 삽입하는 쿼리문

```SQL
INSERT INTO 테이블명 (컬럼1,컬럼2,컬럼3) VALUES (값1,값2,값3);
```

테이블의 각 명시한 컬럼에 값이 저장됨 -> 컬럼명과 값의 개수는 동일해야 함  
단, 컬럼명은 생략이 가능함

2. `SELECT`

데이터를 불러오는 쿼리문

```SQL
SELECT 컬럼명 FROM 테이블명 WHERE 조건 ORDER BY 컬럼명 ASC or DESC LIMIT 개수;
```

테이블에서 컬럼을 불러오고 WHERE뒤에오는 조건에 맞는 조건으로 조회함
단, ORDER BY뒤에 오는 컬럼을 기준으로 오름차순인지, 내림차순인지 설정가능

LIMIT뒤의 수의 설정으로 불러오는 row의 수를 정할 수 있음

3. `UPDATE`

데이터를 수정하는 쿼리문

```SQL
UPDATE 테이블명 SET 컬럼1=변경값1, 컬럼2=변경값2 WHERE 조건;
```

WHERE조건에 해당하는 컬럼을 각 설정한 값으로 변경해줌
변경할 값이 여러개 일때는 ,로 구분하여 작성

4. `DELETE`

테이블에서 데이터를 삭제하는 쿼리문

```SQL
DELETE FROM 테이블명 WHERE 조건;
```

조건에 맞는 row를 삭제함

#### SELECT문 실행순서

1. FROM : 각 테이블 확인
2. ON : 조인 조건 확인
3. JOIN : 테이블 조인
4. WHERE : 데이터 추출 조건 확인
5. GROUP BY : 특정 칼럼으로 데이터 그룹화
6. HAVING : 그룹화 이후 데이터 추출 조건 확인
7. SELECT : 데이터 추출
8. DISTINCT : 중복 제거
9. ORDER BY : 데이터 정렬

![image](https://user-images.githubusercontent.com/55472510/184575419-b5a97bb6-d8cd-4ae4-8550-1a6c67430e7f.png)

<hr/>

### JOIN

JOIN의 종류는 크게 `INNER JOIN, OUTER JOIN` 으로 구분이 가능하다

- `INNER JOIN`

inner join은 교집합 연산과 같다
조인 키 컬럼 값이 양쪽 테이블 데이터 집합에서 공통적으로 존재하는 데이터만 조인해서 결과를 냄

```SQL
SELECT 컬럼명
FROM 테이블A,
    테이블B
WHERE 테이블A.조인키 = 테이블B.조인키;
```

![image](https://user-images.githubusercontent.com/55472510/184576363-9631f02c-0ace-4bde-bd70-06fc4039ac0e.png)

- `OUTER JOIN`

  1. **LEFT OUTER JOIN**
     교집합 연산 결과와 차집합 연산결과를 합친것과 같다 -> ( (A ∩ B) ∪ (A - B) )

  ```SQL
  SELECT 컬럼명
      FROM 테이블A
      LEFT OUTER JOIN
      테이블B
      WHERE 테이블A.조인키 = 테이블B.조인키;
  ```

  ![image](https://user-images.githubusercontent.com/55472510/184576395-c710e834-75e2-46a0-814f-2c06c824391e.png)

  2. **RIGHT OUTER JOIN**

     교집합 연산 결과와 차집합 연산결과를 합친것과 같다 -> ( (A ∩ B) ∪ (A - B) )

  ```SQL
  SELECT 컬럼명
      FROM 테이블A
      RIGHT OUTER JOIN
      테이블B
      WHERE 테이블A.조인키 = 테이블B.조인키;
  ```

  ![image](https://user-images.githubusercontent.com/55472510/184576428-bedffd90-8e3b-48fb-8055-a5c247235a9e.png)

  3. **FULL OUTER JOIN**
     합집합 연산결과와 동일하다

  ```SQL
   SELECT 컬럼명
    FROM 테이블A
    FULL OUTER JOIN
    테이블B
    WHERE 테이블A.조인키 = 테이블B.조인키;
  ```

  ![image](https://user-images.githubusercontent.com/55472510/184576445-ca843f98-01ac-4ab9-8c75-bcebd742fbf7.png)

<hr/>

### 출처

기본 SQL 정리: https://lcs1245.tistory.com/entry/%EA%B8%B0%EB%B3%B8-SQL-Query%EB%AC%B8-%EC%A0%95%EB%A6%AC-SELECT-INSERT-UPDATE-DELETE

SELECT 동작 순서: https://nohriter.tistory.com/129

JOIN :
https://developer-jjun.tistory.com/24
https://sparkdia.tistory.com/17
