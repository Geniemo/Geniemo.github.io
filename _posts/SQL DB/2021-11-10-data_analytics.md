---
title:  "[SQL DB] 데이터 분석 단계로 나아가기"
excerpt: "step 04"

categories:
  - SQL DB

toc: true
toc_sticky: true
toc_label: "데이터 분석 단계로 나아가기"

last_modified_at: 2021-11-10
---

## 1. 데이터의 특성 구하기

특정 컬럼의 값을 가진 로우 수를 구하고 싶다면 아래와 같이 작성하면 된다.<br>
이 때 해당 컬럼의 값이 NULL이면 그 로우는 카운트하지 않는다.
```sql
SELECT COUNT(col) FROM dbname.tablename;
```

컬럼의 값이 NULL인 로우는 카운트하지 않기 때문에,<br>
전체 로우의 수를 알고 싶을 때는 불편할 수도 있다.<br>
따라서, 그런 경우에는 아래와 같이 SQL문을 작성하면 된다.
```sql
SELECT COUNT(*) FROM dbname.tablename;
```

특정 컬럼에서 가장 큰 값 또는 가장 작은 값을 찾고 싶다면 아래와 같이 작성하면 된다.
```sql
SELECT MAX(col) FROM dbname.tablename;
SELECT MIN(col) FROM dbname.tablename;
```

특정 컬럼의 평균을 구하고 싶다면 아래와 같이 작성하면 된다.<br>
AVG 함수도 계산할 때 NULL을 포함하지 않으므로 NULL이 포함돼서 이상한 값이 나올 일은 없다.
```sql
SELECT AVG(col) FROM dbname.tablename;
```

특정 컬럼의 합을 구하고 싶다면 아래와 같이 작성하면 된다.
```sql
SELECT SUM(col) FROM dbname.tablename;
```

특정 컬럼의 표준편차를 구하고 싶다면 아래와 같이 작성하면 된다.
```sql
SELECT STD(col) FROM dbname.tablename;
```

이러한 집계함수들 외에도 각 로우마다 단순한 산술 연산을 해주는 산술 함수들도 있다.<br>
산술 함수에는 아래와 같은 함수들이 있다.
```sql
SELECT ABS(col) FROM dbname.tablename;      # 절댓값을 구하는 함수
SELECT SQRT(col) FROM dbname.tablename;     # 제곱근을 구하는 함수
SELECT CEIL(col) FROM dbname.tablename;     # 올림 함수
SELECT FLOOR(col) FROM dbname.tablename;    # 내림 함수
SELECT ROUND(col) FROM dbname.tablename;    # 반올림 함수
```
이 외에도 다양한 산술 함수들이 있는데, 다른 것들이 궁금하다면 [여기](https://dev.mysql.com/doc/refman/8.0/en/mathematical-functions.html)를 참고하자.

## 2. NULL을 다루는 방법

특정 컬럼에 NULL이 들어있는 row들을 조회하려고 한다면 아래와 같이 작성하면 된다.
```sql
SELECT * FROM dbname.tablename WHERE col IS NULL;
```
`IS NULL`은 말 그대로 NULL값이 들어있는지를 나타내는 조건식이다.<br>
만약 반대로 값이 들어있는 row들만 조회하려고 한다면 `IS NOT NULL`을 사용하면 된다.<br>
이 때 IS NULL을 = 로 대체하거나, IS NOT NULL을 !=나 <>로 대체하는 실수를 하기도 하는데,<br>
NULL은 어떤 값이 아니기 때문에 어떤 값과 비교할 수 있는 대상이 아니므로 반드시 IS NULL 또는 IS NOT NULL을 사용해야 한다.

프로그래밍을 하는 사람이라면 NULL이 무슨 뜻인지 다 알고 있을텐데,<br>
다른 직군 사람들과 함께 살펴봐야 할 경우에는 NULL을 좀 더 일반적인 단어로 바꿔주는 것이 좋다.<br>
그러한 방법에는 여러가지가 있는데, 그 중 한가지인 `COALESCE`를 사용해보자.
```sql
SELECT COALESCE(col, defaultvalue) FROM dbname.tablename;
```
위와 같이 sql문을 짠다면 특정 컬럼에 값이 있는 경우에는 그 값을 그대로 보여주고,<br>
NULL 값이 있는 경우에는 defaultvalue를 보여준다.

그리고, NULL에는 어떤 연산을 해도 결국 NULL이다.

## 3. 이상한 값을 제외하고 싶을 때

어떤 컬럼에 정상적인 값, NULL값 외에도 비정상적인 값이 들어있을 수도 있다.<br>
예를 들어, 어떤 사람의 나이를 저장하는 컬럼인데 음수나 500같은 큰 숫자가 들어있다면 이건 비정상적인 값이라고 할 수 있다.
그러므로, 데이터의 특성 값을 구할 때 특정 컬럼의 특성을 고려해서 비정상적인 값들을 제외하고 구해야 한다.

만약 나이가 10세 이상 100세 이하인 사람들의 나이 평균을 구하고 싶다면 아래와 같이 sql문을 작성하면 된다.
```sql
SELECT AVG(age) FROM dbname.tablename WHERE age BETWEEN 10 AND 100;
```
age 컬럼이 아니라 다른 의미를 갖는 컬럼들에는 어떻게 적용해야 하지? 하고 궁금해질 수도 있는데<br>
일반적으로 어떤 컬럼이 갖는 특성을 잘 고려해서 알맞은 조건을 만들어서 비정상적인 값을 제외하면 된다.

