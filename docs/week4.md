# Normalization

### 정규화가 생겨난 배경

한 릴레이션이 여러 엔티티의 애트리뷰트들을 혼합하게 됨녀 정보가 중복 저장되며, 공간을 낭비하게 된다.
그리고 중복된 정보로 인해 갱신이상이 발생하게 된다 -> **_동일한 정보를 가진 릴레이션은 변경하고, 나머지는 바꾸지 않은 경우 무엇이 정확한지 알 수 없어지는 것이다_**

<hr/>

### 정규화(Normalization)란?

- 관계형 데이터베이스에서 중복을 최소화하기 위해 데이터를 구조화하는 작업
- 불만족스러운 나쁜 릴레이션의 애트리뷰트들을 나누어서 좋은 작은 릴레이션으로 분해하는 작업
- `테이블간의 중복된 데이터를 허용하지 않음으로써 무결성을 유지할 수 있음`

<hr/>

### 정규화 종류 및 과정

![image](https://user-images.githubusercontent.com/55472510/188302524-991023bd-13d6-4b71-bddf-aa62b70ae2af.png)

(1)` 제 1정규화`

`테이블의 컬럼이 원자값을 갖도록 테이블을 분해하는 것`

<img width="360" alt="image" src="https://user-images.githubusercontent.com/55472510/188157179-939ee750-4445-463c-9226-e487bccdc570.png">

위와 같은 예시 중 이름이 추신수인 row를 확인해보면 영화와 음악으로 두가지 값을 갖고 있기 때문에 위배된다

(2) `제 2정규화`

`제 1정규화를 진행하고 테이블에 대해 완전 함수 종속을 만족하도록 테이블을 분해`해야한다

<img width="957" alt="image" src="https://user-images.githubusercontent.com/55472510/188157905-b7b03194-910a-4eb8-a6a5-203f64eb42ef.png">

위의 테이블의 경우 기본키가(학생번호,강좌이름)을 사용한 복합키이다
그리고 기본키로서 성적을 결정하고 있다
하지만 강의실 컬럼의 경우 강좌이름에 의해서 결정될 수 있기 때문에 테이블을 둘로 분리한다

(3) `제 3정규화`

제 2 정규화를 진행한 테이블에 대해 이행적 종속을 없애도록 테이블을 분리하는 것

- **_이행적 종속: A->B , B->C가 성립할때 A->C가 성립하는 것을 의미_**

![image](https://user-images.githubusercontent.com/55472510/188303080-55277b45-4ee1-4bbd-ba08-0c9645c56c71.png)

위의 테이블의 경우에는 학생번호가 강좌이름을 결정하고, 강좌 이름은 수강료를 결정한다

따라서 테이블을 아래와 같이 둘로 분리 할 수 있다

![image](https://user-images.githubusercontent.com/55472510/188303054-a325262e-e1e7-4c4a-a389-0fabdc6bb180.png)

해당 사진을 보면 학생번호와 강좌이름 그리고 강좌이름과 수강료로 나누어진 것을 확인할 수 있다

(4) `BCNF 정규화`
제 3 정규화를 진행한 테이블에 대해 모든 결정자가 후보키가 되도록 테이블을 분해하는 것

[예시 참고](https://mangkyu.tistory.com/110)

<hr/>

### 출처

정규화란: https://github.com/JaeYeopHan/Interview_Question_for_Beginner/tree/master/Database

정규화 종류: https://mangkyu.tistory.com/110
정규화 과정: https://velog.io/@bsjp400/Database-DB-%EC%A0%95%EA%B7%9C%ED%99%94-%EB%B9%84%EC%A0%95%EA%B7%9C%ED%99%94%EB%9E%80
